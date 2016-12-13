# Define objects

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
