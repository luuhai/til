### Anonymous class

You can create an `anonymous class` using `Class.new` and add instance methods at the time tou create it by appending a code block after the call to `new`

```ruby
c = Class.new do
  def say_hello
  puts "Hello!"
end

c.new.say_hello # => "Hello!"
```
