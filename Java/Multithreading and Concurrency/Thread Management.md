- [ ] **Thread Priorities:** Understand how thread priorities influence thread scheduling.
- [ ] **Thread Group:** Learn about thread groups and how to manage multiple threads collectively.
- [ ] **Daemon Threads:** Understand what daemon threads are and how they differ from user threads.

## Thread Priorities
```java
t1.setPriority(4);
t2.setPriority(5);
```
t2 will have higher priority.
Default priority of main thread is always 5 and it can be changed. Priority for other threads depend on parent thread
