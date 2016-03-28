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
