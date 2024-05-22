### Where to Use

Use the Strategy Pattern in the following scenarios:

- When you have multiple algorithms for a specific task and you want to choose the algorithm at runtime.
- When you want to avoid conditional statements for selecting different behaviors.
- When you have multiple related classes that differ only in their behavior.
- When you need different variations of an algorithm, encapsulated and interchangeable.

### Code Explanation

#### Strategy Pattern Implementation

##### Step 1: Define the Strategy Interface

```java
public interface PaymentStrategy {
    void pay(int amount);
}

```

- The `PaymentStrategy` interface declares a method `pay` that different payment methods will implement.

##### Step 2: Implement Concrete Strategies

```java
// Concrete Strategy for credit card payment
public class CreditCardPayment implements PaymentStrategy {
    private String cardNumber;
    private String name;
    private String cvv;
    private String dateOfExpiry;

    public CreditCardPayment(String cardNumber, String name, String cvv, String dateOfExpiry) {
        this.cardNumber = cardNumber;
        this.name = name;
        this.cvv = cvv;
        this.dateOfExpiry = dateOfExpiry;
    }

    @Override
    public void pay(int amount) {
        System.out.println(amount + " paid with credit card.");
    }
}

// Concrete Strategy for PayPal payment
public class PayPalPayment implements PaymentStrategy {
    private String emailId;
    private String password;

    public PayPalPayment(String emailId, String password) {
        this.emailId = emailId;
        this.password = password;
    }

    @Override
    public void pay(int amount) {
        System.out.println(amount + " paid using PayPal.");
    }
}

```

- `CreditCardPayment` and `PayPalPayment` are concrete implementations of the `PaymentStrategy` interface, each providing a different payment method.

##### Step 3: Define the Context


```java
public class ShoppingCart {
    private List<Item> items;
    private PaymentStrategy paymentStrategy;

    public ShoppingCart() {
        this.items = new ArrayList<>();
    }

    public void addItem(Item item) {
        items.add(item);
    }

    public void removeItem(Item item) {
        items.remove(item);
    }

    public int calculateTotal() {
        int sum = 0;
        for (Item item : items) {
            sum += item.getPrice();
        }
        return sum;
    }

    public void setPaymentStrategy(PaymentStrategy paymentStrategy) {
        this.paymentStrategy = paymentStrategy;
    }

    public void pay() {
        int amount = calculateTotal();
        paymentStrategy.pay(amount);
    }
}

```

- `ShoppingCart` is the context class that uses a `PaymentStrategy` to make payments. It can change its payment strategy at runtime.

##### Step 4: Client Code

```java
public class StrategyPatternExample {
    public static void main(String[] args) {
        ShoppingCart cart = new ShoppingCart();

        Item item1 = new Item("1234", 10);
        Item item2 = new Item("5678", 40);

        cart.addItem(item1);
        cart.addItem(item2);

        // Pay using credit card
        cart.setPaymentStrategy(new CreditCardPayment("1234567890123456", "John Doe", "123", "12/23"));
        cart.pay();

        // Pay using PayPal
        cart.setPaymentStrategy(new PayPalPayment("john.doe@example.com", "password"));
        cart.pay();
    }
}

```

