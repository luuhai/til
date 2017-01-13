### Partial Function

* A `partial function` is a function that only apply to a subset of values. For examples, a square root function only apply for positive integers.
* In Scala, we define a `partial function` is defined as a block with multi `case` statements, or by `PartialFunction` trait.

    ```scala
    val fraction = new PartialFunction[Int, Int] {
      def apply(d: Int) = 42/d
      def isDefinedAt(d: Int) = d != 0
    }

    fraction(42) // => 1
    fraction(0)  // => java.lang.ArithmeticException

    // The exact same function can be written
    val fraction: PartialFunction[Int, Int] = {
      case d: Int if d != 0 => 42 / d
    }

    fraction(42) // => 1
    fraction(0)  // => MatchError
    ```

* A `PartialFunction` must provide `isDefinedAt` method, which allows the caller of the function to know whether the function can return result for a given value.
* Collections that extends `Traversable` trait use `collect` function, not `map`, to map elements using a `PartialFunction`

    ```scala
    List(42, 21, 0) collect fraction => List(1, 2)
    ```

* Collections that extends `Seq` or `Map` can be used as `PartialFunction`

    ```scala
    val pets = List("dog", "cat", "frog")
    Seq(1,2,3) collect pets // => List("cat", "frog")
    ```

* `PartialFunction` trait provides `lift` method that returns a normal value that doesn't crash

    ```scala
    pets.lift(0)  // => Some(cat)
    pets.lift(42) // => None
    ```

