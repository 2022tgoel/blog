
![[Screenshot 2026-01-02 at 10.34.30 AM.png]]
Last one missing from this figure is all-to-all, used in EP.
https://www.cs.utexas.edu/~pingali/CSE392/2011sp/lectures/Conc_Comp.pdf
## Datacenters
![[Pasted image 20260102112342.png]]
https://textbook.cs168.io/datacenter/topology.html
**Oversubscription** is a measure of how far from the full bisection bandwidth we are, or equivalently, how overloaded the bottleneck part of the network is. It’s a ratio of the bisection bandwidth to the full bisection bandwidth (the bandwidth if all hosts sent at full rate).
![[Pasted image 20260102112806.png]]

If we using a tree to design our topology, you either need a high radix switch of a high bandwidth switch at the top. Could we design a topology that gives high bisection bandwidth, using cheap commodity elements? In particular, we’d like to use a large number of cheap off-the-shelf switches, where all the switches have the same number of ports, each switch has a low number of ports, and all link speeds are the same.

## Butterfly Networks
![[Pasted image 20260102101819.png]]



For $p$ nodes, you have $p (\log_2{p} + 1)$ switches. 

Switching node $N(i, j)$ gets connected to:
* $N(i-1, j)$
* $N(i-1, m)$, where $m$ is derived by inverting the $i$th bit of $j$. 

You have a latency $2$ connection to $i + \frac{n}{2} \pmod{n}$, a latency 4 connection to $i + \frac{n}{4} \pmod{n}$, $i + \frac{n}{2} + \frac{n}{4} \pmod{n}$ ... etc. 
BBN Butterfly](https://en.wikipedia.org/wiki/BBN_Butterfly "BBN Butterfly"), a massive [parallel computer](https://en.wikipedia.org/wiki/Parallel_computer "Parallel computer") built by [Bolt, Beranek and Newman](https://en.wikipedia.org/wiki/Bolt,_Beranek_and_Newman "Bolt, Beranek and Newman") in the 1980s, used a butterfly interconnect network. Later in 1990, [Cray Research](https://en.wikipedia.org/wiki/Cray "Cray")'s machine [Cray C90](https://en.wikipedia.org/wiki/Cray_C90 "Cray C90"), used a butterfly network to communicate between its 16 processors and 1024 memory banks

The big advantage is high bisection bandwidth while still having constant router complexity. Nowadays, higher router complexity isn't such a big deal. 

You can also flatten a column of the diagram above into a single higher-radix switch, yielding the flattened butterfly. 

https://stygianet.cs.purdue.edu/courses/2025fallaidc/AI-DC-Networking-Collectives.pdf
## Clos Network 

In a classic Clos network, we’d have all the racks on the left send data to the racks on the right. In datacenters, racks can both send and receive data, so instead of having a separate layer of senders and recipients, we can have a single layer with all the racks (acting as either sender or recipient). Then, data travels along one of the many paths deeper into the network, and then back out to reach the recipient. This result is called a **folded Clos network**, because we’ve “folded” the sender and recipient layers into one.

Folded Clos Network Diagram:
![[Pasted image 20260102123334.png]]

This is actually a **Two-Tier Clos Architecture (Leaf-Spine)**

![[Screenshot 2026-01-02 at 12.31.00 PM.png]]

Realistically, in almost all real Clos (leaf–spine) architectures, a “leaf” switch corresponds to a single rack, not $\sqrt{n}$ servers.

| Topology     | Diameter        | Bisection Bandwidth | Links                          | Degree       |
| ------------ | --------------- | ------------------- | ------------------------------ | ------------ |
| Linear array | ⁠$p-1$⁠         | 1                   | ⁠$p-1$⁠                        | 2            |
| Ring         | ⁠$\frac{p}{2}$⁠ | 2                   | $p$                            | 2            |
| _2-D mesh_   | $2(\sqrt{p}-1)$ | $\sqrt{p}$          | $2\sqrt{p}(\sqrt{p}-1)$        | 4            |
| Hypercube    |                 | $\frac{p}{2}$       | $\log_2{p} \times \frac{p}{2}$ | $\log_2{p}$  |
| Butterfly    | $2 \log_2{p}$   | $p$                 | $2p \log_2{p}$                 | 4            |
| Clos         | $O(1)$          | $\frac{p}{2}$       | $2p$                           | $2 \sqrt{p}$ |

![[Screenshot 2026-01-02 at 2.39.03 PM.png]]
You can kind of do whatever you want for a 3-tiered Clos network (basically strings together a bunch of 2-tiered Clos networks with a top level), but if you are smart about it you don't have to change the bandwidth per link or # of links per switch for the switches at the top level compared to the other levels, while still preserving symmetry (full bisection). Like what the diagram above achieves. 

* $k$ -> # of switches per pod at a single layer ($\sqrt{m}$ where $m$ is the number of devices in a pod)
* $m$ is the number of pods. 

* There are $km$ switches on the second layer

* Perserving bandwidth per link: There should be $k^2 m$ links between the 2nd layer and top layer. 
	* So if you are connecting everything to everything else, you could do $k$ switches at the top level. 
	* You actually don't need to do this because of some symmetry properties. You can complete graph $k$ groups of $m$ switches (or $\frac{k}{2}$ groups of $2m$ switches, etc.), which would give you $k^2$ switches at the top level (or $\frac{k^2}{2}$, $\frac{k^2}{4}$, etc.) 
* Perserving links per switch: there should be $2k$ links per switch
	* If you are connected everything to everything else, you have $km$ links per switch, which tells you that $k=2$. This is the diagram below: 
	* With group size $m$, you have $m=2k$. 
* 
![[Screenshot 2026-01-02 at 2.46.30 PM.png]]


* https://docs.nvidia.com/networking-ethernet-software/knowledge-base/Setup-and-Getting-Started/layer-1-Data-Center-Cheat-Sheet/
* https://arxiv.org/pdf/2307.12169
* https://network.nvidia.com/pdf/whitepapers/IB_vs_Ethernet_Clustering_WP_100.pdf