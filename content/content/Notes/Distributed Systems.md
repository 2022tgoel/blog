[[PBFT]]
## FaRM
FaRM uses optimistic concurrency control to consistency

### Reading
You want to read a bunch of objects stored on different servers. You issue RDMA reads to get the objects and the *versions* of the objects. 

It's possible that write transactions happened in the middle and modified the objects that you read.

If the transaction occurred before you read any of the objects modified by the transaction, it doesn't matter (same thing if it happened totally after). If the transaction happened in between, then it must be that at the end of the all of the reads, one of the versions read doesn't match the version stored. 

This motivates a *validation* phase: you check that all of the versions match the ones read, and return success if so. 

### Writing

For write transactions, you have a similar validation phase. However, it's actually split up into *lock* and *validate*. For writes, you not only need to check that the version still matches what was read, but also make sure that no other transaction tries to write to that object. You could have locked at the beginning, but this is a bit better because it holds the lock for less time. 

The lock is implemented through a compare-and-swap of the versions. This doesn't change the actual version of the object or the actual data stored at the object. That happens later when all of the locks have been grabbed successfully and all of the reads have been validated. 

Commit: first to the backups and then to the primaries. 


