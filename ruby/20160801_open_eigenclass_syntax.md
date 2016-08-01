### Open an object's eigenclass

To open an object's eigenclass (singleton class) inside its definition block, you can use `class << self` syntax. These 3 syntaxes have the same effect.

```ruby
class Foo
  class << self
    def method_one
      print 'One'
    end
  end
end

class Foo
  def self.method_two
    print 'Two'
  end
end

def Foo.method_three
  print 'Three'
end

Foo.method_one   # => One
Foo.method_two   # => Two
Foo.method_three # => Three
```
