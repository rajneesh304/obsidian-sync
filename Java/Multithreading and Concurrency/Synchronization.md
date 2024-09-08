- [ ] **Intrinsic Locks and Synchronized Blocks:** Learn how to use the `synchronized` keyword to ensure that only one thread accesses a critical section at a time.
- [ ] **Reentrant Locks:** Study the `ReentrantLock` class from `java.util.concurrent.locks` package for more control over locking.
- [ ] **Atomic Operations:** Learn about atomic classes like `AtomicInteger`, `AtomicBoolean`, and `AtomicReference` for lock-free thread-safe operations.
## Intrinsic Lock and Synchronized Blocks
- An intrinsic lock, also known as a monitor lock, is a fundamental concept in Java concurrency that is associated with every object and class. 
- It is used to manage access to synchronized blocks or methods to ensure that only one thread at a time can execute a block of code that is protected by a lock on the same object.

### Key Concepts of Intrinsic Locks:
1. **Synchronized Methods and Blocks:**
    - When a thread enters a synchronized method or block, it automatically acquires the intrinsic lock (monitor) associated with the object whose method or block it is accessing.
    - Other threads attempting to execute the same synchronized block or method on the same object must wait until the first thread releases the lock.
2. **Locking on Objects:**
    - In instance methods, the intrinsic lock is associated with the instance of the object (i.e., `this`).
    - In static methods, the intrinsic lock is associated with the `Class` object representing the class.
3. **Reentrancy:**
    - Java's intrinsic locks are reentrant, meaning that if a thread holds an intrinsic lock, it can re-enter any synchronized block or method that requires the same lock without being blocked.
    - This is useful in scenarios where synchronized methods or blocks call other synchronized methods on the same object.