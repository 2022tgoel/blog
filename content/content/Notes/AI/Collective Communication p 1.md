
* Collectives we care about: All-Gather, Reduce-Scatter, All-to-All
* Send/Recv with PP is the simplest, all of the other types of parallelism give you much more to think about algorithmically
* All-Reduce can be and usually is implemented as a All-Gather and then Reduce-Scatter
* you can imagine you live in a complete graph, in which case you just send everything along all of your edges are you are done!
	* You can't actually achieve this, it's too many wires
	* you also might not be capable of receiving everything at once
	* time taken = $N D / B$ where $N$ is the number of bytes, $D$ is the number of devices, and $B$ is the bandwidth
	* latency = $O(1)$, since you can start sending data to each GPU immediately
* What people actually do: ring
	* Send the shard you just received to the next GPU in the ring 
	*  This is $O(D)$ latency -- oh no! 
	* However, you are only every sending data to one other GPU, which you can optimize that to be a really closeby GPU -- don't need that many wires, actually practical
* However, we still need to fix this latency issue. Latency dominates when you have a large number of GPUs. (A good way to think about latency is imagine you are sending one byte)
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