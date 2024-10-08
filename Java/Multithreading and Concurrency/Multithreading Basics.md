- **Multiprocessing -** Multiple Processors/CPUs executing concurrently. The unit of concurrency here is a CPU.
    
- **Multitasking -** Multiple tasks/processes running concurrently on a single CPU. The operating system executes these tasks by switching between them very frequently. The unit of concurrency, in this case, is a Process.
    
- **Multithreading -** Multiple parts of the same program running concurrently. In this case, we go a step further and divide the same program into multiple parts/threads and run those threads concurrently.

## Processes and Threads

| Process                                                                              | Thread                                                                                                                                                                       |
| ------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Process means any program is in execution.                                           | Thread means a segment of a process.                                                                                                                                         |
| The process takes more time to terminate.                                            | The thread takes less time to terminate.                                                                                                                                     |
| It takes more time for creation.                                                     | It takes less time for creation.                                                                                                                                             |
| It also takes more time for context switching.                                       | It takes less time for context switching.                                                                                                                                    |
| The process is less efficient in terms of communication.                             | Thread is more efficient in terms of communication.                                                                                                                          |
| Multiprogramming holds the concepts of multi-process.                                | We don’t need multi programs in action for multiple threads because a single process consists of multiple threads.                                                           |
| The process is isolated.                                                             | Threads share memory.                                                                                                                                                        |
| The process is called the heavyweight process.                                       | A Thread is lightweight as each thread in a process shares code, data, and resources.                                                                                        |
| Process switching uses an interface in an operating system.                          | Thread switching does not require calling an operating system and causes an interrupt to the kernel.                                                                         |
| If one process is blocked, then it will not affect the execution of other processes. | If a user-level thread is blocked, then all other user-level threads are blocked.                                                                                            |
| The process has its own Process Control Block, Stack, and Address Space.             | Thread has Parents’ PCB, its own Thread Control Block, and Stack and common Address space.                                                                                   |
| Changes to the parent process do not affect child processes.                         | Since all threads of the same process share address space and other resources so any changes to the main thread may affect the behavior of the other threads of the process. |
| A system call is involved in it.                                                     | No system call is involved, it is created using APIs.                                                                                                                        |
| The process does not share data with each other.                                     | Threads share data with each other.                                                                                                                                          |

---

## Thread Lifecycle
![[Screenshot_20240907_232903.png]]
**New:** Whenever a new thread is created, it is always in the new state. For a thread in the new state, the code has not been run yet and thus has not begun its execution.

**Active:** When a thread invokes the start() method, it moves from the new state to the active state. The active state contains two states within it: one is **runnable**, and the other is **running**.

- **Runnable:** A thread, that is ready to run is then moved to the runnable state. In the runnable state, the thread may be running or may be ready to run at any given instant of time. It is the duty of the thread scheduler to provide the thread time to run, i.e., moving the thread the running state.  
    A program implementing multithreading acquires a fixed slice of time to each individual thread. Each and every thread runs for a short span of time and when that allocated time slice is over, the thread voluntarily gives up the CPU to the other thread, so that the other threads can also run for their slice of time. Whenever such a scenario occurs, all those threads that are willing to run, waiting for their turn to run, lie in the runnable state. In the runnable state, there is a queue where the threads lie.
- **Running:** When the thread gets the CPU, it moves from the runnable to the running state. Generally, the most common change in the state of a thread is from runnable to running and again back to runnable.

**Blocked or Waiting:** Whenever a thread is inactive for a span of time (not permanently) then, either the thread is in the blocked state or is in the waiting state.

**Timed Waiting:** Sometimes, waiting for leads to starvation. For example, a thread (its name is A) has entered the critical section of a code and is not willing to leave that critical section. In such a scenario, another thread (its name is B) has to wait forever, which leads to starvation. To avoid such scenario, a timed waiting state is given to thread B. Thus, thread lies in the waiting state for a specific span of time, and not forever. A real example of timed waiting is when we invoke the sleep() method on a specific thread. The sleep() method puts the thread in the timed wait state. After the time runs out, the thread wakes up and start its execution from when it has left earlier.

**Terminated:** A thread reaches the termination state because of the following reasons:

- When a thread has finished its job, then it exists or terminates normally.
- **Abnormal termination:** It occurs when some unusual events such as an unhandled exception or segmentation fault.

---
## Java thread implementation
Multithreading can be achieved using 2 ways: 
1. Extending Threads class
   ```java
   class MyThread extends Thread {
    @Override
    public void run() {
        // something something
    }
}

public class ThreadExample {
    public static void main(String[] args) {
        MyThread thread1 = new MyThread();
        MyThread thread2 = new MyThread();

        thread1.start(); // Start the first thread
        thread2.start(); // Start the second thread
    }
}
```
2. Implementing Runnable interface
```java
public class LambdaRunnableExample {
    public static void main(String[] args) {
        Runnable runnable = () -> {
        // Something something
        };

        Thread thread1 = new Thread(runnable);
        Thread thread2 = new Thread(runnable);

        thread1.start(); // Start the first thread
        thread2.start(); // Start the second thread
    }
}
```

> [!NOTE]
> _Inherit less, interface more._

| Feature          | Runnable                                                              | Thread                                                          |
| ---------------- | --------------------------------------------------------------------- | --------------------------------------------------------------- |
| Implementation   | This is an Interface                                                  | This is a Class                                                 |
| Inheritance      | The child class can extend another class                              | The child class cannot extend another class                     |
| Code Reusability | A single instance can be shared among multiple threads                | Each thread needs a new instance                                |
| Resource Sharing | Allows sharing of resources among multiple threads                    | More difficult to share resources                               |
| Memory Overhead  | Lower memory overhead as no separate object is created for the thread | Higher memory overhead as each thread object has its own memory |
