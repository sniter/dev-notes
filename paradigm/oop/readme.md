# OOP

## Items

* Classes
* Objects
* Class variables
* Instance variables
* Member variables
* Class methods
* Instance methods

## Main points

### Encapsulation

If class disallow to acces object data directly, only via methods only

### Composition

Objects can contain other objects in their instance variables

### Inheritance

Possibility of subtyping system when child class may have access to methods and properties of parent class
    
### Delegation

Object refers to anther object to provide a specified set of functionalities.

### Polymorhism (subtype polymorphism)

using objects with single interface but different implementation

### Open recursion

Existance of ``self`` or ``this`` objects

## Principles

### SOLID

* Single responsibility
    - Class should have only one responsibility
* Open/Closed
    - Open for extension closed for modification
* Liskov substitution principle
    - instances in program can be replaced with subtype instances without altering correctness of the program
* Interface segregation principle
    - many client-specific interfaces are better then general purpose interface
* Dependency inversion principle
    - Depending on interfaces not implementations

### KISS

Keep it simple, stupid - simplicity is key point of design

### DRY

Every piece of knowledge should have single, unambiguous, authoritative representation within the system

### YAGNI (until deemed necessary)(XP)

* Add functionality when it is deemed necessary
* Do the simplest think that can possibly work
* Worse is better
* Software that is limited but simple to use may be more appealing then reverse