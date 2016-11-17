### Variable Arguments

* In Scala, to implement a function that take a variable number of arguments you denote the arguments type with a `*` symbol

    ```scala
    def sum(args: Int*): Int = {
      var result = 0
      for (arg <- args) result += arg
      result
    }
    ```

* The `args` in the example above is a sequence of `Int` values. But you can not pass a sequence of `Int` values directly to `sum`. Overcome this by append `: _*` after the sequence

    ```scala
    sum(1 to 5)  // => compile error
    sum(1 to 5: _*)  // => ok
    ```

  This call syntax is needed in recursive function

    ```scala
    def recursiveSum(args: Int*) : Int = {
      if (args.length == 0) 0
      else args.head + recursiveSum(args.tail : _*)
    }
    ```
