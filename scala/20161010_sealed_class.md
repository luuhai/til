### Sealed Class

* A sealed class in Scala can be only directly inherited by classes in the same source file.
* "Grandchild" classes of a sealed class can stay on other files.
* A practical consequence of this is that the compiler can warn if the pattern match is incomplete.

    ```scala
    sealed abstract class Exp
    case class Var(name: String) extends Expr
    case class Number(num: Double) extends Expr
    case class UnOp(operator: String, arg: Expr) extends Expr
    case class BinOp(operator: String,
        left: Expr, right: Expr) extends Expr

    def describe(e: Expr): String = e match {
      case Number(_) => "a number"
      case Var(_)    => "a variable"
    }

    // warning: match is not exhaustive!
    // missing combination           UnOp
    // missing combination          BinOp
    ```

* If a match's selector expression carries `@unchecked` annotation, exhaustivity checking for the patterns that follow will be suppressed.

    ```scala
    sealed abstract class Exp
    case class Var(name: String) extends Expr
    case class Number(num: Double) extends Expr
    case class UnOp(operator: String, arg: Expr) extends Expr
    case class BinOp(operator: String,
        left: Expr, right: Expr) extends Expr

    def describe(e: Expr): String = (e @unchecked) match {
      case Number(_) => "a number"
      case Var(_)    => "a variable"
    }

    // No warning
    ```

