- **Multiprocessing -** Multiple Processors/CPUs executing concurrently. The unit of concurrency here is a CPU.
    
- **Multitasking -** Multiple tasks/processes running concurrently on a single CPU. The operating system executes these tasks by switching between them very frequently. The unit of concurrency, in this case, is a Process.
    
- **Multithreading -** Multiple parts of the same program running concurrently. In this case, we go a step further and divide the same program into multiple parts/threads and run those threads concurrently.

## Processes and Threads
#### **Process**
A Process is a program in execution. It has its own address space, a call stack, and link to any resources such as open files.

A computer system normally has multiple processes running at a time. The operating system keeps track of all these processes and facilitates their execution by sharing the processing time of the CPU among them.
#### **Thread**
A thread is a path of execution within a process. Every process has at least one thread - called the main thread. The main thread can create additional threads within the process.

Threads within a process share the process’s resources including memory and open files. However, every thread has its own call stack.

Since threads share the same address space of the process, creating new threads and communicating between them is more efficient.
