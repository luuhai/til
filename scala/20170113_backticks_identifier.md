### Backticks identifier

* Scala allows you to define identifiers that start and end with backticks and can contain [pretty much anything](https://stackoverflow.com/questions/7656937/valid-identifier-characters-in-scala) between them, including space.

    ```scala
    def `i see what you did there` =
      // Things you did
    ```

* You can use backticks identifier to call methods from Java libraries whose name is reversed keyword in Scala.
* In pattern matching, using backticks identifier in a `case` expression refer to a local scope variable, avoid `variable shadowing`

    ```scala
    val x = 1
    val y = 3

    def check(expr: Any) = expr match {
      case (`x`, _) => 1
      case (2, "b") => 2
      case (y, "c") => y
      case _ => 3
    }

    check((1, "a")) // => 1
    check((2, "b")) // => 2
    check((4, "c")) // => 4
    ```
