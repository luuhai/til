### Merge two arrays

There are several ways to merge two arrays in Ruby

```ruby
a1 = [1,2,3]
a2 = [4,5,6]

a1.concat a2
a1 + a2             # create a new array
a1.push *a2
a2.unshift(*a1)     # a2 is the receiver
a1[a1.length, 0] = a2
a1[a1.length..0] = a2
a1.insert(a1.length, *a2)
(a1 << a2).flatten!
(a1 << a2).flatten  # create a new array
```
