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

// handling context *this* -- case 1
var self = this;
my_list.map(function (v){ return self.calc(v) + 1});

// handling context *this* -- case 2
my_list.map(function (v){ return this.calc(v) + 1}, this);

// handling context *this* -- case 3 -- since ECMAScript 5.1 only
my_list.map(function (v){ return this.calc(v) + 1}.bind(this));
```


