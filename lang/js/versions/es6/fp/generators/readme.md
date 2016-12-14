# Generators

More information can be found [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*)

It's a function that returns Generator object, that allow to iterate anything. 

The only requirement is statement `yield` in function body.

``` js
function* myGenerator(any_list){
    for(value in any_list){
        yield value;
    }
}
```

## Iteration interface

More inf can be found [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols)

Iterator can be owerride using `Symbol.iterator` key:

``` js

let myString = "1,2,3"

myString[Symbol.iterator] = function*(){
    // ... some code here
}
```

## Iterable Protocol

More imformation can be found [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#iterable)

Method `iterator()` required to be implemented.

## Iterator Protocol

Interface require to implement tho only one method - `next()`, which return object with next properties:

|property|type|description|
|--------|----|-----------|
|done|boolean|if *true* - then iteration completed, else *false* - iteration is in progress|
|value|any JS value|can be omitted if **done** is *true*|

More information about `iterator` protocol can be found [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#iterator)

``` js

let myList = [1, 2, 3]

myList[Symbol.iterator] = function(){
    return { // this is the iterator object
        next: function() {

            if (this._first) {
                this._first = false;
                return { value: "Hello", done: false };
            } else {
                return { done: true };
            }
        },
        _first: true
    };
}

```
