# Key Principles of Object-Oriented Programming (OOP)

## [Encapsulation](Encapsulation.md)
Encapsulation in Object-Oriented Programming (OOP) refers to the bundling of data and methods within a class, which serves to protect the data integrity and control access to it. By encapsulating data and methods together, OOP ensures that the internal workings of an object are hidden from outside interference, thus promoting code security, reliability, and maintainability.

## [Inheritance](Inheritance.md)
Inheritance is a fundamental principle of OOP that involves creating new classes (subclasses) that inherit properties and behaviors from existing classes (superclasses). This promotes code reusability and specialization, as subclasses can extend and modify the functionality of their superclass while inheriting its common attributes and methods. Inheritance facilitates the creation of hierarchical class structures and supports the "is-a" relationship between classes.

## [Polymorphism](Polymorphism.md)
Polymorphism in OOP allows objects of different classes to respond to the same method call in different ways. This enhances flexibility and dynamic behavior within a program, as different objects can exhibit different behaviors based on their specific implementations of a common method. Polymorphism enables code to be written in a more generic and reusable manner, as it allows for the implementation of algorithms that can operate on objects of various types without needing to know their specific classes.

## [Abstraction](Abstraction.md)
Abstraction is the process of focusing on the essential functionalities of an object while hiding its implementation details. In OOP, abstraction simplifies code and promotes understanding by defining a clear interface for interacting with objects while hiding the complexities of their internal workings. By abstracting away unnecessary details, developers can create more modular, maintainable, and adaptable code that is easier to comprehend and work with.


## **Comparing and Contrasting Abstraction and Encapsulation**

While both abstraction and encapsulation are fundamental concepts in object-oriented programming (OOP), they serve distinct purposes:

**Abstraction:**

- **Focus:** Hides the implementation details of a concept, focusing on its essential functionalities and how it interacts with other parts of the system.
- **Goal:** Simplifies complex systems by providing a higher-level view, making them easier to understand and use.
- **Example:** Consider a car. We interact with it through the steering wheel, pedals, and other controls, without needing to know the intricate mechanics of the engine, brakes, and other internal components.

**Encapsulation:**

- **Focus:** Bundles data (attributes) and the operations (methods) that act on that data into a single unit called a class.
- **Goal:** Protects data integrity by controlling access and ensuring that data is manipulated only through authorized methods.
- **Example:** A bank account class encapsulates the account balance (data) and methods for deposit, withdrawal, and balance inquiry. This ensures that the balance is only modified through these controlled methods, preventing unauthorized access or manipulation.
