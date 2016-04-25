### load vs require

* `require` reads and parses files only once, when they were referenced for the first time. Files is saved to the memory and run in a given place.
* `load` reads and parse files every time you call `load`.

For example, here we have the module file `test.rb`

  ```ruby
  module Test
    def foo
      puts 1
    end
  end
  ```

And the main file

  ```ruby
  while true
    load 'test.rb' # or require_relative 'test'

    class A
      include Test
    end

    `sleep 2`
    A.new.foo
  end
  ```

Run the main file with `load`

  ```
  1
  1
  1
  1
  2 # change the output of foo to 2
  2
  2
  ```

and with `require`

  ```
  1
  1
  1
  1 # still the same even if you change the output of foo
  1
  1
  ```
