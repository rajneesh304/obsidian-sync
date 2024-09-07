- [x] **Thread Priorities:** Understand how thread priorities influence thread scheduling.
- [ ] **Thread Group:** Learn about thread groups and how to manage multiple threads collectively.
- [ ] **Daemon Threads:** Understand what daemon threads are and how they differ from user threads.
---
## Thread Priorities
A thread's priority is a recommendation to the operating system to prefer one thread over another in any scheduling or CPU allocation decision point where these two threads are involved. But how this is implemented depends on the operating system and the JVM implementation.
```java
t1.setPriority(4);
t2.setPriority(5);

t1.getPriority();
t2.getPriority();
```
t2 will have higher priority.
Default priority of main thread is always 5 and it can be changed. Priority for other threads depend on parent thread's priority.
- The default priority is set to 5 as excepted.
- Minimum priority is set to 1.
- Maximum priority is set to 10.

[JavaMex](http://www.javamex.com/tutorials/threads/priority.shtml) has a nice discussion of thread priorities. The gist is that:
1. Priorities may have no effect at all.
2. Priorities are only _one_ part of a calculation that dictates scheduling.
3. Distinct Java priority values may be translated into the same value in practice (so for example, priority 10 and 9 may be the same).
4. Each OS makes its own decisions what to do with the priorities, as Java is using the underlying OS's threading mechanism.
---
## Thread Groups
- Every Java thread is a member of a _thread group_. 
- Thread groups provide a mechanism for collecting multiple threads into a single object and manipulating those threads all at once, rather than individually.
- A thread is a permanent member of whatever thread group it joins upon its creation--you cannot move a thread to a new group after the thread has been created.