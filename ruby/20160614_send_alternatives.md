### `send`'s alternatives

To avoid conflict with other `send` methods, Ruby provides 2 alternatives for it:
* `__send__` which works exactly like `send`
* `public_send`, which only works with public methods

```ruby
class Test
  def foo
    puts 'foo'
  end

  private
    def bar
      puts 'bar'
    end
end

Test.new.__send__('foo') #==> 'foo'
Test.new.__send__('bar') #==> 'bar'
Test.new.public_send('bar') #==> NoMethodError
```
