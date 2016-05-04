### Block's scope

* Blocks share local scope with the code that precedes them

    ```ruby
    def some_method
      x = 100
      1.times do
        puts "x is: #{x}"
        x = 200
        puts "now x is: #{x}"
      end
      puts "outside x is: #{x}"
    end

    some_method
    # x is: 100
    # now x is: 200
    # outside x is: 200
    ```

* These local variables are not the same as block's parameters

    ```ruby
    def some_method
      x = 100
      1.times do |x|
        puts "inside x is: #{x}"
      end
      puts "outside x is: #{x}"
    end

    some_method
    # inside x is: 1
    # outside x is: 100
    ```

* You can define block's own local variable using `;`

    ```ruby
    def some_method
      x = 100
      1.times do |i;x|
        x = i * 5
        puts "inside x is: #{x}"
      end
      puts "outside x is: #{x}"
    end

    some_method
    # inside x is: 1
    # outside x is: 100
    ```
