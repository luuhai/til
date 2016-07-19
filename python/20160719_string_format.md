### String format

You can use `format()` to format values in a string

```python
print('{0:5d} {1:0.2f}'.format(1992, 10.566)) # 0:5d => format the first value right-aligned in a column of width 5
# => ' 1992 10.57'
print('{0:<5d} {1:0.2f}'.format(1992, 10.566)) # 0:<5d => format the first value left-aligned in a column of width 5
# => '1992  10.57'
```

From Python 2.7 you can omit the order number

```python
print('{:5d} {:0.2f}'.format(1992, 10.566))
# => ' 1992 10.57'
```
