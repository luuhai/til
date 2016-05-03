### Curly braces vs do-end

The difference between the two ways of delimiting a code block is a difference in precedence

```ruby
puts [1,2,3].map { |n| n * 2 }
# 2
# 4
# 6
# => nil

puts [1,2,3].map do |n| n * 2 end
# #<Enumerator:0x0000000496b870>
# => nil
```

The first `puts` statement is interpreted like this

```ruby
puts ([1,2,3].map { |n| n * 2 }
```

And the second is interpreted like this

```ruby
puts([1,2,3].map) do |n| n * 2 end
```
