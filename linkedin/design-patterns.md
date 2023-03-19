# Creational Design Patterns
good software must be 
+ Flexible 
+ Maintainable
+ Extendable

creational patterns focus on object instantiation
+ The **goal** of creational patterns is to efficiently create objects to increase flexibility

## Factory Method
+ one of the most used design patterns
+ Encapsulates the creation of related objects
+ Provides and interface to create an object but defers the creation to the sub classes
+ create object based on runtime parameters
+ Do not need to know which objects you will need to create
+ Lets the subclasses instantiate the object instead of the main program
+ easy to add new products or change existing ones
+ no need to make changes throughout the code base

![](./images/factory-pattern.png)



eg: coffee machine  
+ espresso
+ Cappuccino


## Abstract Factory Method
+ Provides an interface for creating families of related objects without specifying their concrete classes
+ Abstract factories keep families of objects together


![](./images/abstract-factory-pattern.png)

[Code Showing Abstract factory](./code/code-abstact-factory.md)


eg: car factories  
+ gas cars
+ electric cars


## Builder
+ Separates construction of complex objects
+ Builds a complex object one step at a time
+ Same construction process for different representations
+ The builder design **encapsulates** the build
+ Builders share the same steps to build an object

![](./images/builder-pattern.png)

[Code describing builder pattern](./code/code-builder.md)


## Prototype
+ Creates new objects by cloning or copying an existing one
+ is it better to perform shallow or deep copy

![](./images/prototype-pattern.png)


## Singleton
+ constructor is private
+ static getInstance() creates an object
+ globally available only one instance exists


![Summary](./images/creational-pattern-summary.png)


<div style="page-break-after: always"></div>



# Structural 
class hierarchies and relationships  
































































<div style="page-break-after: always"></div>

# Behavioral Design Patterns
Object Intercommunication


