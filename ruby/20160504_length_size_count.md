### length, size and count

In ruby, there're 3 methods to calculate number of elements of an `Enumerable` object, called `length`, `size` and `count`.
* `size` is alias of `length`. Normally people use `size` with `Enumerable` objects, and `length` with `String`.
* `length` usually runs in `O(1)` time.
* `count` is usually used with a block or an argument and will return the number of matches in an `Enumerable`.
* `count` needs to traverse the enumerable object, which is not particularly fast.
* Some class (like `Array`) implement an optimized version of `count` in terms of length, but many don't.
