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

## Thread Lifecycle
![[Screenshot_20240907_232903.png]]
