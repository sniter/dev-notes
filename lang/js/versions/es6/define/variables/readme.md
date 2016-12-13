# Define variables

ES6:

The `let` statement declares a **block scope local variable**, optionally initializing it to a value.

More about `let` syntax can be found [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let).

``` js
let len = 1;

for(let i=0; i<len; i++){
    // ...
}
```

ES5:

The variable statement declares a variable, optionally initializing it to a value.

More about `var` syntax can be found [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var).

``` js
var foo;

for(var i=0; i<len; i++){
    // ....
}
```

# Define Constants

ES6 (new):

Constants are **block-scoped**, much like variables defined using the let statement. The value of a constant cannot change through re-assignment, and it can't be redeclared. 

More about `const` syntax can be found [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const).

``` js
const foo = 111;
```

ES5:
``` js
Object.defineProperty(typeof global === "object" ? global : window, "PI", {
    value:        111,
    enumerable:   true,
    writable:     false,
    configurable: false
});
```


