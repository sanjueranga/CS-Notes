### Where to Use

Use the Interpreter Pattern in the following scenarios:

- When you need to interpret a language, grammar, or expression, such as mathematical expressions, regular expressions, or parsed input.
- When you need a simple language or notation that can be parsed and evaluated.

### Code Explanation

#### Interpreter Pattern Implementation

##### Step 1: Define the Abstract Expression

```java
public interface Expression {
    boolean interpret(String context);
}
```

- The `Expression` interface declares an `interpret` method that will be implemented by all terminal and non-terminal expressions.

##### Step 2: Implement Terminal Expressions

```java
public class TerminalExpression implements Expression {
    private String data;

    public TerminalExpression(String data) {
        this.data = data;
    }

    @Override
    public boolean interpret(String context) {
        return context.contains(data);
    }
}

```

- `TerminalExpression` implements the `Expression` interface. It checks if the given context contains the data.

##### Step 3: Implement Non-terminal Expressions

```java
    @Override
    public boolean interpret(String context) {
        return expr1.interpret(context) || expr2.interpret(context);
    }
}

public class AndExpression implements Expression {
    private Expression expr1;
    private Expression expr2;

    public AndExpression(Expression expr1, Expression expr2) {
        this.expr1 = expr1;
        this.expr2 = expr2;
    }

    @Override
    public boolean interpret(String context) {
        return expr1.interpret(context) && expr2.interpret(context);
    }
}

```

- `OrExpression` and `AndExpression` are non-terminal expressions that combine multiple expressions using logical OR and AND operations, respectively.

##### Step 4: Client Code

```java
public class InterpreterPatternExample {
    // Rule: Robert and John are male
    public static Expression getMaleExpression() {
        Expression robert = new TerminalExpression("Robert");
        Expression john = new TerminalExpression("John");
        return new OrExpression(robert, john);
    }

    // Rule: Julie is a married woman
    public static Expression getMarriedWomanExpression() {
        Expression julie = new TerminalExpression("Julie");
        Expression married = new TerminalExpression("Married");
        return new AndExpression(julie, married);
    }

    public static void main(String[] args) {
        Expression isMale = getMaleExpression();
        Expression isMarriedWoman = getMarriedWomanExpression();

        System.out.println("John is male? " + isMale.interpret("John"));
        System.out.println("Julie is a married woman? " + isMarriedWoman.interpret("Married Julie"));
        System.out.println("Robert is a married man? " + isMarriedWoman.interpret("Married Robert"));
    }
}

```

```java
// Abstract Expression
public interface Expression {
    boolean interpret(String context);
}

// Terminal Expression for user role
public class RoleExpression implements Expression {
    private String role;

    public RoleExpression(String role) {
        this.role = role;
    }

    @Override
    public boolean interpret(String context) {
        return context.contains(role);
    }
}

// Non-terminal Expression for OR operation
public class OrExpression implements Expression {
    private Expression expr1;
    private Expression expr2;

    public OrExpression(Expression expr1, Expression expr2) {
        this.expr1 = expr1;
        this.expr2 = expr2;
    }

    @Override
    public boolean interpret(String context) {
        return expr1.interpret(context) || expr2.interpret(context);
    }
}

// Non-terminal Expression for AND operation
public class AndExpression implements Expression {
    private Expression expr1;
    private Expression expr2;

    public AndExpression(Expression expr1, Expression expr2) {
        this.expr1 = expr1;
        this.expr2 = expr2;
    }

    @Override
    public boolean interpret(String context) {
        return expr1.interpret(context) && expr2.interpret(context);
    }
}

// Client code
public class AccessControl {
    public static void main(String[] args) {
        Expression admin = new RoleExpression("ADMIN");
        Expression manager = new RoleExpression("MANAGER");
        Expression user = new RoleExpression("USER");

        Expression isAdminOrManager = new OrExpression(admin, manager);
        Expression isAdminAndManager = new AndExpression(admin, manager);

        System.out.println("Is ADMIN or MANAGER? " + isAdminOrManager.interpret("ADMIN"));
        System.out.println("Is ADMIN and MANAGER? " + isAdminAndManager.interpret("ADMIN MANAGER"));
        System.out.println("Is USER or ADMIN? " + new OrExpression(user, admin).interpret("USER"));
    }
}

```

In this example, the Interpreter Pattern is used to evaluate user roles dynamically based on the provided context. Different expressions are combined using logical operations to achieve complex access control rules.