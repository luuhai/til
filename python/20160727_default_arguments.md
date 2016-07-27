### Function's default arguments

In Python, a function's default arguments' values are calculated when the function is defined, not when it executes.

```python
def test(a=[]):
    a.append(1)
    return a

test() # => [1]
test() # => [1, 1]
test() # => [1, 1, 1]
```

We can check that the `test` function actually returns the same object everytime.

```python
id(test()) # => 140348801680016
id(test()) # => 140348801680016
```

To avoid that situation, we can use a placeholder value instead of modifying the default value. `None` is a common value

```python
def test(a=None):
    if a is None:
        a = []
    # modify a here
```
