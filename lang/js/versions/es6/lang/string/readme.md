# String

## String Interpolation 

More information about templates can be found [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals).

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

## Symbols

A Symbol is a primitive data type whose instances are unique and immutable. 

More information about `Symbol` templates can be found [here](https://developer.mozilla.org/en-US/docs/Glossary/Symbol)

ES6:

``` js
// CASE: Creating Symbol
const mySymbol = Symbol("MySymbol")

// CASE: Unique Behavior
Symbol("foo") !== Symbol("foo") // true

// CASE: Unique Behavior #2
let f = "foo"

f1 = Symbol(f)
f2 = Symbol(f)

f1 !== f2 // true

// CASE: Cannot create Symbol from Symbol
f3 = Symbol(f1) // raises TypeError: Cannot convert a Symbol value to a string
```
