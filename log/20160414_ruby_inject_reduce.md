# Calculate sum of an array the ruby way

* With `inject`
    ``` ruby
    [1,2,3].inject(0) { |sum, num| sum + num }
    ```
  or shorter
    ``` ruby
    [1,2,3].inject(:+)
    ```
  but be careful
    ``` ruby
    [].inject(:+) # => nil
    [].inject(0, :+) # => 0
    ```
* With `reduce`
    + `reduce` is just an alias of `inject`
    + Rubocop will give you a warning if you use `inject` instead of `reduce`
    + map/reduce style:
        ``` ruby
        array.map(&:to_i).reduce(:+)
        ```
* `inject`, `reduce`, `fold`, `accumulate`, `compress` are all synonynous as a class of [folding function](https://en.wikipedia.org/wiki/Fold_(higher-order_function))
