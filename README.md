# Design Patterns
Notes on design patterns for future reference

# Creational
## Abstract factory
## Builder
## Factory method
## Prototype
## Singleton
Gist:
* Static class to get one and only one instance.
<img src="https://upload.wikimedia.org/wikipedia/commons/f/fb/Singleton_UML_class_diagram.svg" alt="UML Illustration" width="400">

Use cases:
* When you do not want to pass a popular object reference everywhere

# Structural
## Adapter
Gist:
* Basically a wrapper to existing class to adapt to new interface (rewrite method names, parameters, return types ...)
* Can either be adaptor to an object (pass the object as reference to adaptor) or adaptor to a class (subclassing)

Use cases:
* New interface
* Alternative interfaces

## Bridge*
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

## Composite
* The essence is to use a common interface for both component and composite
* Composite hold references to each component
* Composite distribute client call to each component methods
<img src="https://upload.wikimedia.org/wikipedia/commons/5/5a/Composite_UML_class_diagram_%28fixed%29.svg" alt="UML Illustration" width="400">

Use cases:
* Unify client-facing interface for composite and component operations

## Decorator
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

## Facade
Gist:
* A simplified API for complex underlying code structure

## Flyweight
Gist:
* Reduce memory usage by sharing common state/data as much as possible

## Proxy
Gist
* A light-weight substitute to another more heavy-weight object
* The proxy and real object share the common interface
* The proxy holds a private reference to the real object
* The proxy can add additional logic to control access to the real object
<img src="https://upload.wikimedia.org/wikipedia/commons/7/75/Proxy_pattern_diagram.svg" alt="UML Illustration" width="400">

Use cases:
* When the real object is complex
* More often, when access to the real object needs to be controlled (some condition checks in proxy)


# Behavioral
## Chain of responsibility
Gist:
* Structurally the same as [decorator](#decorator)
* Except exactly one of the classes in the chain handles the request, unlike decorator, where all classes handle the request
* Decouples request sender and request handlers

Use cases:
* When you need a chain of receivers to either handle or pass to next receiver at run time

## Command (resembles functional programming)
Gist:
* A command object contains all information needed to execute the command at a later time (can be queued)
* 3 objects are involved to execute an action:
  * Invoker: issues a command, only know command interface, does not know the command receiver
  * Command: has reference to the receiver and all the parameters needed for the receiver to perform the action
  * Receiver: the target object which performs the actual action

Use cases:
* UI action, input replay, undo-redo, transaction, multi-page wizards

## Interpreter*
* Kind of a special case of [composite](#composite) pattern
* A sequence of interpreters completes a task 

## Iterator
* Should be self-explanatory

## Mediator
* A middle man that handles interaction between objects
* Objects calls mediator and pass themselves as parameter
* Mediator then handles the interaction for them 
<img src="https://upload.wikimedia.org/wikipedia/commons/9/92/W3sDesign_Mediator_Design_Pattern_UML.jpg" alt="UML Illustration" width="400">

## Memento
* A pattern to save state and restore state (undo)
<img src="https://upload.wikimedia.org/wikipedia/commons/3/38/W3sDesign_Memento_Design_Pattern_UML.jpg" alt="UML Illustration" width="400">

## Observer
Gist:
* Object being observed register/unregister observers in a private list
* Object notifies registered observers when there is a state change
* Observers then inform other relevant objects about the state change event
* Decouples the observed object from the other objects
<img src="https://upload.wikimedia.org/wikipedia/commons/a/a8/Observer_w_update.svg" alt="UML Illustration" width="400">

Use cases:
* Observer as the middle man of message/event passing
* MVC pattern where observer is the controller

## State
## Strategy
## Template method
## Visitor

