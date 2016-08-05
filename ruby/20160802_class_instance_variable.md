### Class instance variables

* `Class instance variables` is instance variables of object class. They're defined at class level.
* Differ with normal class variables, class instance variables are not shared with subclasses

```ruby
class Person
  @count = 0

  def initialize
    self.class.count += 1
  end

  def self.count
    @count
  end

  def self.count=(value)
    @count = value
  end
end

class Worker
  @count = 0
end

8.times { Person.new }
4.times { Worker.new }

Person.count # => 8
Worker.count # => 4
```

#### Use case

```ruby
module DogMixin
  class << self
    def included(base)
      base.extend ClassMethods
    end
  end

  module ClassMethods
    def assign(*names)
      # @dogs is bound to the EACH DogOwner subclass
      @dog_names = names
    end

    def dog_names
      # @dogs is bound to the EACH DogOwner subclass
      @dog_names
    end
  end
end

class Owner
  include DogMixin
end

class Nerd < Owner
  assign :r2d2, :posix
end

class Emo < Owner
  assign :bill, :tom
end

class Hater < Owner
end

p Nerd.dog_names
# => [:r2d2, :posix]

p Emo.dog_names
# => [:bill, :tom]

p Hater.dog_names
# => nil
```

#### Links
* http://thoughts.codegram.com/understanding-class-instance-variables-in-ruby/
