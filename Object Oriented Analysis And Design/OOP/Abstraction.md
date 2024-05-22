a) **Define the term Abstraction with a suitable non-computing example.** (4 Marks)

Abstraction is the fundamental concept of focusing on essential details while hiding irrelevant or complex ones. It's a crucial aspect of simplifying complex systems and making them easier to understand and manage.

**Non-computing example:**

**Recipe:** A recipe provides the key steps and ingredients for preparing a dish without delving into the intricate chemical reactions or physical processes involved in cooking. It abstracts away the underlying complexity, allowing users to focus on the desired outcome (the cooked dish).

b) **Explain why in Java, a method cannot be defined with a 'final abstract' combination.** (2 Marks)

In Java, the final and abstract keywords have distinct purposes that cannot be combined in a method declaration:

- **final:** Makes a method non-overridable by subclasses. It ensures consistency and prevents unintended modifications.
- **abstract:** Declares a method without implementation, forcing subclasses to provide their own concrete implementations. It promotes polymorphism and flexibility.

Combining these keywords would create a contradiction:

- A final method cannot be overridden, so there's no need for a subclass to provide an implementation.
- An abstract method requires a subclass to implement it, but the final keyword would prevent that.

Therefore, Java disallows the final abstract combination to maintain consistency and avoid logical conflicts.
