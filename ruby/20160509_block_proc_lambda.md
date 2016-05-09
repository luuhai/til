### block, proc and lambda

* A `proc` is an instance of `Proc` class. A `block` is just a syntax

    ```ruby
    p = Proc.new { puts 'this is a proc' }
    p.call # => this is a proc
    { puts 'this is a block' } # => syntax error
    b = { puts 'this is a block' } # => syntax error
    ```

* You can only pass at most one block to a method. In contrast, you can pass multiple procs to methods.

    ```ruby
    def multiple_procs(proc1, proc2)
      proc1.call
      proc2.call
    end

    a = Proc.new { puts "First proc" }
    b = Proc.new { puts "Second proc" }

    multiple_procs(a,b)
    # => First proc
    # => Second proc
    ```

* A `lambda` is also an instance of `Proc` class.

    ```ruby
    l = lambda { puts "this is a lambda" }
    l.class # => Proc
    ```

* `lambda` checks the number of arguments, while `proc` does not.

    ```ruby
    l = lambda { |x| puts x }
    p = proc { |x| puts x }

    l.call # => ArgumentError
    l.call(2) # => 2
    l.call(2,3) # => ArgumentError

    p.call # => nil
    p.call(2) # => 2
    p.call(2,3) # => 2
    ```

* `lambda` and `proc` treats the `return` differently.

    ```ruby
    def lambda_test
      l = lambda { return }
      l.call
      puts 'hihihi'
    end

    def proc_test
      p = proc { return }
      p.call
      puts 'huhuhu'
    end

    lambda_test # => hihihi
    proc_test # => nil
    ```

