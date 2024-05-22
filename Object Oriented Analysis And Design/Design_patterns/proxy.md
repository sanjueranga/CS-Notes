### Where to Use

Use the Proxy Pattern in the following scenarios:

- **Remote Proxy**: When you want to represent an object that is located remotely.
- **Virtual Proxy**: When you want to create a placeholder for an expensive-to-create object.
- **Protection Proxy**: When you want to control access to an object based on permissions or security checks.
- **Smart Reference Proxy**: When you want to add extra functionality to the accessed object, such as caching or logging.

### Code Explanation

#### Proxy Pattern Implementation

##### Step 1: Define the Subject Interface

```java
// Subject interface
public interface Image {
    void display();
}

```
- The `Image` interface declares the common interface for both the RealSubject and Proxy.

##### Step 2: Implement the RealSubject

```java
// RealSubject
public class RealImage implements Image {
    private String fileName;

    public RealImage(String fileName) {
        this.fileName = fileName;
        loadFromDisk();
    }

    private void loadFromDisk() {
        System.out.println("Loading image: " + fileName);
    }

    @Override
    public void display() {
        System.out.println("Displaying image: " + fileName);
    }
}

```

- The `RealImage` class represents the actual object that the Proxy is meant to control access to.

##### Step 3: Implement the Proxy

```java
// Proxy
public class ProxyImage implements Image {
    private RealImage realImage;
    private String fileName;

    public ProxyImage(String fileName) {
        this.fileName = fileName;
    }

    @Override
    public void display() {
        if (realImage == null) {
            realImage = new RealImage(fileName);
        }
        realImage.display();
    }
}

```

- The `ProxyImage` class acts as a proxy to control access to the `RealImage`. It creates the `RealImage` object only when necessary and delegates the `display()` method call to the `RealImage`.

#### Step 4: Client Code

```java
public class ProxyPatternExample {
    public static void main(String[] args) {
        Image image1 = new ProxyImage("image1.jpg");
        Image image2 = new ProxyImage("image2.jpg");

        // Image 1 will be loaded from disk
        image1.display();

        // Image 2 will be loaded from disk only when needed
        image2.display();
    }
}

```

