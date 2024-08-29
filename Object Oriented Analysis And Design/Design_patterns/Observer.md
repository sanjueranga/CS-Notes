#### Where to Use

Use the Observer Pattern in the following scenarios:

- When changes to one object need to be communicated to other objects without making the objects tightly coupled.
- When an abstraction has two aspects, one dependent on the other. Encapsulating these aspects in separate objects lets you vary and reuse them independently.
- When a change to one object requires changing others, and you don't know how many objects need to be changed.
- When an object should be able to notify other objects without knowing who these objects are.


## Introduction

The Observer Pattern is a behavioral design pattern that defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically. This pattern is useful for implementing distributed event handling systems.


## Code Explanation

### Observer Pattern Implementation: YouTube Channel Example

#### Step 1: Define the Subject Interface

```java
import java.util.ArrayList;
import java.util.List;

public interface Subject {
    void registerObserver(Observer observer);
    void removeObserver(Observer observer);
    void notifyObservers();
}


```

- The `Subject` interface declares methods to register, remove, and notify observers.

#### Step 2: Implement the Concrete Subject

```java
public class YouTubeChannel implements Subject {
    private List<Observer> subscribers;
    private String channelName;
    private String latestVideo;

    public YouTubeChannel(String channelName) {
        this.channelName = channelName;
        this.subscribers = new ArrayList<>();
    }

    public String getChannelName() {
        return channelName;
    }

    public String getLatestVideo() {
        return latestVideo;
    }

    public void uploadVideo(String videoTitle) {
        this.latestVideo = videoTitle;
        notifyObservers();
    }

    @Override
    public void registerObserver(Observer observer) {
        subscribers.add(observer);
    }

    @Override
    public void removeObserver(Observer observer) {
        subscribers.remove(observer);
    }

    @Override
    public void notifyObservers() {
        for (Observer subscriber : subscribers) {
            subscriber.update();
        }
    }
}

```

- `YouTubeChannel` maintains a list of subscribers and implements the methods to manage them. It also has a `latestVideo` that triggers notifications when a new video is uploaded.

#### Step 3: Define the Observer Interface

```java
public interface Observer {
    void update();
}

```

- The `Observer` interface declares the `update()` method that subjects call to notify observers of a change.

#### Step 4: Implement the Concrete Observer

```java
public class Subscriber implements Observer {
    private String name;
    private YouTubeChannel channel;

    public Subscriber(String name, YouTubeChannel channel) {
        this.name = name;
        this.channel = channel;
    }

    @Override
    public void update() {
        System.out.println("Hey " + name + ", " + channel.getChannelName() + " has uploaded a new video: " + channel.getLatestVideo());
    }
}

```

- `Subscriber` implements the `Observer` interface and reacts to updates from the `YouTubeChannel`.

#### Step 5: Client Cod


```java
public class YouTubeNotificationSystem {
    public static void main(String[] args) {
        // Create a YouTube channel
        YouTubeChannel myChannel = new YouTubeChannel("Tech World");

        // Create subscribers
        Subscriber subscriber1 = new Subscriber("Alice", myChannel);
        Subscriber subscriber2 = new Subscriber("Bob", myChannel);

        // Register subscribers to the channel
        myChannel.registerObserver(subscriber1);
        myChannel.registerObserver(subscriber2);

        // Upload a new video
        myChannel.uploadVideo("Observer Pattern Tutorial");

        // Another subscriber joins
        Subscriber subscriber3 = new Subscriber("Charlie", myChannel);
        myChannel.registerObserver(subscriber3);

        // Upload another video
        myChannel.uploadVideo("Singleton Pattern Tutorial");
    }
}

```

```java
// Subject interface
public interface YouTubeChannel {
    void registerSubscriber(Subscriber subscriber);
    void removeSubscriber(Subscriber subscriber);
    void notifySubscribers();
}

// Concrete Subject
public class YouTubeChannelImpl implements YouTubeChannel {
    private List<Subscriber> subscribers;
    private String channelName;
    private String latestVideo;

    public YouTubeChannelImpl(String channelName) {
        this.channelName = channelName;
        this.subscribers = new ArrayList<>();
    }

    public void uploadVideo(String videoTitle) {
        this.latestVideo = videoTitle;
        notifySubscribers();
    }

    @Override
    public void registerSubscriber(Subscriber subscriber) {
        subscribers.add(subscriber);
    }

    @Override
    public void removeSubscriber(Subscriber subscriber) {
        subscribers.remove(subscriber);
    }

    @Override
    public void notifySubscribers() {
        for (Subscriber subscriber : subscribers) {
            subscriber.update(latestVideo);
        }
    }
}

// Observer interface
public interface Subscriber {
    void update(String videoTitle);
}

// Concrete Observer
public class YouTubeSubscriber implements Subscriber {
    private String name;

    public YouTubeSubscriber(String name) {
        this.name = name;
    }

    @Override
    public void update(String videoTitle) {
        System.out.println(name + " has been notified of a new video: " + videoTitle);
    }
}

// Client code
public class YouTubeChannelExample {
    public static void main(String[] args) {
        YouTubeChannelImpl techChannel = new YouTubeChannelImpl("Tech World");

        Subscriber alice = new YouTubeSubscriber("Alice");
        Subscriber bob = new YouTubeSubscriber("Bob");

        techChannel.registerSubscriber(alice);
        techChannel.registerSubscriber(bob);

        techChannel.uploadVideo("Observer Pattern Tutorial");

        Subscriber charlie = new YouTubeSubscriber("Charlie");
        techChannel.registerSubscriber(charlie);

        techChannel.uploadVideo("Singleton Pattern Tutorial");
    }
}

```