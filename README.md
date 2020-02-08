# Design Patterns
Notes on design patterns for future reference.

Note that there are people criticising design patterns as a work-around to hide the defects of the language.

Personally feel the patterns can be grouped as:
* Modify by inheritance
  * [Factory Method](#factory-method) - creator method that can be modified by subclassing
  * [Template](#template) - single branch of inheritance
  * [Bridge](#bridge) - two separate branches of inheritance
* Repurposing by wrapping
  * [Adapter](#adapter) - change interface by wrapping one
  * [Facade](#facade) - simplify interface by wrapping many
  * [Proxy](#proxy) - control access by wrapping one
* Middle man
  * [Mediator](#mediator) - single point of contact for objects interaction
  * [Observer](#observer) - pass message from one object to others
  * [Builder](*builder) - build a complex object for someone else
* Object(s) in object
  * [Composite](#composite) - components in composite
  * [Flyweight](#flyweight) - common data shared across objects
* Object to be passed around and acted upon
  * [Prototype](#prototype) - object that can be cloned to new objcect
  * [Singleton](#singleton) - single instance to be referenced by any object
  * [Command](#command) - command to be executed on receiver later
  * [Memento](#memento) - data needed to undo/redo an action
  * [State](#state) - data needed to inform others about their state
* Object that lends functionality to others at run time
  * [Decorator](#decorator) - accept others to lend functionality
  * [Abstract Factory](#abstract-factory) - accepted by others to lend object creation functionality
  * [Strategy](#strategy) - accepted by others to lend functionality
  * [visitor](#visitor) - accepted by others to lend functionality
* Object that references the next object in a chain-like fashion
  * [Chain of responsibility](#chain-of-responsibility) - sequentially invoke the next object in chain
  * [Interpreter](#interpreter) - sequentially evaluates a message
* Others
  * [Iterator](#iterator)

# Creational
## Factory Method
Gist:
* An object creation method that resides in its caller
* Whereas [abstract factory](#abstract-factory) is an object with potentially many factory methods and is separate from the caller object
* You can pass a different [abstract factory](#abstract-factory) object to the caller to use a different set of factory methods but you can only subclass the caller to change its own factory method
<img src="https://javacurious.files.wordpress.com/2013/03/fm_dp1.png" alt="UML Illustration" width="400">

Use cases:
* When you want to encapsulate object creation to a method

## Abstract factory
Gist:
* An object with potentially many factory methods
* Lends itself to the caller to produce required object
<img src="https://javacurious.files.wordpress.com/2013/03/af_dp.png" alt="UML Illustration" width="400">

Use cases:
* When you want the flexibility of producing different products at run time

## Builder
Gist:
* Builds a complex object for someone else.
<img src="https://upload.wikimedia.org/wikipedia/commons/8/87/W3sDesign_Builder_Design_Pattern_UML.jpg" alt="UML Illustration" width="400">

Use cases:
* When instantiating an object involves assembling multiple components dynamically

## Prototype
Gist:
* An object that can be cloned to create new object
<img src="https://upload.wikimedia.org/wikipedia/commons/c/c4/W3sDesign_Prototype_Design_Pattern_UML.jpg" alt="UML Illustration" width="400">

Use cases:
* When you want to avoid repeatedly defining the same object structure in factory method

## Singleton
Gist:
* Static class to get one and only one instance.
* Only the static class can instantiate and destruct of the instance.
* One of the authors suggested to remove this pattern
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
* No impact on existing abstract-implementation files when you need different class structure and implementation. Just subclass a different pair of abstract-implementation files!


## Composite
Gist:
* The essence is to use a common interface for both component and composite
* Composite hold references to each component
* Composite distribute client call to each component methods
<img src="https://upload.wikimedia.org/wikipedia/commons/5/5a/Composite_UML_class_diagram_%28fixed%29.svg" alt="UML Illustration" width="400">

Use cases:
* Unify client-facing interface for composite and component operations so that you don't have to worry whether you are calling a component or composite

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

## Command
Gist:
* Resembles functional programming
* A command object contains all information needed to execute the command at a later time (can be queued)
* 3 objects are involved to execute an action:
  * Invoker: issues a command, only know command interface, does not know the command receiver
  * Command: has reference to the receiver and all the parameters needed for the receiver to perform the action
  * Receiver: the target object which performs the actual action

Use cases:
* UI action, input replay, undo-redo, transaction, multi-page wizards

## Interpreter*
Gist:
* Kind of a special case of [composite](#composite) pattern
* A sequence of interpreters completes a task 

## Iterator
Should require no explanation

## Mediator
Gist:
* A middle man that handles interaction between objects, like a single point of contact
* Objects calls mediator and pass themselves as parameter
* Mediator then handles the interaction for them 
<img src="https://upload.wikimedia.org/wikipedia/commons/9/92/W3sDesign_Mediator_Design_Pattern_UML.jpg" alt="UML Illustration" width="400">

Use cases:
* Tidy up objects interaction 

## Observer
Gist:
* Somewhat a special case of [mediator](#mediator)
* Object being observed register/unregister observers in a private list
* Object notifies registered observers when there is a state change
* Observers then inform other relevant objects about the state change event
* Decouples the observed object from the other objects
<img src="https://upload.wikimedia.org/wikipedia/commons/0/01/W3sDesign_Observer_Design_Pattern_UML.jpg" alt="UML Illustration" width="400">

Use cases:
* Event listener, the middle man of message/event passing
* MVC pattern where observer is the controller

## Memento
Gist:
* A simple class with setState and getState methods
* But unlike [state](#state) pattern, it does not act on state, just a data keeper
<img src="https://upload.wikimedia.org/wikipedia/commons/3/38/W3sDesign_Memento_Design_Pattern_UML.jpg" alt="UML Illustration" width="400">

Use cases:
* Redo/Undo

## State
Gist:
* Structurally similar to [strategy](#strategy) and [visitor](#visitor)
* Context object accepts state object at run time and behave differently based on state
<img src="https://upload.wikimedia.org/wikipedia/commons/e/ec/W3sDesign_State_Design_Pattern_UML.jpg" alt="UML Illustration" width="400">

Use cases:
* When you want to change context object's behaviour at run time on different conditions

## Strategy
Gist:
* Structurally similar to [state](#state) and [visitor](#visitor)
* Context object accepts strategy object and calls strategy object to perform operation at run time
<img src="https://upload.wikimedia.org/wikipedia/commons/4/45/W3sDesign_Strategy_Design_Pattern_UML.jpg" alt="UML Illustration" width="400">

Use cases:
* When you want context object to receive and execute differet algorithms at run time

## Visitor
Gist:
* Structurally similar to [state](#state) and [Strategy](#strategy)
* Element object accepts visitor object and calls vistor object to perform operation on element at run time
<img src="https://upload.wikimedia.org/wikipedia/commons/0/00/W3sDesign_Visitor_Design_Pattern_UML.jpg" alt="UML Illustration" width="400">

Use cases:
* When you want element object to receive and execute differet algorithms at run time (very similar to [strategy](#strategy))

## Template
Gist:
* Essentially what you always do when you create super-subclass structure
* Provide abstract or shared methods in base class and allow subclass to implement or override the methods

Use cases:
* When you want objects to have shared and custom behaviours
