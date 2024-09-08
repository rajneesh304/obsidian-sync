## Executors
ref. https://www.baeldung.com/java-executor-service-tutorial

- Executor is a JDK API that simplifies running tasks in asynchronous mode. Generally speaking, _ExecutorService_ automatically provides a pool of threads and an API for assigning tasks to it.
instantiating ExecutorService through Executors factory: 
```java
import java.util.concurrent.ExecutorService;  
import java.util.concurrent.Executors;  
  
public class ExecutorFactory {  
    ExecutorService executor = Executors.newFixedThreadPool(10);  
      
}
```
- ExecutorService can execute _Runnable_ and _Callable_ tasks.
We can assign tasks to the _ExecutorService_ using several methods including _execute()_, which is inherited from the _Executor_ interface, and also _submit()_, _invokeAny()_ and _invokeAll()_

- The **_execute()_** method is _void_ and doesn’t give any possibility to get the result of a task’s execution or to check the task’s status (is it running):

```java
executorService.execute(runnableTask);
```

- **_submit()_** submits a _Callable_ or a _Runnable_ task to an _ExecutorService_ and returns a result of type _Future_:

```java
Future<String> future = 
  executorService.submit(callableTask);
```

- **_invokeAny()_** assigns a collection of tasks to an _ExecutorService_, causing each to run, and returns the result of a successful execution of one task (if there was a successful execution):

```java
String result = executorService.invokeAny(callableTasks);
```

- _**invokeAll()**_ assigns a collection of tasks to an _ExecutorService_, causing each to run, and returns the result of all task executions in the form of a list of objects of type _Future_:

```java
List<Future<String>> futures = executorService.invokeAll(callableTasks);
```

#### **Shutting Down an _ExecutorService_**
In general, the _ExecutorService_ will not be automatically destroyed when there is no task to process. It will stay alive and wait for new work to do.

The _**shutdown()**_ method doesn’t cause immediate destruction of the _ExecutorService_. It will make the _ExecutorService_ stop accepting new tasks and shut down after all running threads finish their current work:
```java
es.shutdown();
```

The **_shutdownNow()_** method tries to destroy the _ExecutorService_ immediately, but it doesn’t guarantee that all the running threads will be stopped at the same time:
```java
List<Runnable> notExecutedTasks = es.shutDownNow();
```
## Fork/Join framework
- It provides tools to help speed up parallel processing by attempting to use all available processor cores. It accomplishes this **through a divide and conquer approach.**
- To provide effective parallel execution, the fork/join framework uses a pool of threads called the _ForkJoinPool_. This pool manages worker threads of type _ForkJoinWorkerThread_.

### ForkJoinPool
- The _ForkJoinPool_ is the heart of the framework. It is an implementation of the _[ExecutorService](https://www.baeldung.com/java-executor-service-tutorial)_ that manages worker threads and provides us with tools to get information about the thread pool state and performance.
- Worker threads can execute only one task at a time, but the _ForkJoinPool_ doesn’t create a separate thread for every single subtask. Instead, each thread in the pool has its own double-ended queue that stores tasks.
#### Work-Stealing Algorithm

