**Single Leader or primary-secondary replication**

- In **primary-secondary replication,** data is replicated across multiple nodes. One node is designated as the primary. It’s responsible for processing any writes to data stored on the cluster. It also sends all the writes to the secondary nodes and keeps them in sync.
- Primary-secondary replication is **appropriate when our workload is read-heavy**. However, replicating data to many followers can make a primary bottleneck.
- primary-secondary replication is **inappropriate if our workload is write-heavy**.
- It’s **read resilient**. Secondary nodes can still handle read requests in case of primary node failure. Therefore, it’s a helpful approach for read-intensive applications.
- Replication via this approach comes with **inconsistency if we use asynchronous replication**.

### Replication Strategies:
1. **Statement-based replication (SBR)** is an approach used in MySQL databases. In this approach, the primary node executes the SQL statements such as `INSERT`, `UPDATE`, `DELETE`, etc., and then the statements are written into a log file. In the next step, the log file is sent to the secondary nodes for execution. This type of replication was used in MySQL before version 5.1.
