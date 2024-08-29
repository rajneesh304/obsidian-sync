**Observer** is a behavioral design pattern that lets you define a subscription mechanism to notify multiple objects about any events that happen to the object they’re observing.

**Example**
Imagine that you have two types of objects: a `Customer` and a `Store`. The customer is very interested in a particular brand of product (say, it’s a new model of the iPhone) which should become available in the store very soon. So the customer will get subscribed to the item in store and store will become a producer.

**Producer Code**
```java
public interface ObservableInterface {  
    void addObserver(ObserverInterface observer);  
    void deleteObserver(ObserverInterface observer);  
    void notifyObservers();  
    String getMessage();  
    void setMessage(String message);  
}
```

```java
public class Publisher implements ObservableInterface {  
    private List<ObserverInterface> list = new ArrayList<>();  
  
    private String message;  
  
    public Publisher(String message) {  
        this.message = message;  
    }  
  
    public String getMessage() {  
        return message;  
    }  
  
    public void setMessage(String message) {  
        this.message = message;  
        notifyObservers();  
    }  
  
    @Override  
    public void addObserver(ObserverInterface observer) {  
        list.add(observer);  
  
    }  
  
    @Override  
    public void deleteObserver(ObserverInterface observer) {  
        list.remove(observer);  
    }  
  
    @Override  
    public void notifyObservers() {  
        for(ObserverInterface observer : list) {  
            observer.update();  
        }  
    }  
}
```

**Subscriber code**
```java
public interface ObserverInterface {  
    public void update();  
}
```
```java

```