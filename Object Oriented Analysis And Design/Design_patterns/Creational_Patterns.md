
### [Factory Pattern](Factory_Pattern.md)

The Factory pattern provides a way to use an instance as a object factory.
The factory can return an instance of one of several possible classes (in a
subclass hierarchy), depending on the data provided to it.

###### Where to use

- When a class can't anticipate which kind of class of object it must create.
- You want to localize the knowledge of which class gets created.
- When you have classes that is derived from the same subclasses, or they
	may in fact be unrelated classes that just share the same interface. Either
	way, the methods in these class instances are the same and can be used
	interchangeably.
- When you want to insulate the client from the actual type that is being
	instantiated.

### [Abstract Factory Pattern](Abstract_Factory_Pattern.md) 

The Abstract Factory pattern is a creational pattern which is related to the
Factory Method pattern, but it adds another level of abstraction. What this
means is that the pattern encapsulates a group of individual concrete factory
classes (as opposed to concrete factory methods which are derived in
subclasses) which share common interfaces. The client software uses the
Abstract Factory which provides an interface for creating families of related
or dependent objects without specifying their concrete classes. This pattern
separates the implementation details of a set of objects from its general
usage.

### [Builder Pattern](Builder_Pattern.md)

The Builder pattern can be used to ease the construction of a complex object
from simple objects. The Builder pattern also separates the construction of a
complex object from its representation so that the same construction process
can be used to create another composition of objects.
Related patterns include Abstract Factory and Composite.

### [Prototype Pattern](Prototype_Pattern.md)

The Prototype pattern is basically the creation of new instances through
cloning existing instances. By creating a prototype, new objects are created
by copying this prototype.


### [Singleton Pattern](Singleton_Pattern.md)

The Singleton pattern provides the possibility to control the number of
instances (mostly one) that are allowed to be made. We also receive a global
point of access to it (them).
