### Error message in Rails

* If you want error message starts with input's name, use `full_error`, otherwise use `error`
    + model

        ```ruby
        validates :email, presence: true, length: { maximum: 60 },
                  format: { with: valid_email_regex, message: 'Invalid' }
        ```

    + view

        ```ruby
        f.full_error :email # => "Email Invalid"
        f.error :email # => "Invalid"
        ```

* You can specify error message in validations using symbol.
    + locales yaml file

        ```yaml
        [lang]:
          activerecord:
            errors:
              messages:
                bad_email: "just ain't right"
        ```

    + model

        ```ruby
        validates :email, presence: true, length: { maximum: 60 },
                  format: { with: valid_email_regex, message: :bad_email }
        ```
