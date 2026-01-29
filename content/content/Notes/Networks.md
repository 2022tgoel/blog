
# Routing

Distance-vector works on large scales, link-state works on small scales. 

#### Distance-Vector
* Getting shortest path: Distributed Bellman-Ford
* Problem: routes can update: accept updates from next hop
* Problem: packets can be dropped: resend at regular intervals
* Problem: next hop can break: create a TTL
* Problem: TTL is not very fast at detecting failures: poison
	* If a table entry expires, make the entry poison and advertise it.
	* Poisoning is basically like nodes sending distance at regular intervals + accepting updates from the next hop
* Problem: you can get stuck in loops: 
	* Split Horizon: don't advertise back to your next hop
	* This is the same as **poison reverse**: advertising infinity back to you next hop 
* Problem: count to infinity loops
	* Set some low hop number as infinity
* Problem: hierarchical addressing can mean you match multiple entries (you are now advertising distances to groups of nodes, not individual nodes)
	* longest prefix matching. You can use tries as the data structure to implement this efficiently. 

Path-vector is like distance-vector but with advertising the full path instead of just its length. This prevents loops if people use arbitrary / different route selection policies (everyone has a slightly different bellman ford implementation according to their unique notion of "cost"). It is used in BGP. 

##### Link-State
building a full network graph

First learn all of the edges, then advertise them. When you advertise edges, track which edge advertisements you've seen so they don't go around indefinitely 

One thing I didn't know is *how expensive routers can be*. A router with 288 physical ports each at 400 Gbps bandwidth can be 1 million dollars. 

Forwarding chips and controller card separate the fast path and slow path. 

# Datacenters

###  Equal Cost Multi-Path (ECMP) Routing

In Clos networks, because you have so many paths, you need to modify the algorithms to make sure they use them all. The switch contains algorithms for distributing connection (source IP/port, dest IP/port) across paths. In Infiniband, the connections are QPs. So each QP takes a single route.

Distance vector protocols are modified to store paths with the same distance instead of drop them. 

Infiniband uses link-state style routing though. 

###### Why flow control Virtual Lanes instead of QPs? 
To be able to support millions of QPs

# Reliable Connections
* They have an ACK/NACK mechanism for the packets
	* In TCP: 
		* loss is the congestion signal
		* Ack means the receiver got it. 
		* nack means that they got it but with a bad checksum (this is optional)
	* In infiniband
		* loss is rare, because of credit-based flow control to manage the congestion. If you send a packet, only data corruption should make it so that it doesn't make it. You don't have to worry about queue overflow. 
		* Packet sequence numbers (PSNs)
		* You maintain a send PSN and a receive expected PSN
			* PSN == expected, accept
			* PSN > expeced, nack
			* PSN < expected, drop
			* This does mean that you have to wait to get a later packet for the sender to know that you are missing a packet (as opposed to them just determining this based on a timeout)
				* This is not scalable, because if the node dies the connection will just continue to be flood with information. There needs to be a way to know that the connection has died without it relying on the receiver sending a packet. 
		* ACKs on a cumulative sequence of packets
### TCP 

Ethernet MTU = 1500 became universal in the 1980s.

* 