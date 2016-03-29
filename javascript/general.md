General
=======

### Strict mode

"Strict mode" is introduced from ES5. Generally it keeps the code to a safer and more appropriate set of guidelines. Adhering to strict mode also makes your code generally more optimizable by the engine.
You can opt in to strict mode for an individual function, or an entire file, depending on where you put the strict mode pragma.

``` javascript
function foo() {
    "use strict";

    // this code is strict mode

    function bar() {
        // this code is strict mode
    }
}

// this code is not strict mode
```

Compare that to

``` javascript
"use strict";

function foo() {
    // this code is strict mode

    function bar() {
        // this code is strict mode
    }
}

// this code is strict mode
```

Strict mode disallow implicit top-level global variable declaration

``` javascript
function foo() {
    "use strict";   // turn on strict mode
    a = 1;          // `var` missing, ReferenceError
}

foo();
```
