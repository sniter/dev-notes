# Javascript - version ES6

## Sources

* [ECMAScript 6 — New Features: Overview & Comparison](http://es6-features.org/)

## What's new

### Define variables

#### Variables

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

#### Constants

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

### Define lambda

ES6:
``` js
let my_list = [1,2,3];

my_list.map(v => v + 1);

// In case many paramaters
my_list.map((v, x) => v + x);

// handling context *this*
my_list.map(v => this.calc(v) + 1)
```

ES5
``` js
var my_list = [1,2,3];

my_list.map(function (v){ return v + 1});

// In case many paramaters
my_list.map(function (v, x){ return v + x});

// CASE: handling context *this* -- case 1
var self = this;
my_list.map(function (v){ return self.calc(v) + 1});

// CASE: handling context *this* -- case 2
my_list.map(function (v){ return this.calc(v) + 1}, this);

// CASE: handling context *this* -- case 3 -- since ECMAScript 5.1 only
my_list.map(function (v){ return this.calc(v) + 1}.bind(this));
```

### Define objects

ES6:
``` js
let x, y = 1;

// CASE: Object properties shorthand
let tc1 = { x, y } // { x: 1, y: 1}

// CASE: Object properties names
let tc2 = {
    foo: 'bar',
    ['prop_' + x]: 'baz' // property definition
}

tc2['prop_1']; // baz

// CASE: Object metods definition
let tc3 = {
    foo(a,b){
        return a + b;
    }
}

tc3.foo(1, 2); // 3

// CASE: Object generator methods definition
let tc4 = {
    *foo(a,b){
        // ...
    }
}
```

### Strings

#### Templates

More about templates can be found [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals).

ES6:
``` js
let a = 5;

// CASE: Interpolation
let t = `My custom template: ${a}` // My custom template: 5

// CASE: Multiline feature
let t2 = `It is multi-line
by default: ${a}`
/*
It is multi-line
by default: 5
*/

// CASE: Expressions
let t3 = `It supports expressions: ${a + 3}`; // It supports expressions: 8

// CASE: special symbols are not escaped
let t4 = `Template with \n newline` // Template with
                                    // newline

// CASE: round brackets may be skipped while calling function with template as param
function foo(tpl){
    return tpl + '_foo';
}

foo `Calling function without brackets` // Calling function without brackets_foo
```

### Modules

#### Export

More information about `export` can be found [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export)

**NB: Default export object can be declared once per script**

ES6:
```js

// CASE: exporting object declared earlier
export { MyObject };

// CASE: exporting function
export function foo(a, b){
    return a + b;
}

// CASE: exporting constant
export const myConst = 15;


// CASE: exporting default object(function)
export default function(a, b){
    return a + b;
}

// CASE: exporting default object(class)
export default class{
    // ...
}
```

#### Import

More information about `import` can be found [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)

ES6:

``` js
import * as MyModule from "AnotherModule"; // import all

import { ASingleMember } from "AnotherModule"; // import single object into current scope

import { ASingleMember, YetAnotherSingleMember } from "AnotherModule"; // import single objects into current scope

import { ASingleMember as MySingleMember} from "AnotherModule"; // import single object into current scope

import "AnotherModule"; // mport an entire module for side effects only, without importing any bindings.

import DefaultObject from "AnotherModule"; // Importing default object from module
```

### Functional Programming

#### Extractors

ES6:
``` js
let myList = [ 7, 42, 12, 43 ];

// CASE: Arrays Extractor - Basic extractors 1
let [tc1, ] = myList;
tc1; // 7

// CASE:  Arrays Extractor - Basic extractors 2
let [tc2] = myList;
tc2; // 7

// CASE:  Arrays Extractor - Basic extractors 3
let [tc3=777,] = myList;
tc3; // 7

// CASE: Arrays Extractor - Skipping values
let [,tc4] = myList;
tc4; // 42

// CASE: Arrays Extractor - Fail tolerance
let [,,,,tc5] = myList;
tc5; // undefined


// CASE: Arrays Extractor - Function parameter matching
function foo([a, b]){
    return a + b;
}

foo([1, 2]); // 3


// CASE: Object Extractor - Values extractor
// Ensure that extracted variables werent declared beforehead
let myDict = {
    key: "value",
    fkey: {
        key: "value2"
    }
}
let { fkey: { key: a }, key: b} = myDict;

a; // value2
b; // value

// CASE: Object Extractor - Function parameter matching
function foo({ prefix: a, postfix: b }){
    return a + b;
}

foo({ prefix: 1, postfix: 2}); // 3

```


