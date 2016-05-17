### Custom database's table name and primary key

To set up custome table name and primary key columns for an ActiveRecord model, using `ActiveRecord::Base.table_name=` and `ActiveRecord::Base.primary_key=` methods

  ```ruby
  class Product < ActiveRecord::Base
    self.table_name = 'my_products'
    self.primary_key' = 'product_id'
  end
  ```
