# Modules

## Export

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

## Import

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