### Get value of an Option

There are 2 ways to transform and get value of an Option: using `map / getOrElse` or `fold`.

```scala
def format(value: Option[Double]): String = value.map(v => v.toString + "%") getOrElse "Nothing"
```

is equal to

```scala
def format(value: Option[Double]): String = value.fold("Nothing") { _.toString + "%" }
```

`fold` is shorter but many people prefer `map / getOrElse` for some reasons:
* Option.getOrElse/map is a more idiomatic Scala code because Option.fold was only introduced in Scala 2.10.
* Fold on Option is not obvious to most developers.
* Option.fold is not readable.
  + Reverses the order of Some vs None.
  + Putting the default condition first there makes it not as intuitive.
  + When code gets long, the lack of an obvious boundary with two closures is confusing. (“} {” compared to getOrElse)
* Fold is a more functional idiom in general.

Source: https://kwangyulseo.com/2014/05/21/scala-option-fold-vs-option-mapgetorelse/
