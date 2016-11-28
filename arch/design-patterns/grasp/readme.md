# GRASP

General Responsibility Assignment Software Patterns

Author: Craig Larman

## Main Task

    - Define  how to delegate responsibilities in code
    - Tried and teseted programming pricniples

## Patterns:

### Information expert (used to determine where to delegate responsibilities)

    - look at given responsibility
    - determine the information needed to fullfill it
    - determine where that information is stored
    - Information Expert will lead to placing responsibility on the class  with the most information required to fulfill it.

### Creator

    - Class B creates class A:
        - Instances of B contain or compositely aggregate instances of A
        - Instance of B record instances of A
        - instances of B closely use instances of A
        - Instances of B have the initializing information of instances of A and  pass it on creation

### Controller

    - Is responsible to handle clients requests
    - should delegate the work to other objects
    - coordinates or controls the actitvity, it should not do much work itself

### Low Coupling (dictates how to assign responsibilities to support)

    - lower dependency between classes
    - change in one class having lower impact on other classes
    - higher reuse potential

### High Cohesion (used in support of Low Coupling)

    - Responsibility of given element are strongly related and highly focused

### Polymorphism 

As is in OOP

### Pure Fabrication

    - is a class that does not represent a concept in the problem domain, specialy made up to achieve low couppling, high cohension and reuse potential thereof derived
    - This kind of class is called Service in DDD


### Indirection

    - Pattern supports low coupling between two elements by assigning responsibility between them to an intermediate object

### Protected Variations

    - Pattern protects elements from variations on other elements by wrapping the focus of instability with an interface and using polymorhism to create various implementations