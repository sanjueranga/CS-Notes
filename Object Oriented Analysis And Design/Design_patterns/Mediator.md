### Where to Use

Use the Mediator Pattern in the following scenarios:

- When a set of objects communicate in complex but well-defined ways.
- When reusing an object is difficult because it refers to and communicates with many other objects.
- When you want to make a system easier to understand by encapsulating complex protocols and workflows.

### Code Explanation

#### Mediator Pattern Implementation

##### Step 1: Define the Mediator Interface

```java
public interface Mediator {
    void notify(Component sender, String event);
}

```

- The `Mediator` interface declares a method for communicating with components.

##### Step 2: Implement Concrete Mediator

```java
public class ConcreteMediator implements Mediator {
    private ComponentA componentA;
    private ComponentB componentB;

    public void setComponentA(ComponentA componentA) {
        this.componentA = componentA;
    }

    public void setComponentB(ComponentB componentB) {
        this.componentB = componentB;
    }

    @Override
    public void notify(Component sender, String event) {
        if (event.equals("A")) {
            System.out.println("Mediator reacts on A and triggers following operations:");
            componentB.doB();
        } else if (event.equals("B")) {
            System.out.println("Mediator reacts on B and triggers following operations:");
            componentA.doA();
        }
    }
}

```

- `ConcreteMediator` coordinates the interaction between components. It has references to the components and triggers their methods based on events.

##### Step 3: Define Component Interface

```java
public abstract class Component {
    protected Mediator mediator;

    public Component(Mediator mediator) {
        this.mediator = mediator;
    }

    public void setMediator(Mediator mediator) {
        this.mediator = mediator;
    }
}

```

- The `Component` abstract class has a reference to the mediator and provides a method to set the mediator.

##### Step 4: Implement Concrete Components

```java
public class ComponentA extends Component {
    public ComponentA(Mediator mediator) {
        super(mediator);
    }

    public void doA() {
        System.out.println("Component A does A.");
        mediator.notify(this, "A");
    }
}

public class ComponentB extends Component {
    public ComponentB(Mediator mediator) {
        super(mediator);
    }

    public void doB() {
        System.out.println("Component B does B.");
        mediator.notify(this, "B");
    }
}

```

- `ComponentA` and `ComponentB` are concrete implementations of the `Component` class. They notify the mediator about their events.

##### Step 5: Client Code

```java
public class MediatorPatternExample {
    public static void main(String[] args) {
        ConcreteMediator mediator = new ConcreteMediator();

        ComponentA componentA = new ComponentA(mediator);
        ComponentB componentB = new ComponentB(mediator);

        mediator.setComponentA(componentA);
        mediator.setComponentB(componentB);

        componentA.doA();
        componentB.doB();
    }
}

```

```java
import java.util.ArrayList;
import java.util.List;

// Mediator interface
public interface ChatMediator {
    void sendMessage(String message, User user);
    void addUser(User user);
}

// Concrete Mediator
public class ChatRoom implements ChatMediator {
    private List<User> users;

    public ChatRoom() {
        this.users = new ArrayList<>();
    }

    @Override
    public void addUser(User user) {
        this.users.add(user);
    }

    @Override
    public void sendMessage(String message, User user) {
        for (User u : users) {
            // Message should not be received by the user sending it
            if (u != user) {
                u.receive(message);
            }
        }
    }
}

// Abstract Colleague
public abstract class User {
    protected ChatMediator mediator;
    protected String name;

    public User(ChatMediator mediator, String name) {
        this.mediator = mediator;
        this.name = name;
    }

    public abstract void send(String message);
    public abstract void receive(String message);
}

// Concrete Colleague
public class ChatUser extends User {
    public ChatUser(ChatMediator mediator, String name) {
        super(mediator, name);
    }

    @Override
    public void send(String message) {
        System.out.println(this.name + " sends: " + message);
        mediator.sendMessage(message, this);
    }

    @Override
    public void receive(String message) {
        System.out.println(this.name + " receives: " + message);
    }
}

// Client code
public class ChatApplication {
    public static void main(String[] args) {
        ChatMediator chatMediator = new ChatRoom();

        User user1 = new ChatUser(chatMediator, "User1");
        User user2 = new ChatUser(chatMediator, "User2");
        User user3 = new ChatUser(chatMediator, "User3");

        chatMediator.addUser(user1);
        chatMediator.addUser(user2);
        chatMediator.addUser(user3);

        user1.send("Hello everyone!");
        user2.send("Hi User1!");
    }
}

```

In this example, the `ChatRoom` class acts as a mediator that facilitates the communication between `ChatUser` objects. Each user sends messages through the mediator, which then broadcasts the message to all other users. This ensures that the users do not need to reference each other directly, promoting loose coupling.