### `freeze`, `dup` and `clone`

* `freeze` can be used to prevents an object from further changes.

```ruby
a = 'Hello!'
a.freeze
a.replace('Goodbye!') # ==> RuntimeError
```

* `freeze` an array _do not_ freeze its elements.

```ruby
a = ['foo', 'bar']
a.freeze
a[0] = 'boo' # ==> RuntimeError
a[0].replace('boo')
p a # ==> ['boo', 'bar']
```

* `dup` and `clone` both duplicate an object. The difference is that if you `clone` a frozen object, the clone is also frozen, whereas if you `dup` a frozen object, the duplicate isn't frozen.
