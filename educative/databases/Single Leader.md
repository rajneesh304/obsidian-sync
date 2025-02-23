**Single Leader or primary-secondary replication**

- In **primary-secondary replication,** data is replicated across multiple nodes. One node is designated as the primary. It’s responsible for processing any writes to data stored on the cluster. It also sends all the writes to the secondary nodes and keeps them in sync.
- Primary-secondary replication is **appropriate when our workload is read-heavy**. However, replicating data to many followers can make a primary bottleneck.
- primary-secondary replication is **inappropriate if our workload is write-heavy**.
- It’s **read resilient**. Secondary nodes can still handle read requests in case of primary node failure. Therefore, it’s a helpful approach for read-intensive applications.
- 