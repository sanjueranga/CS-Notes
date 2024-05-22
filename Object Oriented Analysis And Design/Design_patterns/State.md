### Where to Use

Use the State Pattern in the following scenarios:

- When an object's behavior depends on its state and it must change its behavior dynamically based on that state.
- When the operations have large, multipart conditional statements that depend on the object's state.
- When you want to avoid using conditional statements to represent different states of an object.

### Code Explanation

#### State Pattern Implementation

##### Step 1: Define the State Interface

```java
public interface State {
    void handle(Context context);
}

```

- The `State` interface declares a method that encapsulates state-specific behavior.

##### Step 2: Implement Concrete States

```java
public class ConcreteStateA implements State {
    @Override
    public void handle(Context context) {
        System.out.println("Handling state A.");
        context.setState(new ConcreteStateB());
    }
}

public class ConcreteStateB implements State {
    @Override
    public void handle(Context context) {
        System.out.println("Handling state B.");
        context.setState(new ConcreteStateA());
    }
}

```

- `ConcreteStateA` and `ConcreteStateB` implement the `State` interface and provide behavior specific to each state. They also trigger state transitions.

##### Step 3: Define the Context

```java
public class Context {
    private State state;

    public Context(State state) {
        this.state = state;
    }

    public void setState(State state) {
        this.state = state;
    }

    public void request() {
        state.handle(this);
    }
}

```

- The `Context` class maintains a reference to the current state object and delegates state-specific behavior to the state object.

##### Step 4: Client Code

```java
public class StatePatternExample {
    public static void main(String[] args) {
        Context context = new Context(new ConcreteStateA());

        context.request();
        context.request();
        context.request();
    }
}

```

### Real World Example

Consider a traffic light system where the behavior of the traffic light changes based on its current state (e.g., red, yellow, green). The State Pattern can be used to represent each state and define the transitions between states.

```java
// State interface
public interface TrafficLightState {
    void handle();
}

// Concrete States
public class RedState implements TrafficLightState {
    @Override
    public void handle() {
        System.out.println("Red light - Stop");
    }
}

public class YellowState implements TrafficLightState {
    @Override
    public void handle() {
        System.out.println("Yellow light - Prepare to stop");
    }
}

public class GreenState implements TrafficLightState {
    @Override
    public void handle() {
        System.out.println("Green light - Go");
    }
}

// Context
public class TrafficLight {
    private TrafficLightState state;

    public TrafficLight() {
        this.state = new RedState();
    }

    public void setState(TrafficLightState state) {
        this.state = state;
    }

    public void changeState() {
        if (state instanceof RedState) {
            setState(new GreenState());
        } else if (state instanceof GreenState) {
            setState(new YellowState());
        } else if (state instanceof YellowState) {
            setState(new RedState());
        }
    }

    public void request() {
        state.handle();
        changeState();
    }
}

// Client code
public class TrafficLightSystem {
    public static void main(String[] args) {
        TrafficLight trafficLight = new TrafficLight();

        for (int i = 0; i < 3; i++) {
            trafficLight.request();
        }
    }
}

```

In this example, each state of the traffic light (red, yellow, green) is represented by a concrete state class. The `TrafficLight` class acts as the context, and it changes its state based on the current state and requests from the client. This allows the traffic light to transition between states dynamically.