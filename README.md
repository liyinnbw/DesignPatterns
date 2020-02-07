# Design Patterns
Notes on design patterns for future reference

## Creational
### Abstract factory
### Builder
### Factory method
### Prototype
### Singleton
Gist:
* Static class to get one and only one instance.
<img src="https://upload.wikimedia.org/wikipedia/commons/f/fb/Singleton_UML_class_diagram.svg" alt="UML Illustration" width="400">

Use cases:
* When you do not want to pass a popular object reference everywhere

## Structural
### Adapter
Gist:
* Basically a wrapper to existing class to adapt to new interface (rewrite method names, parameters, return types ...)
* Can either be adaptor to an object (pass the object as reference to adaptor) or adaptor to a class (subclassing)

Use cases:
* New interface
* Alternative interfaces

### Bridge*
Gist:
* Instead of subclassing abstract class into implementor class, let abstract class hold reference to abstract implementor so that both can be independently subclassed and implemented
* Decouples abstraction from implementation
  * Abstraction (abstract class)
    * defines the abstract interface
    * maintains the Implementor reference
  * RefinedAbstraction (normal class)
    * extends the interface defined by Abstraction
  * Implementor (interface)
    * defines the interface for implementation classes
  * ConcreteImplementor (normal class)
    * implements the Implementor interface
<img src="https://upload.wikimedia.org/wikipedia/commons/c/cf/Bridge_UML_class_diagram.svg" alt="UML Illustration" width="400">

Use cases:
* When both the class and what it does can be modified very often

Down side:
* You will need at least 4 separate files to do something that could be done by 1 class...

### Composite
* The essence is to use a common interface for both component and composite
* Composite hold references to each component
* Composite distribute client call to each component methods
<img src="https://upload.wikimedia.org/wikipedia/commons/5/5a/Composite_UML_class_diagram_%28fixed%29.svg" alt="UML Illustration" width="400">

Use cases:
* Unify client-facing interface for composite and component operations

### Decorator
Gist:
* A way of extending object functionality
* Structurally the same as [chain of responsibility](#chain-of-responsibility) 
* Subclass base class
* Receive base class object reference at constructor and save as private property
* Use base class object reference to call base class methods
* Extend base class functionality by implementing new methods
* Decorator can subclass decorator
<img src="https://upload.wikimedia.org/wikipedia/commons/e/e9/Decorator_UML_class_diagram.svg" alt="UML Illustration" width="400">

Use cases:
* When you do not want to create multiple subclasses just to add new functionalities
* When you want to add functionalities at run time to some object instances but not all

### Facade

### Flyweight
### Proxy provides

## Behavioral
### Chain of responsibility
Gist:
* Structurally the same as [decorator](#decorator)
* Except exactly one of the classes in the chain handles the request, unlike decorator, where all classes handle the request
* Decouples request sender and request handlers

Use cases:
* When you need a chain of receivers to either handle or pass to next receiver at run time

### Command
### Interpreter
### Iterator
### Mediator
### Memento
### Observer
Gist:
* Object being observed register/unregister observers in a private list
* Object notifies registered observers when there is a state change
* Observers then inform other relevant objects about the state change event
* Decouples the observed object from the other objects
<img src="https://upload.wikimedia.org/wikipedia/commons/a/a8/Observer_w_update.svg" alt="UML Illustration" width="400">

Use cases:
* Observer as the middle man of message/event passing
* MVC pattern where observer is the controller

### State
### Strategy
### Template method
### Visitor

