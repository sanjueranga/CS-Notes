1. Factory Method
```java
public interface Product {}

public abstract class Creator {
    abstract Product factoryMethod();
}


```

2. Abstract Factory

```java
public interface AbstractFactory {
    ProductA createProductA();
    ProductB createProductB();
}

public interface ProductA {}
public interface ProductB {}

```

3. Singleton
```java
public class Singleton {
    private static Singleton instance;
    private Singleton() {}
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}

```

4. Prototype

```java
public interface Prototype {
    Prototype clone();
}

```

5. Adapter

```java
public interface Target {
    void request();
}

public class Adapter implements Target {
    private Adaptee adaptee;
    public Adapter(Adaptee adaptee) {
        this.adaptee = adaptee;
    }
    public void request() {
        adaptee.specificRequest();
    }
}

```


6. Proxy


```java
public interface Subject {
    void request();
}

public class Proxy implements Subject {
    private RealSubject realSubject;
    public void request() {
        if (realSubject == null) {
            realSubject = new RealSubject();
        }
        realSubject.request();
    }
}

```

8. Facade
```java
public class Facade {
    private Subsystem1 subsystem1;
    private Subsystem2 subsystem2;
    public void operation() {
        subsystem1.method1();
        subsystem2.method2();
    }
}

```
9. Strategy

```java
public interface Strategy {
    void execute();
}

public class Context {
    private Strategy strategy;
    public void setStrategy(Strategy strategy) {
        this.strategy = strategy;
    }
    public void executeStrategy() {
        strategy.execute();
    }
}

```

10. State

```java

public interface State {
    void handle(Context context);
}

public class Context {
    private State state;
    public void setState(State state) {
        this.state = state;
    }
    public void request() {
        state.handle(this);
    }
}

```

11. Command

```java

public interface Command {
    void execute();
}

public class Invoker {
    private Command command;
    public void setCommand(Command command) {
        this.command = command;
    }
    public void executeCommand() {
        command.execute();
    }
}

```



12. Observer

```java

public interface Observer {
    void update();
}

public interface Subject {
    void attach(Observer observer);
    void detach(Observer observer);
    void notifyObservers();
}

```
13. Template Method

```java
public abstract class AbstractClass {
    final void templateMethod() {
        step1();
        step2();
        step3();
    }
    abstract void step1();
    abstract void step2();
    abstract void step3();
}

```
