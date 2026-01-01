
* Collectives we care about: All-Gather, Reduce-Scatter, All-to-All
* Send/Recv with PP is the simplest, all of the other types of parallelism give you much more to think about algorithmically
* All-Reduce can be and usually is implemented as a Reduce-Scatter and then an All-Gather
* Latency and bandwidth
	* A link has a length ($L$) and bandwidth ($B$)
	* The time for $M$ bytes to traverse the link is ($L + \frac{M}{B}$)
* you can imagine you live in a complete graph, in which case you just send everything along all of your edges are you are done!
	* You can't actually achieve this, it's too many wires ($O(N^2)$ wires)
		* another way of thinking about this is that in realistic network topologies, sending to father away nodes is higher latency.
		* Common topologies
			* Bus, ring
				* multi-dimensional mesh
				* mesh + wraparound (TPUs) 
					* the wraparound links don't scale
			* tree
				* Clos switched (GPUs)
					* In a two-tier clos topology, the lower level is the leaf, and the layer above is the spine. 
			* The exact topology has extremely important implications. For example, i'm pretty sure the complete graph algorithm works fine instead of a ring on a 8-GPU nvidia node, but it wouldn't work well on a TPU torus
	* you also might not be capable of receiving everything at once, due to limited buffer space 
		* Theoretically, you can start sending/processing the data as soon as you receive it, but this is not practical, you need to do some buffering. 
	* You also have to set up $N^2$ connections, which each have an overhead. Switch is managing each connection.
	* time taken = $N / B$ where $N$ is the number of bytes per device, $D$ is the number of devices, and $B$ is the (per-link) bandwidth
	* latency = $O(1)$, since you can start sending data to each GPU immediately
* What people actually do: ring
	* Send the shard you just received to the next GPU in the ring 
	*  This is $O(D)$ latency -- oh no! 
	* However, you are only every sending data to one other GPU, which you can optimize that to be a really closeby GPU -- don't need that many wires, actually practical
* However, we still need to fix this latency issue. Latency dominates when you have a large number of GPUs. (A good way to think about latency is imagine you are sending one byte. Or imagine the longest wire distance any byte travels.)
	* Well this is because bandwidth pressure scales with the message size, and latency scales with the number of devices. Suppose you are all-gathering $M$ bytes distributed on $N$ gpus (like scaling FSDP with a fixed model size. maybe this is a bad setup because presumably you are scaling the model). Then each gpu has $\frac{M}{N}$ bytes. There is per-link bandwidth $B$. The total time is $N(\frac{M}{NB} + O(1))$. The bandwidth cost is fixed $\frac{M}{B}$. However, the latency cost keeps growing as $O(N)$.
* One idea is tree, and while this is logarithmic latency, its not good for bandwidth
	* One issue is that farther up the root you have to wait a bit before you start to send/recv data
	* Another issue is that the leaves send/recv less data than internal nodes
	* If we do a [double binary tree](https://developer.nvidia.com/blog/massively-scale-deep-learning-training-nccl-2-4/), we can fix the second issue
* This is where Bruck's algorithm comes in! After a step of ring, you have two nodes data. But you only send one. Instead, send both, to a node that has neither. This is the core idea. 
	* However, in order to do this, you need to send to a farther and farther away node each time. 
	* some kind of fundamental tradeoff between latency and the distance between communicating nodes
	* send to nodes 2, 4, 8, 16, etc. 
	* why not try a higher base than 2? seems like you get fewer tree levels (lower latency) and you talk to nearer nodes
* PAT extends this to when the intermediate buffer is of limited capacity. 