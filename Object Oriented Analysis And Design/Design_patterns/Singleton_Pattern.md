
## Introduction

The Singleton Pattern is a creational design pattern that ensures a class has only one instance and provides a global point of access to that instance. It is used to control object creation, limiting the number of instances to one. This is useful when exactly one object is needed to coordinate actions across a system.

## Where to Use

Use the Singleton Pattern in the following scenarios:

- When exactly one instance of a class is required to control some operations.
- When the single instance should be accessible by multiple parts of the system.
- When controlling the access to some shared resource, such as a database or file, to prevent concurrent access issues.
- When you want to encapsulate the sole instance and provide controlled access.

## Code Explanation

### Singleton Pattern Implementation

#### Step 1: Define the Singleton Class

```java
public class Singleton {
    // Private static variable of the single instance
    private static Singleton instance;

    // Private constructor to prevent instantiation from other classes
    private Singleton() {
        // Initialization code here
    }

    // Public method to provide access to the instance
    public static Singleton getInstance() {
        if (instance == null) {
            synchronized (Singleton.class) {
                if (instance == null) {
                    instance = new Singleton();
                }
            }
        }
        return instance;
    }

    // Example method to demonstrate Singleton usage
    public void showMessage() {
        System.out.println("Hello, I am a Singleton!");
    }
}


```

- `Singleton` class has a private static variable `instance` to hold the single instance.
- The constructor is private to prevent direct instantiation.
- `getInstance()` method provides a global point of access to the single instance, with double-checked locking to ensure thread safety.

#### Step 2: Client Code

```java
public class SingletonPatternExample {
    public static void main(String[] args) {
        // Get the only object available
        Singleton singleton = Singleton.getInstance();

        // Show the message
        singleton.showMessage();
    }
}

```

## Real World Example

Consider a logging system where a single instance of a logger is needed to log messages from different parts of an application. Using the Singleton Pattern ensures that all components use the same logger instance.


```java
// Logger class using Singleton Pattern
public class Logger {
    // Private static variable of the single instance
    private static Logger instance;

    // Private constructor to prevent instantiation
    private Logger() {
        // Initialization code here
    }

    // Public method to provide access to the instance
    public static Logger getInstance() {
        if (instance == null) {
            synchronized (Logger.class) {
                if (instance == null) {
                    instance = new Logger();
                }
            }
        }
        return instance;
    }

    // Method to log messages
    public void log(String message) {
        System.out.println("Log: " + message);
    }
}

// Client code
public class Application {
    public static void main(String[] args) {
        // Get the logger instance
        Logger logger = Logger.getInstance();

        // Log messages
        logger.log("Application started");
        logger.log("Application running");
        logger.log("Application stopped");
    }
}

```

