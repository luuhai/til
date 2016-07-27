### Iterate with else

In Python you can use iterator (`for`, `while`) with `else` to check whether it has completed normally (i.e. no `break` call)

```python
numbers = [1, 3, 5]
position = 0
while position < len(numbers):
    number = numbers[position]
    if number % 2 == 0:
        print('Found even number', number)
        break
    position += 1
else:
    print('No even number found')

# ==> No even number found
```
