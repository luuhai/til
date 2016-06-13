### Double bang

Double bang (!!) is used to convert a value to boolean. Basically it turns `nil` or `false` to `false`, and any other value to `true`. It is often used with `?` methods, when you don't want to return a whole large object.

  ```ruby
  def logged_in?
    !!@current_user
  end
  ```
