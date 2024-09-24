## Power of two

```
 2^10 == ~1000 == 1kb
 2^20 == ~1mil == 1mb
 2^30 == ~1bil == 1gb
 2^40 == ~1tril == 1tb
 2^50 == ~1quad == 1pb
 ```

## Latency numbers every programmer should know

```
L1 cache reference == 0.5ns
Branch mispredict == 5ns
Mutex lock/unlock == 100ns
Main memory reference == 100ns
Compress 1kb == 10,000ns == 10us
Send 2kb over 1gbps network == 20,000ns == 20us
Read 1mb sequentially from memory == 250us
Round trip within same DC == 500us
Disk seek == 10ms
Read 1mb sequentially from network == 10ms
Read 1mb sequentially from disk == 30ms
Send packet CA->Netherlands->CA == 150ms
```

- Memory is fast, disk is slow
- Avoid disk seeks if possible
- Compression is usually fast
- Compress data before sending over the network if possible
- Data centers round trips are expensive

## Availability numbers
High availability == ability of a system to be continuously operational. In other words, minimizing downtime.

Typically, services aim for availability in the range of 99% to 100%.

An SLA is a formal agreement between a service provider and a customer. This formally defines the level of uptime your service needs to support.

Cloud providers typically set their uptime at 99.9% or more. Eg AWS EC2 has an SLA of 99.99%

![[sla-chart.png]]

_Commonly asked estimations to make - QPS (queries per second), peak QPS, storage, cache, number of servers._

