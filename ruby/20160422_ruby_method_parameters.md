### Method parameters

* Ruby tries to assign values to as many variables as possible. And the sponge parameters get the lowest priority: if the method runs out of arguments after it's performed the assignments of required arguments, the the sponge parameter ends up as an empty array.

    ```ruby
    def mix_args(a, b, *c, d)
      puts "Arguments"
      p a, b, c, d
    end

    mixed_args(1,2,3,4,5)

    # Arguments:
    # 1
    # 2
    # [3, 4]
    # 5
    ```
The required arguments both before and after *c get taken care of before *c does.

* Argument assignments' order of priority: required arguments are handled first, then the default-valued optional argument, and then the sponge.

    ```ruby
    def mix_args(a, b=1, *c, d)
      puts "Arguments"
      p a, b, c, d
    end

    mixed_args(1,2)

    # Arguments:
    # 1
    # 1
    # []
    # 3
    ```

* You can't do these things:

    ```ruby
    def mix_args(a, *b, c=1)
    def mix_args(a, b=1, c, d=1)
    def mix_args(a, b=1, c, *d)
    def mix_args(*a, *b)
    ```
