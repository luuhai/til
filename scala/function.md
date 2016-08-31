### Function

* `return`
  - Functions that have explicit `return` method must be defined with explicit return type.
  - Using `return` in Scala is error-proned and should be avoided.
  - Is has no effect on anonymous functions. For example:
  ```scala
  def foo(x: Int): Int = {
    val anonFunc: Int => Int = { z =>
      if (z > 5)
        return x // This line makes x the return value of foo
      else
        z + 2    // This line is the return value of anonFunc
    }
    anonFunc(x)  // This line is the return value of foo
  }
  ```
