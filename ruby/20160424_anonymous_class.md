### Anonymous class

You can create an `anonymous class` using `Class.new` and add instance methods or class methods at the time you create it by appending a code block after the call to `new`

```ruby
c = Class.new do
  def say_hello
    puts "Hello!"
  end

  def self.say_goodbye
    puts "Goodbye!"
  end
end

c.new.say_hello # => "Hello!"
c.say_goodbye # => "Goodbye!"
```
