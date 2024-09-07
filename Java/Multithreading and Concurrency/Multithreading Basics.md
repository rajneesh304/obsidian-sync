- **Multiprocessing -** Multiple Processors/CPUs executing concurrently. The unit of concurrency here is a CPU.
    
- **Multitasking -** Multiple tasks/processes running concurrently on a single CPU. The operating system executes these tasks by switching between them very frequently. The unit of concurrency, in this case, is a Process.
    
- **Multithreading -** Multiple parts of the same program running concurrently. In this case, we go a step further and divide the same program into multiple parts/threads and run those threads concurrently.

## Processes and Threads

| Process                                    | Thread                                   |
| ------------------------------------------ | ---------------------------------------- |
| Process means any program is in execution. | Thread means a segment of a process.     |
| The process takes more time to terminate.  | The thread takes less time to terminate. |
| It takes more time for creation.           |                                          |
|                                            |                                          |
|                                            |                                          |
|                                            |                                          |
Since threads share the same address space of the process, creating new threads and communicating between them is more efficient.

