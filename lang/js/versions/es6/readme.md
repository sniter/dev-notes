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

_.map(my_list, v => v + 1);

// In case many paramaters
_.map(my_list, (v, x) => v + x);
```

ES5
``` js
var my_list = [1,2,3];

_.map(my_list, function (v){ return v + 1;});

// In case many paramaters
_.map(my_list, function (v, x){ return v + x;});
```