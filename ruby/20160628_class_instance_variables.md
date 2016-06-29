### Class and instance variables

* Instance variables always belong to `self`.
* Class variables aren't class-scoped variables, but class-hierarchy-scoped variables, which means they're shared between a class and all of its superclasses and subclasses

    ```ruby
    class Parent
      @@value = 100
    end

    class Child < Parent
      @@value = 200
    end

    class Parent
      puts @@value #==> 200
    end
    ```
