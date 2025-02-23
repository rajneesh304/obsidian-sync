- In primary-secondary replication, the primary node is a bottleneck and a single point of failure. Moreover, it helps to achieve read scalability but fails to provide write scalability. 
- The **peer-to-peer replication** model resolves these problems by not having a single primary node. All the nodes have equal weightage and can accept read and write requests. This replication scheme can be found in the Cassandra database.
- Like primary-secondary replication, this replication can also yield inconsistency. This is because when several nodes accept write requests, it may lead to concurrent writes. A helpful approach used for solving write-write inconsistency is called **quorums**.
![[Pasted image 20250223123906.png]]

#### Quorums
Let’s suppose we have three nodes. If at least two out of three nodes are guaranteed to return successful updates, it means only one node has failed. This means that if we read from two nodes, at least one of them will have the updated version, and our system can continue working.

If we have *n* nodes, then every write must be updated in at least *w* nodes to be considered a success, and we must read from *r* nodes. We’ll get an updated value from reading as long as ***w+r>n*** because at least one of the nodes must have an updated write from which we can read. Quorum reads and writes adhere to these rr and ww values. These nn, ww, and rr are configurable in Dynamo-style databases.