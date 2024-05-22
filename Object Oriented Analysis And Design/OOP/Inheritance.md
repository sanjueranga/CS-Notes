# Five Types of Inheritance in OOP

Inheritance is a powerful OOP mechanism that allows new classes (subclasses) to inherit properties and behaviors from existing classes (superclasses). Here's an overview of the five main types of inheritance:

1. **Single Inheritance:**
   - A subclass inherits from one superclass.
   - **Example:** A `Dog` class inherits from an `Animal` class, inheriting general animal attributes and behaviors while adding dog-specific characteristics.

2. **Multilevel Inheritance:**
   - A subclass inherits from another subclass, which in turn inherits from a superclass, forming a chain of inheritance.
   - **Example:** A `GuardDog` class inherits from a `Dog` class, which inherits from an `Animal` class, gaining attributes and behaviors from all levels in the hierarchy.

3. **Hierarchical Inheritance:**
   - Multiple subclasses inherit from a single superclass.
   - **Example:** A `Vehicle` class can have subclasses like `Car`, `Truck`, and `Bicycle`, each inheriting common vehicle attributes while specializing in their own functionalities.

4. **Multiple Inheritance:**
   - A subclass inherits from multiple superclasses, directly combining their properties and behaviors.
   - Java does not directly support multiple inheritance due to potential ambiguity issues, but it can be simulated using interfaces.
   - **Example:** In languages that support it, a `FlyingCar` class could inherit from both `Car` and `Airplane` classes, combining functionalities of both.

5. **Interface Inheritance:**
   - Interfaces can inherit from other interfaces, allowing for extending and specializing their functionalities.
   - **Example:** A `Drawable` interface might inherit from a `Printable` interface, adding drawing capabilities to the printing functionality.

