
## Introduction

The Prototype Pattern is a creational design pattern that allows cloning objects, even complex ones, without coupling to their specific classes. This pattern is used when the type of object to create is determined by a prototypical instance, which is cloned to produce new objects. It provides a way to copy original objects and create new objects without knowing their exact details.

## Where to Use

Use the Prototype Pattern in the following scenarios:

- When creating an object is costly (in terms of time or resources), and you want to avoid the overhead of creation from scratch.
- When an object should be independent of how its clone is created.
- When you need to create a large number of objects, or a combination of objects, that are similar but not exact copies.
- When the object structures are complex and involve many references to other objects.

## Code Explanation

### Prototype Pattern Implementation

#### Step 1: Define the Prototype Interface

```java
// Prototype interface
public interface Prototype {
    Prototype clone();
}
```


- `Prototype` defines a method for cloning itself.

```java
// Concrete Prototype for a specific type of object
public class ConcretePrototype implements Prototype {
    private String attribute;

    public ConcretePrototype(String attribute) {
        this.attribute = attribute;
    }

    public void setAttribute(String attribute) {
        this.attribute = attribute;
    }

    public String getAttribute() {
        return attribute;
    }

    @Override
    public Prototype clone() {
        return new ConcretePrototype(this.attribute);
    }

    @Override
    public String toString() {
        return "ConcretePrototype [attribute=" + attribute + "]";
    }
}

```

- `ConcretePrototype` implements the `Prototype` interface, providing a method to clone itself.

#### Step 3: Client Code

```java
public class PrototypePatternExample {
    public static void main(String[] args) {
        // Create an original object
        ConcretePrototype original = new ConcretePrototype("Original");
        System.out.println("Original: " + original);

        // Clone the original object
        ConcretePrototype clone = (ConcretePrototype) original.clone();
        System.out.println("Clone: " + clone);

        // Modify the clone
        clone.setAttribute("Modified Clone");
        System.out.println("Modified Clone: " + clone);

        // Original object remains unchanged
        System.out.println("Original after clone modification: " + original);
    }
}

```

## Real World Example

Consider a scenario where you are developing a game and you need to create various types of enemies with similar properties but different behaviors. Using the Prototype Pattern, you can clone enemy objects instead of creating them from scratch each time.


```java
// Prototype interface
public interface EnemyPrototype {
    EnemyPrototype clone();
    void attack();
}

// Concrete Prototype for a specific type of enemy
public class Orc implements EnemyPrototype {
    private String weapon;

    public Orc(String weapon) {
        this.weapon = weapon;
    }

    public void setWeapon(String weapon) {
        this.weapon = weapon;
    }

    public String getWeapon() {
        return weapon;
    }

    @Override
    public EnemyPrototype clone() {
        return new Orc(this.weapon);
    }

    @Override
    public void attack() {
        System.out.println("Orc attacks with " + weapon);
    }

    @Override
    public String toString() {
        return "Orc [weapon=" + weapon + "]";
    }
}

// Client code
public class Game {
    public static void main(String[] args) {
        // Create an original Orc
        Orc originalOrc = new Orc("Axe");
        originalOrc.attack();

        // Clone the original Orc
        Orc clonedOrc = (Orc) originalOrc.clone();
        clonedOrc.attack();

        // Modify the clone
        clonedOrc.setWeapon("Sword");
        clonedOrc.attack();

        // Original Orc remains unchanged
        originalOrc.attack();
    }
}

```

In this example, the Prototype Pattern is used to clone enemy objects, allowing for efficient creation of multiple similar enemies with different configurations. This helps in managing game resources and ensuring consistent behavior across different enemy instances.