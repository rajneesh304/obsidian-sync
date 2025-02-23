**Single Leader or primary-secondary replication**

- In **primary-secondary replication,** data is replicated across multiple nodes. One node is designated as the primary. It’s responsible for processing any writes to data stored on the cluster. It also sends all the writes to the secondary nodes and keeps them in sync.
- Primary-secondary replication is **appropriate when our workload is read-heavy**. However, replicating data to many followers can make a primary bottleneck.
- primary-secondary replication is **inappropriate if our workload is write-heavy**.
- It’s **read resilient**. Secondary nodes can still handle read requests in case of primary node failure. Therefore, it’s a helpful approach for read-intensive applications.
- Replication via this approach comes with **inconsistency if we use asynchronous replication**.

### Replication Strategies:
1. **Statement-based replication (SBR)** is an approach used in MySQL databases. In this approach, the primary node executes the SQL statements such as `INSERT`, `UPDATE`, `DELETE`, etc., and then the statements are written into a log file. In the next step, the log file is sent to the secondary nodes for execution. This type of replication was used in MySQL before version 5.1.
   Disadvantage: Any nondeterministic functions such as `NOW()` might result in distinct writes on the primary and secondary nodes.
2. **Write-ahead log (WAL) shipping** is a data replication technique used in both PostgreSQL and Oracle. In this technique, when a transaction occurs, it’s initially recorded in a transactional log file, and the log file is written to disk. Subsequently, the recorded operations are executed on the primary database before being transmitted to secondary nodes for execution. Unlike SBR, WAL maintains transactional logs instead of SQL statements into a log file, ensuring consistency when dealing with nondeterministic functions. Writing to disk also aids in recovery in case of crash failures.
   Disadvantage: Tight coupling with the inner structure of the database engine, making software upgrades on the leader and followers complicated.
3. **Logical (row-based) replication** is utilized in various relational databases, including PostgreSQL and MySQL. In this approach, changes made to the database are captured at the level of individual rows and then replicated to the secondary nodes. Instead of replicating the actual physical changes made to the database, this approach captures the operations in a logical format and then executes them on secondary nodes.
