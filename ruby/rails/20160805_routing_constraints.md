### Routing Constraints

#### HTTP Verb Constraints

* Routes /properties to properties controller's index action and contrain it to GET and POST requests

```ruby
match 'properties', to: 'properties#index', via: [:get, :post]
```

* Constrain it to every HTTP verb

```ruby
match 'properties', to: 'properties#index', via: :all
```

#### Segment Constraints

* Enforce a format for a given parameter

```ruby
get 'properties/:slug', to: 'properties#show', constraints: { slug: /[a-z]+\.\d+/ }
# /properties/alex.9 => valid
# /properties/alex   => invalid
```

#### Request Based Constraints

* Constrain a route using any method the `Request` object responds to: `ip`, `useragent`, `subdomain`...
* With this constrain, your applicaion would serve the dashboard page from `staging.yourapp.com/dashboard`, but would reject requests to `www.yourapp.com/dashboard`

```ruby
get 'dashboard', to: 'dashboard#index', constraints: { subdomain: 'staging' }
```

* Or you can serve a different homepage to a user depending on the devide they're requesting the page from

```ruby
root 'iphone#index', constraints: lambda { |req| req.env["HTTP_USER_AGENT"] =~ /iPhone/ }
root 'web#index'
```

* The `constraints` method can be called with a block containing all of the routes you'd like to constrain

```ruby
constraints(subdomain: ["admin", "staging"]) do
  match 'properties', to: 'properties#show', via: :get
  match 'properties', to: 'properties#create' via: :post
  match 'dashboard', to: 'main#dashboard', via: :get
end
```

* You can create your own custom constraints by providing an object that respond to a `matches?` method, which returns `true` if a request should be given access to a route, or `false` if the request should be rejected.

```ruby
# iphone_admin.rb
class IphoneAdmin
  def self.matches?(request)
    request.env["HTTP_USER_AGENT"] =~ /iPhone/ && request.subdomain == "admin"
  end
end

# routes.rb
constraints(IphoneAdmin) do
end
```

#### Use case

```ruby
get 'products/:gender(/:brand)(/:sale)', to: 'products#show', constraints: ProductConstraint.new
```

We want the method to check whether or not the given `gender` parameter is a valid gender, the given `brand` is an existing one and if `sale` is set. If the `brand` or `sale` parameter is empty, we still want to route the match, falling back to no brand or sale filter. This means the page should be vailable through the following paths:

```
1. /products/male
2. /products/female
3. /products/male/sale
4. /products/female/sale
5. /products/male/:brand
6. /products/female/:brand
7. /products/male/:brand/sale
8. /products/female/:brand/sale
```

Here is the constraints class

```ruby
class ProductConstraint
  def matches?(request)
    params = request.path_parameters

    return false unless %w(male female).include? params[:gender]

    sale = params[:sale]
    if 'sale' == params[:brand]
      sale = params[:brand]
      request.path_parameters.delete :brand
    elsif params[:brand].present?
      return false unless brands.include? params[:brand]
    end

    request.path_parameters[:sale] = ('sale' == sale)

    true
  end

private

  def brands
    Rails.cache.fetch(:brand_slugs, expires_in: 1.hour) { Brand.pluck(:slug) }
  end
end
```

#### Links

* http://www.yanted.com/2014/08/27/rails-constraints-custom-routes/
* http://building.vts.com/blog/2015/09/08/zen-and-the-art-of-rails-routing-constraints/
