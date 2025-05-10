https://pdos.csail.mit.edu/6.824/papers/castro-practicalbft.pdf

The setting for PBFT is that you want to implement a replicated state machine with $f$ faulty servers. E.g. there is some software vulnerability, and you can't guarantee the behavior of these machines. 

We can guarantee correct behavior if a majority of non-faulty servers agree to an operation. This motivates the following algorithm on $|R| - 3f + 1$ machines:

### Total Order: Algorithm #1
2. Client multicasts the message to all of the servers
3. Servers execute op
4. Client waits for $2 f + 1$ replies
This guarantees $f + 1$ out of $2f+1$ non-faulty servers execute the request. This means that for any two operations, at least one non-faulty server executed both operations. This means for any pair of operations, you know the order. You can resolve all of these orderings to get a full total order (linearization) of all of the operations.

### Algorithm #2 
A total order isn't all that we want. We also want to be able to guarantee that any server that executes an operation has executed the full log of operations that preceded it. This motivates having a primary serve as a linearization point -- you need a single server to know the order of all of the operations. 

1. Client sends request to primary (leader) of the current view (term). This is fixed to be $v \; \text{mod} \; |R|$, where $v$ is the view number.
2. Primary multicasts the message to all of the servers, with a sequence number $n$
3. Servers execute op, checking that the sequence number is the last sequence number$+ 1$ 
4. Client waits for $2 f + 1$ replies

The lecture motivates the introduction of a primary as a way of dealing with multiple clients. I'm not sure this makes sense to me.

**What if the view changes?**

The biggest issues come with dealing with multiple clients and view changes. 

When a view changes, you need to be sure that the new primary won't be able to drop operations that have committed (imagine a raft where the server starts acting as leader of a new term even though it hasn't guaranteed that its log is up-to-date). However, in the current scheme, the servers don't know if an operation has committed. 

This motivates adding a **prepare** phase, where the servers multicast their acknowledgement of the message to all of the other servers. If you receive $2f + 1$ prepare messages, you know that the operation has been replicated fault-tolerantly. At this point, you can both commit the message and enforce that the message shows up in any new views by tagging in it view change requests. 

The paper also mentions multicasting the commit message. I'm not sure why this can't just go directly to the client -- the lecturer didn't seem to know either. Should think.
