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

``` js

class MyParentClass {
    // ... some code here
};

class MyChildClass extends MyParentClass {
    // ... some code here
}
```