# Associational (Usage) Relationships

Associational relationships in UML diagrams define how classes interact and collaborate with each other. They are characterized by several key attributes:

1. **Multiplicity:**
   - Describes how many instances of one class are associated with instances of another class.
   - Notation:
     - `*`: Zero or more instances.
     - `1`: Exactly one instance.
     - `2..4`: Between 2 and 4 instances, inclusive.
     - `3..*`: Three or more instances.
   - Indicates the cardinality or quantity of objects involved in the relationship.

2. **Name:**
   - Specifies the name of the association, providing context and clarity to the relationship.

3. **Navigability:**
   - Determines the direction in which objects participate in the relationship.
   - Notation:
     - `-`: Bidirectional navigability (objects at both ends can navigate to each other).
     - `>`: Unidirectional navigability (navigation allowed from one end to the other).
     - `<`: Reverse unidirectional navigability (navigation allowed in the opposite direction).
     - `<>`: Bi-directional navigability (navigation allowed in both directions).

Associational relationships help in modeling the connections and interactions between classes, facilitating a better understanding of the system's structure and behavior.



# Types of Associational Relationships

Associational relationships in UML diagrams define how classes interact and collaborate with each other. They can be categorized into several types based on the nature of the relationship:

## One-to-One Relationship
- **Description:** Each instance of one class is associated with exactly one instance of another class.
- **Example:** Each student must carry exactly one ID card.

## One-to-Many Relationship
- **Description:** Each instance of one class is associated with multiple instances of another class.
- **Example:** One rectangle list can contain many rectangles.

## Aggregation Relationship
- **Description:** Represents a "is part of" relationship, where one class contains objects of another class as part of its state.
- **Symbol:** Clear white diamond.

## Composition Relationship
- **Description:** A stronger version of aggregation where the parts live and die with the whole.
- **Symbol:** Black diamond.

## Dependency Relationship
- **Description:** Indicates that one class depends on another class, often temporarily.
- **Symbol:** Dotted line.
- **Usage:** Dependency relationships are often implementation details rather than intrinsic parts of an object's state.

These different types of associational relationships help in modeling complex interactions and dependencies between classes in a software system.
