### Namedtuple

To create a new `namedtuple`, you use `namedtuple()` method, with 2 arguments, first is the tuple's name and second is a string represents its fields' names, seperated by spaces (you can use a `list` or a `tuple` contains all fields name too, but don't use a `set` or a `dict`. It works, but not in the way you expect, cause `set` and `dict` are unordered.)

```python
from collections import namedtuple

Person = namedtuple('Person', 'name age')

lam = Person('Lam', 26)
lam.name # => 'Lam'
lam.age # => 26

Duck = namedtuple('Duck', set(['bill', 'tail']))
```

* A `namedtuple` is immutable, which means you cannot reassign fields' values or add more fields.
* [Instances of named tuples use no more space than regular tuples](https://twitter.com/raymondh/status/524660721968107521)
* You can create a `class` with immutable attributes by inherit from a namedtuple

```python
class Duck(namedtuple('_Duck', 'bill tail')):
    pass

duck = Duck('red', 'long')
duck.bill # => 'red'
duck.tail # => 'long'

duck.bill = 'blue' # => AttributeError
```
