### Define class methods inside module

* If your module only consists of class methods, just use `extend ModuleName`

    ```ruby
    module Foo
      def some_method
        puts 'something'
      end
    end

    class Bar
      extend Foo
    end

    Bar.some_method # => something
    ```
* If your module have both class and instance methods

    ```ruby
    module Foo
      def self.included(base)
        base.extend(ClassMethods)
      end

      module ClassMethods
        def some_method
          puts 'something'
        end
      end
    end

    class Bar
      include Foo
    end

    Bar.some_method # => something
    ```
