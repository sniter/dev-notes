# Scala Syntax

## Main aspects
- JVM Compatible, Java Interoperability
- No primitive type, just in case of translation
- Statically Typed
- Multiparadigm language (OOP/FP)

## Basic Java Difference

- Traits
- Tuples
- Pattern Matching
- Case classes and objects
- Type Inference and higher kinds
- Multiple inheritance (partial)
- Implicits
- Metaprogramming
- no breaks and continue (via wrappers)
- Custom postfix ops, i.e +, * etc.
- passing parameters by value and by name

## Scala vs Java Cons

- Lazy vals
- Currying
- Closures (for Java < 8)
- Metaprigramming based on AST Parse, Reflection is deprecated

## Syntax Features

### Identifiers
    - An alphanumeric identifier starts with a letter or an underscore character

### Operators
    - like in java
    - return specific behavior in lambdas

### Functions, methods

* First class function - function which can be represented as object and can be passed as parameter
* Function value - representation form of first class functions at runtime, i.e. type Function<...>
* Function literal - shorthand first-class function, has no name in Source code, i.e (in:Int):Int => in + 10,
* Bound variable - variable is defined and used within expression (function)
* Free variable - variable that was defined before expression(function)
* Closure - function that have access to the scope it was called
* using placeholder syntax (underscore)
* apply()- method name that can be ommited
* unapply() - extractor to Option[Tuple]
* passing parameters by value and by name
* Repeated parameters, i.e. def foo(p:String*) // Array[String], like ... in Java. Dont forget that array can be converted to repeated parameters by adding "value: _*"
* Tail recursion - is advised method to avoid classic imperative loops, cand be marked with annotation @tailrec
* Currying - a way to write functions with multiple parameters lists

### OOP

* Two namespases:
 * values (fields,methods,packages)
 * types (class,trait)
* import
 * a => b is alias
 * a => _ exclude
 * a._ include all
*Scala types are not variant.
* co-variant types: [+T] T is subtype of S then V[T] is subtype of V[S]
* contra-variant types: [-T] T is subtype of S then V[S] is subtype of V[T]
 * contra-variant required
  * method parameters
  * lower bounds
* Liskov substitution principle:
  * if type T is subtype of type U then you can substitute a value of type T wherever a value of type U is required

### Classes

 * val
  * in class - public properties with getter
  * immutable, thread-safe
  * custom postfix ops, i.e +, * etc.
 * var
  * in class - private properties with getter and setter
 * lazy val
  * double checked thread safe variable with lazy initialization
 * Overriding Accessors/Mutators (both methods should be overridable)
  * getter
   * def ${field}:Type = ...
  * setter
   * def ${field}_:Unit = ...
 * Companion Object / Singleton objects
  * should be located in same file together with class and have same name

### Traits

* A mixin
* Allow mulitple inheritance
* Can be partially implemented:
 * Trait Foo[A+]{ val a[A]: String = 5; val b:String }
* Can be typed
 * Trait Foo[A+]{ val a[A]: String = 5 }
* Can be instatiated.
 * val foo = new Foo{  }

### Case Classes

* Multiple constructors
* First constructor (in class declaration) is main constructor
* Another should start def this(...), calling main or parent constructor like in Java - at 1st line
* extends Product
* Has companion with constructor, extractor and copy methods

#### Case Objects

* Pattern matching support
* defaul implementation equals() and hashCode()
* Serialization implementation
* toString overriding
* implementation Product trait

#### Sealed cases

* improves pattern matching

### Type Inference

TODO: describe

### Type Erasure

* anywhere except Array[] - java heritage

### Implicits

* Implicit conversions
* Implicit paramenter
 * Recommended to use

### Pattern Matching

* Using placeholders
* guard functions
* type erasure
* set var @
* extractor

###  FilterMonadic[+A,+Repr]
* flatMap
* map
* foreach
* withFilter

# Option

TODO: describe

# Try

TODO: describe

# Async via Future

TODO: describe

# Combinator parsing (built-in)

TODO: describe