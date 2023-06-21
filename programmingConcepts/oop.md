--------------------------------------------------------------------------------
= Object Oriented Programming =
--------------------------------------------------------------------------------
The Four major principles of OOP
  - Encapsulation
  - Abstraction
  - Inheritance
  - Polymorphism

  - Encapsulation
    Encapsulation means information hiding; The data in the class can not be
    viewed or modified from outside the classe, instead, viewing and modifying
    the data in the class must be done through functions that are controlled by
    the class object.

  - Abstraction
    Abstraction is related to encapsulation. When using abstraction, you hide the
    internal implementatio of how data is manages and provide a more simplified
    interface t othe ouside code. The primary reason is the cause "loose coupling"
    (meaning that its is desirable for code that is responsible for one set of data
    to be independent and separated from other code).

  - Inheritance
    Used for code reuse.

  - Polymorphism
    Polymorphism is related to Inheritance in that it is possible to create
    an object that can be set to on of any number of possible typs that inherit
    from the same base lineage. This capability is useful for scenarios where the
    type needed is not imeediately knowable but can be set at runtime once the
    appropriate circumstance have arisen.

--------------------------------------------------------------------------------
== Terms ==
  Object-oriented Analysis   | The process of looking at a proble, system, or task
                             | and identifying the objects and interactions
                             | between those objects. The analysis stage is all
                             | about what needs to be done
                             | Analysis Stage -> requierments (description of system)
                             |
  Object-oriented Design     | The process of converting such requirements into
                             | an implementation specification
                             | the designer:
                             |     names the objects
                             |     defines the behaviors on other objects
                             | The design stage is all about tranforming what should
                             | be done into how is should be done
                             |
                             | Design Stage -> implementation specification
                             |
  Object-oriented programming| The proces of converting a design into a working
                             | program that does what the procuct owner originally
                             | requested
                             |
  An Object                  | A collection of data with associated behaviors
                             |
  Composition                | Composition is the act of collecting several
                             | objects together to create a new one. Composition
                             | is usually a good choice when one object is part
                             | of another object.
                             |
  Aggregation                | Aggregation is similar to composition, the difference
                             | being that aggregate object can exist independently.
                             |
  Interface                  | An abstract method that is initiated by a class
                             | which has no default behavior, wherein an inheriting
                             | class can define the interfaces behavior.
                             |
--------------------------------------------------------------------------------
4 + 1 Views
  Logical View               | A logical view of the data entities, their static
                             | attributes, and their relationships. This is the
                             | heart of object-oriented design
                             |
  Process View               | A process view that describes how the data is
                             | processed. This can take a variety of forms, including
                             | state models, activity diagrams, and sequence diagrams
                             |
  Development View           | A development view of the code components to be
                             | built. This diagram shows relationships among
                             | software components. This is used to show how class
                             | definitions are gathered into models and packages
                             |
  Physical View              | A physical view of the application to be integrated
                             | and deployed. In cases where an application follows
                             | a common design pattern, a sophisticated diagram
                             | isn't necessary. In other cases, a diagram is
                             | essential to show how a collection of components are
                             | integrated and deployed
                             |
  Context View               | A context view that provides a unifying context
                             | for the other four views. The context view will
                             | often describe the actors that use (or interact)
                             | with the system to be built. This can involve
                             | human actors as well as automated interfaces: both
                             | are outside the system, and the system must respond
                             | to these external actors
                             |
                             |
                             |
                             |
--------------------------------------------------------------------------------
== OOP in Python ==
                             | class Employee(inherited-class):   <- Class definition with inherited class
                             |    def __init__(self, name, age):  <- Constructor / initializer method definition
                             |      self.name = name                 (must always have 'self as a parameter'
                             |      self.age = age                    as the method must be applied to the created instance)
                             |      self.hours_worked = 0
                             |
                             |    def add_hourse(self, hours):
                             |      self.hours_worked += hours
                             |
