### Where to Use

Use the Flyweight Pattern in the following scenarios:

- When you need to create a large number of similar objects and memory usage is a concern.
- When the majority of the object state can be extrinsic (context-dependent) and shared among multiple objects.
- When the application can benefit from reduced memory consumption and improved performance by sharing common parts of objects.

### Code Explanation

#### Flyweight Pattern Implementation

##### Step 1: Identify Intrinsic and Extrinsic State

Intrinsic state: The state that is shared among multiple objects and can be considered immutable. Extrinsic state: The state that varies between individual objects and cannot be shared.

##### Step 2: Define the Flyweight Interface


```java
// Flyweight interface
public interface CoffeeOrder {
    void serveCoffee(CoffeeOrderContext context);
}

```

- The `CoffeeFlavor` class represents a specific coffee flavor and implements the `CoffeeOrder` interface.
- The `CoffeeOrder` interface defines the method for serving coffee, which includes the context information.

##### Step 3: Implement the Concrete Flyweight

```java
// Concrete flyweight
public class CoffeeFlavor implements CoffeeOrder {
    private final String flavor;

    public CoffeeFlavor(String flavor) {
        this.flavor = flavor;
    }

    @Override
    public void serveCoffee(CoffeeOrderContext context) {
        System.out.println("Serving coffee flavor '" + flavor + "' to table number " + context.getTableNumber());
    }
}

```
##### Step 4: Implement the Flyweight Factory

```java
import java.util.HashMap;
import java.util.Map;

// Flyweight factory
public class CoffeeFlavorFactory {
    private Map<String, CoffeeFlavor> flavors = new HashMap<>();

    public CoffeeOrder getCoffeeFlavor(String flavorName) {
        CoffeeFlavor flavor = flavors.get(flavorName);
        if (flavor == null) {
            flavor = new CoffeeFlavor(flavorName);
            flavors.put(flavorName, flavor);
        }
        return flavor;
    }

    public int getTotalCoffeeFlavorsMade() {
        return flavors.size();
    }
}

```

- The `CoffeeFlavorFactory` class is responsible for creating and managing flyweight objects (coffee flavors).

#### Step 5: Client Code

```java
public class FlyweightPatternExample {
    public static void main(String[] args) {
        CoffeeFlavorFactory coffeeFlavorFactory = new CoffeeFlavorFactory();

        // Order coffee flavors
        CoffeeOrder order1 = coffeeFlavorFactory.getCoffeeFlavor("Cappuccino");
        order1.serveCoffee(new CoffeeOrderContext(1));

        CoffeeOrder order2 = coffeeFlavorFactory.getCoffeeFlavor("Espresso");
        order2.serveCoffee(new CoffeeOrderContext(2));

        CoffeeOrder order3 = coffeeFlavorFactory.getCoffeeFlavor("Cappuccino");
        order3.serveCoffee(new CoffeeOrderContext(3));

        // Output total coffee flavors made
        System.out.println("Total coffee flavors made: " + coffeeFlavorFactory.getTotalCoffeeFlavorsMade());
    }
}

```

### Real World Example

Consider a text editor application where each character in a document is represented by a flyweight object. The intrinsic state of each character (such as font size, style, and color) can be shared among multiple characters, while the extrinsic state (position in the document) is unique to each character.

### Summary

The Flyweight Pattern is used to minimize memory usage or computational expenses by sharing as much as possible with similar objects. It's particularly effective when dealing with a large number of objects that have overlapping state and can benefit from sharing common parts. This pattern helps in improving performance and reducing memory consumption in applications with large-scale object creation requirements.