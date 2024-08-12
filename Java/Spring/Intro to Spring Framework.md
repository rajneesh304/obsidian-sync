# What is Spring framework?
Basically Spring is a framework for [dependency-injection](https://stackoverflow.com/questions/tagged/dependency-injection "show questions tagged 'dependency-injection'") which is a pattern that allows building very decoupled systems.

## The problem

For example, suppose you need to list the users of the system and thus declare an interface called `UserLister`:

```java
public interface UserLister {
    List<User> getUsers();
}
```

And maybe an implementation accessing a database to get all the users:

```java
public class UserListerDB implements UserLister {
    public List<User> getUsers() {
        // DB access code here
    }
}
```

In your view you'll need to access an instance (just an example, remember):

```java
public class SomeView {
    private UserLister userLister;

    public void render() {
        List<User> users = userLister.getUsers();
        view.render(users);
    }
}
```

Note that the code above hasn't initialized the variable `userLister`. What should we do? If I explicitly instantiate the object like this:

```java
UserLister userLister = new UserListerDB();
```

...I'd couple the view with my implementation of the class that access the DB. What if I want to switch from the DB implementation to another that gets the user list from a comma-separated file (remember, it's an example)? In that case, I would go to my code again and change the above line to:

```java
UserLister userLister = new UserListerCommaSeparatedFile();
```

This has no problem with a small program like this but... What happens in a program that has hundreds of views and a similar number of business classes? The maintenance becomes a nightmare!

## Spring (Dependency Injection) approach

What Spring does is to _wire_ the classes up by using an XML file or annotations, this way all the objects are instantiated and initialized by Spring and _injected_ in the right places (Servlets, Web Frameworks, Business classes, DAOs, etc, etc, etc...).

Going back to the example in Spring we just need to have a setter for the `userLister` field and have either an XML file like this:

```xml
<bean id="userLister" class="UserListerDB" />

<bean class="SomeView">
    <property name="userLister" ref="userLister" />
</bean>
```

or more simply annotate the filed in our view class with `@Inject`:

```java
@Inject
private UserLister userLister;
```

This way when the view is created it _magically_ will have a `UserLister` ready to work.

```java
List<User> users = userLister.getUsers();  // This will actually work
                                           // without adding any line of code
```

It is great! Isn't it?

- _What if you want to use another implementation of your `UserLister` interface?_ Just change the XML.
- _What if don't have a `UserLister` implementation ready?_ Program a temporal mock implementation of `UserLister` and ease the development of the view.
- _What if I don't want to use Spring anymore?_ Just don't use it! Your application isn't coupled to it. [Inversion of Control](http://en.wikipedia.org/wiki/Inversion_of_control) states: "The application controls the framework, not the framework controls the application".

There are some other options for Dependency Injection around there, what in my opinion has made Spring so famous besides its simplicity, elegance and stability is that the guys of SpringSource have programmed many many POJOs that help to integrate Spring with many other common frameworks without being intrusive in your application. Also, Spring has several good subprojects like Spring MVC, Spring WebFlow, Spring Security and again a loooong list of etceteras.

Anyway, I encourage you to read [Martin Fowler's article](http://martinfowler.com/articles/injection.html) about Dependency Injection and Inversion of Control because he does it better than me. ~~After understanding the basics take a look at [Spring Documentation](http://static.springframework.org/spring/docs/2.5.x/reference/index.html)~~, in my opinion, it ~~is~~ **used to be** the best Spring book ever.


# What is annotation?
Annotations are used to provide supplemental information about a program.
- Annotations start with ‘**@**’.
- Annotations do not change the action of a compiled program.
- Annotations help to associate _metadata_ (information) to the program elements i.e. instance variables, constructors, methods, classes, etc.
- Annotations are not pure comments as they can change the way a program is treated by the compiler. See below code for example.
- Annotations basically are used to provide additional information, so could be an alternative to XML and Java marker interfaces.