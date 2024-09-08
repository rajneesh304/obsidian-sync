## Executors
- Executor is a JDK API that simplifies running tasks in asynchronous mode. Generally speaking, _ExecutorService_ automatically provides a pool of threads and an API for assigning tasks to it.
instantiating ExecutorService through Executors factory: 
```java
import java.util.concurrent.ExecutorService;  
import java.util.concurrent.Executors;  
  
public class ExecutorFactory {  
    ExecutorService executor = Executors.newFixedThreadPool(10);  
      
}
```
- ExecutorService_ can execute _Runnable_ and _Callable_ tasks.
- 