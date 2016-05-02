# Assignment via attribute accessors

Be careful when using attribute accessors to assign value to an instance variable inside class definition

```ruby
class Foo
  attr_accessor :bar

  def initialize
    @bar = 1
  end

  def change
    bar = 2
  end
end

f = Foo.new
f.bar # => 1
f.change
f.bar # => 1
```

That because inside `change` method, ruby assumes `bar` is a local variable, not a method. If you want to use the accessor there, add `self`

```ruby
class Foo
  attr_accessor :bar

  def initialize
    @bar = 1
  end

  def change
    self.bar = 2
  end
end

f = Foo.new
f.bar # => 1
f.change
f.bar # => 2
```
