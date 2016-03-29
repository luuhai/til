Function
========

### Difference between methods defined by function x() and var x = function()

* Methods defined by function x() can be called before you define it. (named function)
* If you use var x = function() you must define it before you can call it. (anonymous function)

### Immediately invoked function expressions (IIFEs)

``` javascript
(function IIFE(){
    console.log( "Hello!" );
})();
// "Hello!"

IIFE(); // ReferenceError
```

### Closure

```javascript
function makeAdder(x) {
    function add(y) {
        return y + x;
    };

    return add;
}

var plusOne = makeAdder(1);
var plusTen = makeAdder(10);

plusOne( 3 );    // 4
plusOne( 41 );   // 42

plusTen( 13 );   // 23
```
