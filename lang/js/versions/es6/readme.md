# Javascript - version ES6

## Sources

* [ECMAScript 6 — New Features: Overview & Comparison](http://es6-features.org/)

## What's new

### Define variables

#### Variables

ES6:
``` js
let len = 1;

for(let i=0; i<len; i++){
    // ...
}
```

ES5:
``` js
var foo;

for(var i=0; i<len; i++){
    // ....
}
```

#### Constants

ES6 (new):
``` js
constant foo = 111;
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
