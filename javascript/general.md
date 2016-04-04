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

### Module

``` javascript
function User(){
    var username, password;

    function doLogin(user, pw) {
        username = user;
        password = pw;

        // do the reset of the login work
    }

    var publicAPI = {
        login: doLogin
    };

    return publicAPI;
}

// create a User module instance
var fred = User();

fred.login( "fred", "12Battery34!" );
```

The `User()` function serves as an outer scope that holds the variables `username` and `password`, as well as the inner `doLogin()` function; these are all private inner details of this `User` module that cannot be accessed from the outside world.
Executing `User()` creates an instance of the `User` module -- a whole new scope is created, and thus a whole new copy of these inner variables/functions.
The inner `doLogin()` function has a closure over `username` and `password`, meaning it will retain its access to them even after `User()` function finishes running.

### this

``` javascript
function foo() {
    console.log( this.bar );
}

var bar = "global";

var obj1 = {
    bar: "obj1",
    foo: foo
};

var obj2 = {
    bar: "obj2"
};


foo();              // "global"
obj1.foo();         // "obj1"
foo.call( obj2 );   // "obj2"
new foo();          // undefined
```

1. `foo()` ends up setting `this` to the global object in non-strict mode
2. In strict mode, `this` would be `undefined` and you'd get an error in accessing the `bar` property
3. `obj1.foo()` sets `this` to the `obj1` object
4. `foo.call( obj2 )` sets `this` to the `obj2` object
5. `new foo()` sets `this` to a brand new empty object.

### Prototype

``` javascript
var foo = {
    a: 42
};

// create `bar` and link it to `foo`
var bar = Object.create( foo );

bar.b = 'Hello World'

bar.b;   // "Hello World"
bar.a;   // 42 <-- delegated to `foo`
```

The `a` property doesn't actually exist in `bar` object, but because `bar` is prototype-linked to `foo`, JavaScript automatically falls back to looking for `a` on the `foo` object.
