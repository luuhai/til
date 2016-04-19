### `include` vs `prepend`

* `include` inserts the module in the ancestors chain, right _above_ the including class itself.
  ```ruby
  module M1
    def my_method
    end
  end

  class C
    include M1
  end

  class D < C; end

  D.ancestors # => [D, C, M1, Object, Kernel, BasicObject]
  ```

* `prepend` inserts the module _below_ the including class.

  ```ruby
  class C2
    prepend M2
  end

  class D2 < C2; end

  D2.ancestors # => [D2, M2, C2, Object, BasicObject]
  ```
