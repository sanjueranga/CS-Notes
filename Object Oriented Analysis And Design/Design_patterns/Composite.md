### Where to Use

Use the Composite Pattern in the following scenarios:

- When you need to represent part-whole hierarchies of objects.
- When you want clients to treat individual objects and compositions of objects uniformly.
- When you want to simplify the client code by removing the need for explicit checks for leaf or node objects.

### Code Explanation

#### Composite Pattern Implementation

##### Step 1: Define the Component Interface

```java
public interface Component {
    void operation();
}

```

- The `Component` interface declares the common interface for both leaf and composite objects.

##### Step 2: Implement Leaf Component

```java
public class Leaf implements Component {
    @Override
    public void operation() {
        System.out.println("Leaf operation");
    }
}

```

- `Leaf` represents leaf objects in the composition. It implements the `Component` interface.

##### Step 3: Implement Composite Component

```java
import java.util.ArrayList;
import java.util.List;

public class Composite implements Component {
    private List<Component> children = new ArrayList<>();

    public void add(Component component) {
        children.add(component);
    }

    public void remove(Component component) {
        children.remove(component);
    }

    @Override
    public void operation() {
        for (Component component : children) {
            component.operation();
        }
    }
}

```

- `Composite` represents composite objects that can have children. It also implements the `Component` interface.

##### Step 4: Client Code


```java
public class CompositePatternExample {
    public static void main(String[] args) {
        Leaf leaf1 = new Leaf();
        Leaf leaf2 = new Leaf();
        Leaf leaf3 = new Leaf();

        Composite composite1 = new Composite();
        composite1.add(leaf1);
        composite1.add(leaf2);

        Composite composite2 = new Composite();
        composite2.add(leaf3);

        Composite composite = new Composite();
        composite.add(composite1);
        composite.add(composite2);

        composite.operation();
    }
}

```

### Real World Example

Consider a file system where directories can contain files or other directories. The Composite Pattern can be used to represent the file system structure.

```java
// Component interface
public interface FileSystemComponent {
    void display();
}

// Leaf component
public class File implements FileSystemComponent {
    private String name;

    public File(String name) {
        this.name = name;
    }

    @Override
    public void display() {
        System.out.println("File: " + name);
    }
}

// Composite component
import java.util.ArrayList;
import java.util.List;

public class Directory implements FileSystemComponent {
    private String name;
    private List<FileSystemComponent> components = new ArrayList<>();

    public Directory(String name) {
        this.name = name;
    }

    public void add(FileSystemComponent component) {
        components.add(component);
    }

    public void remove(FileSystemComponent component) {
        components.remove(component);
    }

    @Override
    public void display() {
        System.out.println("Directory: " + name);
        for (FileSystemComponent component : components) {
            component.display();
        }
    }
}

// Client code
public class FileSystem {
    public static void main(String[] args) {
        File file1 = new File("File1.txt");
        File file2 = new File("File2.txt");

        Directory subDirectory = new Directory("Sub Directory");
        subDirectory.add(file1);
        subDirectory.add(file2);

        Directory mainDirectory = new Directory("Main Directory");
        mainDirectory.add(subDirectory);

        mainDirectory.display();
    }
}

```

In this example, `File` represents leaf objects (files), and `Directory` represents composite objects (directories). The `FileSystem` class demonstrates how files and directories can be structured using the Composite Pattern.
