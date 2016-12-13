# Define lambda

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
