### include vs extend

* `include` adds module's methods as instance methods.
* `extend` adds module's methods as class methods.

    ```ruby
    module FirstModule
      def foo
        puts 'foo'
      end
    end

    module SecondModule
      def bar
        puts 'bar'
      end
    end

    class Test
      include FirstModule
      extend SecondModule
    end

    Test.new.foo # => foo
    Test.bar # => bar
    ```
