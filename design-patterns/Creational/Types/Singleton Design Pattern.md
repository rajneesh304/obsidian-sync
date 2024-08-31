- Singleton pattern restricts the instantiation of a class and ensures that only one instance of the class exists in the Java Virtual Machine.
- The singleton class must provide a global access point to get the instance of the class.
- Singleton pattern is used for [logging](https://www.digitalocean.com/community/tutorials/logger-in-java-logging-example), drivers objects, caching, and [thread pool](https://www.digitalocean.com/community/tutorials/threadpoolexecutor-java-thread-pool-example-executorservice).
- Singleton design pattern is also used in other design patterns like [Abstract Factory](https://www.digitalocean.com/community/tutorials/abstract-factory-design-pattern-in-java), [Builder](https://www.digitalocean.com/community/tutorials/builder-design-pattern-in-java), [Prototype](https://www.digitalocean.com/community/tutorials/prototype-design-pattern-in-java), [Facade](https://www.digitalocean.com/community/tutorials/facade-design-pattern-in-java), etc.
- Singleton design pattern is used in core Java classes also (for example, `java.lang.Runtime`, `java.awt.Desktop`).

## Implementation considerations
To implement a singleton pattern, we have different approaches, but all of them have the following common concepts.
- Private constructor to restrict instantiation of the class from other classes.
- Private static variable of the same class that is the only instance of the class.
- Public static method that returns the instance of the class, this is the global access point for the outer world to get the instance of the singleton class.

## Implementation approaches

### Eager initialization
In eager initialization, the instance of the singleton class is created at the time of class loading.  
**Drawback:** to eager initialization is that the method is created even though the client application might not be using it.
```java
public class EagerInitializedSingleton {

    private static final EagerInitializedSingleton instance = new EagerInitializedSingleton();

    // private constructor to avoid client applications using the constructor
    private EagerInitializedSingleton(){}

    public static EagerInitializedSingleton getInstance() {
        return instance;
    }
}
```

If your singleton class is not using a lot of resources, this is the approach to use. 
But in most of the scenarios, singleton classes are created for resources such as File System, Database connections, etc.