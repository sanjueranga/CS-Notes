### Code Explanation

#### Decorator Pattern Implementation

##### Step 1: Define the Component Interface

```java
// Component interface
public interface Pizza {
    String getDescription();
    double getCost();
}

```

- The `Pizza` interface defines the methods that all pizza classes must implement.

##### Step 2: Implement the Concrete Component

```java
// Concrete component
public class Margherita implements Pizza {
    @Override
    public String getDescription() {
        return "Margherita Pizza";
    }

    @Override
    public double getCost() {
        return 6.99;
    }
}

```

- The `Margherita` class is a concrete pizza component that implements the `Pizza` interface.

##### Step 3: Implement the Decorator

```java
// Decorator
public abstract class PizzaDecorator implements Pizza {
    protected Pizza pizza;

    public PizzaDecorator(Pizza pizza) {
        this.pizza = pizza;
    }

    @Override
    public String getDescription() {
        return pizza.getDescription();
    }

    @Override
    public double getCost() {
        return pizza.getCost();
    }
}

```

- The `PizzaDecorator` class is the base decorator class that implements the `Pizza` interface. It contains a reference to the wrapped `Pizza` object.

##### Step 4: Implement Concrete Decorators

```java
// Concrete decorator
public class ExtraCheeseDecorator extends PizzaDecorator {
    public ExtraCheeseDecorator(Pizza pizza) {
        super(pizza);
    }

    @Override
    public String getDescription() {
        return pizza.getDescription() + ", Extra Cheese";
    }

    @Override
    public double getCost() {
        return pizza.getCost() + 1.50;
    }
}

// Concrete decorator
public class PepperoniDecorator extends PizzaDecorator {
    public PepperoniDecorator(Pizza pizza) {
        super(pizza);
    }

    @Override
    public String getDescription() {
        return pizza.getDescription() + ", Pepperoni";
    }

    @Override
    public double getCost() {
        return pizza.getCost() + 2.00;
    }
}

```

- The `ExtraCheeseDecorator` and `PepperoniDecorator` classes are concrete decorators that add extra functionality (extra cheese and pepperoni) to the pizza.

#### Step 5: Client Code

```java
public class DecoratorPatternExample {
    public static void main(String[] args) {
        // Base pizza
        Pizza margherita = new Margherita();
        System.out.println("Base pizza: " + margherita.getDescription());
        System.out.println("Cost: $" + margherita.getCost());

        // Decorated pizzas
        Pizza extraCheesePizza = new ExtraCheeseDecorator(margherita);
        System.out.println("\nExtra Cheese pizza: " + extraCheesePizza.getDescription());
        System.out.println("Cost: $" + extraCheesePizza.getCost());

        Pizza pepperoniPizza = new PepperoniDecorator(margherita);
        System.out.println("\nPepperoni pizza: " + pepperoniPizza.getDescription());
        System.out.println("Cost: $" + pepperoniPizza.getCost());
    }
}

```

### Real World Example

Consider a text editor application where you can apply various formatting options (bold, italic, underline) to text. Instead of creating separate classes for each combination of formatting options, you can use the Decorator Pattern to dynamically add or remove formatting to the text.

### Summary

The Decorator Pattern allows behavior to be added to individual objects dynamically without affecting the behavior of other objects from the same class. It promotes flexibility and reusability by allowing classes to be easily extended with new functionality at runtime. This pattern is particularly useful when the behavior of an object needs to be modified or extended without altering its structure.