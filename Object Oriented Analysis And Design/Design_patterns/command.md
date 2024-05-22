### Where to Use

Use the Command Pattern in the following scenarios:

- When you need to parameterize objects with operations.
- When you need to create a queue of requests.
- When you want to support undo and redo operations.
- When you want to log operations so that they can be reapplied if the system crashes.

### Code Explanation

#### Command Pattern Implementation

##### Step 1: Define the Command Interface

```java
public interface Command {
    void execute();
}

`````
- The `Command` interface declares the `execute` method, which will be implemented by all concrete commands.

##### Step 2: Implement Concrete Commands
```java
// Concrete Command for turning on the light
public class LightOnCommand implements Command {
    private Light light;

    public LightOnCommand(Light light) {
        this.light = light;
    }

    @Override
    public void execute() {
        light.turnOn();
    }
}

// Concrete Command for turning off the light
public class LightOffCommand implements Command {
    private Light light;

    public LightOffCommand(Light light) {
        this.light = light;
    }

    @Override
    public void execute() {
        light.turnOff();
    }
}

```

- `LightOnCommand` and `LightOffCommand` are concrete implementations of the `Command` interface. They encapsulate actions to turn a light on and off, respectively.

##### Step 3: Define the Receiver

```java
public class Light {
    private String location;

    public Light(String location) {
        this.location = location;
    }

    public void turnOn() {
        System.out.println(location + " light is ON");
    }

    public void turnOff() {
        System.out.println(location + " light is OFF");
    }
}

```

- The `Light` class is the receiver of the request. It has methods to turn the light on and off.

##### Step 4: Define the Invoker

```java
public class RemoteControl {
    private Command command;

    public void setCommand(Command command) {
        this.command = command;
    }

    public void pressButton() {
        command.execute();
    }
}

```

- The `RemoteControl` class is the invoker. It invokes commands without knowing the specifics of what they do.

##### Step 5: Client Code

```java
public class CommandPatternExample {
    public static void main(String[] args) {
        Light livingRoomLight = new Light("Living Room");
        Light kitchenLight = new Light("Kitchen");

        Command livingRoomLightOn = new LightOnCommand(livingRoomLight);
        Command livingRoomLightOff = new LightOffCommand(livingRoomLight);
        Command kitchenLightOn = new LightOnCommand(kitchenLight);
        Command kitchenLightOff = new LightOffCommand(kitchenLight);

        RemoteControl remote = new RemoteControl();

        // Turn on the living room light
        remote.setCommand(livingRoomLightOn);
        remote.pressButton();

        // Turn off the living room light
        remote.setCommand(livingRoomLightOff);
        remote.pressButton();

        // Turn on the kitchen light
        remote.setCommand(kitchenLightOn);
        remote.pressButton();

        // Turn off the kitchen light
        remote.setCommand(kitchenLightOff);
        remote.pressButton();
    }
}

```

