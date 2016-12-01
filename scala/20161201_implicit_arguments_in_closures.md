### Implicit arguments in closures

A function argument can be marked as implicit just as with methods. Within the scope of the body of the function the implicit parameter is visible and eligible for implicit resolution.

```scala
trait Foo { def bar() }

trait Base {
  def callBar(implicit foo: Foo) = foo.bar
}

object Test extends Base {
  val f: Foo => Unit = { implicit foo =>
    callBar
  }

  def test() = f(new Foo {
    def bar() = println("Hello")
  })
}

Test.test() // => "Hello"

def pi(implicit i: Int = 1) = println(i)
val x: Int => Unit = { implicit i => pi }
val y: Int => Unit = { i => pi }
x(5) // => 5
y(5) // => 1
```
