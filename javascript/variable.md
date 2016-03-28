Variable
========

### Hoisting

Wherever a var appears inside a scope, that declaration is taken to belong to the entire scope and accessible everywhere throughout.

Metaphorically, this behavior is called hoisting, when a var declaration is conceptually "moved" to the top of its enclosing scope. Technically, this process is more accurately explained by how code is compiled, but we can skip over those details for now.

Consider:

``` javascript
var a = 2;

foo();                  // works because `foo()`
                        // declaration is "hoisted"

function foo() {
    a = 3;

    console.log( a );   // 3

    var a;              // declaration is "hoisted"
                        // to the top of `foo()`
}

console.log( a );   // 2
```

### Scope

When you declare a variable, it is available anywhere within that scope and any lower scopes. If you try to access a variable's value in a scope that it's not available, you'll get a ReferenceError. If you try to set a variable that hasn't been declared, you'll end up either creating a variable in top-level global scope or getting an error, depending on "strict mode"

``` javascript
function foo() {
    a = 1;  // `a` not formally declared
}

foo();
a;          // 1 -- oops, auto global variable :(
```

You can declare a variable inside a block using `let` keyword. The scoping rules will behave roughly the same as in functions.

``` javascript
function foo() {
    var a = 1;

    if (a >= 1) {
        let b = 2;

        while (b < 5) {
            let c = b * 2;
            b++;

            console.log( a + c );
        }
    }
}

foo();
// 5 7 9
```
