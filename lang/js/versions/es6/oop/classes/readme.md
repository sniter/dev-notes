# Class

This feature is new. All the examples are written is ES6

More about JS Classes can be found [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/class)



## Definition

> **Warning**
> Re-declaring a class using the class declartion throws a type error.

``` js
class MyClass {
    // ... some definitions here
}
```

## Constructor 

More information about `constructor` can be found [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/constructor)

``` js
class MyClass {
  constructor(a) {
    this.a = a;
  }
}
```

## Methods

``` js
class MyClass { 
    // ... some code here
    updateA (a) {
        this.a = a;
        return this;
    },
    sum (b) {
        return this.a + b
    }
}
```

## Inheritance

More information about iheritance can be found [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/extends).

``` js

class MyParentClass {
    // ... some code here
};

class MyChildClass extends MyParentClass {
    // ... some code here
}
```

## Static methods

The static keyword defines a static method for a class.

More information about `static` can be found [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/static).

``` js

class MyClass {
    static function myStaticMethod(a, b){
        return a + b;
    }
}
```