# Functional Programming

# Extractors

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


