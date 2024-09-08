- [x] **Intrinsic Locks and Synchronized Blocks:** Learn how to use the `synchronized` keyword to ensure that only one thread accesses a critical section at a time.
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
```java
class Counter {
    private int count = 0;

    public synchronized void increment() { // This method is synchronized
        count++;
    }

    public synchronized int getCount() { // This method is also synchronized
        return count;
    }
}
```
## Synchronized block
```java
class Counter {
    private int count = 0;
    private final Object lock = new Object(); // A dedicated lock object

    public void increment() {
        synchronized (lock) { // Synchronized block
            count++;
        }
    }

    public int getCount() {
        synchronized (lock) { // Synchronized block
            return count;
        }
    }
}
```
Synchronized block is **used to prevent multiple threads from executing a portion of a code in a method at the same point in time**. On the other hand, synchronized method will prevent multiple threads from executing the entire method at the same point in time.

#### Issues with synchronized 
- A thread can take a lock only once. Synchronized blocks don’t offer any mechanism of a waiting queue and after the exit of one thread, any thread can take the lock. 
- This could lead to starvation of resources for some other thread for a very long period of time.   

---
## Reentrant Lock
- The ReentrantLock class implements the Lock interface and provides synchronization to methods while accessing shared resources. The code which manipulates the shared resource is surrounded by calls to lock and unlock method. This gives a lock to the current working thread and blocks all other threads which are trying to take a lock on the shared resource.
```java
public void some_method()
{
        reentrantlock.lock();
        
          try{
            //Do some work
        }
  
        catch(Exception e){
            e.printStackTrace();
        }
  
        finally{
            reentrantlock.unlock();
        }
}
```
Methods: 
- ****lock():**** Call to the lock() method increments the hold count by 1 and gives the lock to the thread if the shared resource is initially free.
- ****unlock():**** Call to the unlock() method decrements the hold count by 1. When this count reaches zero, the resource is released.
- ****tryLock():**** If the resource is not held by any other thread, then call to tryLock() returns true and the hold count is incremented by one. If the resource is not free, then the method returns false, and the thread is not blocked, but exits.
- ****tryLock(long timeout, TimeUnit unit):**** As per the method, the thread waits for a certain time period as defined by arguments of the method to acquire the lock on the resource before exiting.
- ****lockInterruptibly():**** This method acquires the lock if the resource is free while allowing for the thread to be interrupted by some other thread while acquiring the resource. It means that if the current thread is waiting for the lock but some other thread requests the lock, then the current thread will be interrupted and return immediately without acquiring the lock.
- ****getHoldCount():**** This method returns the count of the number of locks held on the resource.
- ***isHeldByCurrentThread():** This method returns true if the lock on the resource is held by the current thread.
- **hasQueuedThread()**: This Method Queries whether the given thread is waiting to acquire this lock.
- **isLocked():** Queries if this lock is held by any thread.
- *newCondition()*: Returns a Condition instance for use with this Lock instance.