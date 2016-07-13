### length, size and count

There are differences between `length`, `size` and `count` on `ActiveRecord::Relation`
* `count` always performs a count query
* `length` will load up the records, and call `length` on the resulting array
* `size` will do a `count` the the records have not been loaded, and do a `length` if they have.
