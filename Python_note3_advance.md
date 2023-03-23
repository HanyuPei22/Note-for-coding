# Slice
## To get element from list and tuple

```python
'''
These are different operations for taking slices of lists
or tuples.
'''

L = ['Michael', 'Sarah', 'Tracy', 'Bob', 'Jack']

>>> L[:3]
['Michael', 'Sarah', 'Tracy']

>>> L[1:3]
['Sarah', 'Tracy']

>>> L[-2:]
['Bob', 'Jack']
>>> L[-2:-1]
['Bob']

>>> L = list(range(100))
>>> L
[0, 1, 2, 3, ..., 99]

>>> L[-10:]
[90, 91, 92, 93, 94, 95, 96, 97, 98, 99]

>>> L[::5]
[0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60, 65, 70, 75, 80, 85, 90, 95]

>>> L[:10:2]
[0, 2, 4, 6, 8]


```

## Iteration

use `for` loop to traversal the `list` or `tuple` -----Iteration

In python, for loop can be used on any object that is iterable;

```python
>>> d = {'a': 1, 'b': 2, 'c': 3}
>>> for key in d:
...     print(key)
...
a
c
b
```
因为`dict`的存储不是按照`list`的方式顺序排列，所以，迭代出的结果顺序很可能不一样。

默认情况下，`dict`迭代的是`key`。如果要迭代`value`，可以用`for value in d.values()`，如果要同时迭代`key`和`value`，可以用`for k, v in d.items()`。

loop for character:
```python
>>> for ch in 'ABC':
...     print(ch)
...
A
B
C
```

To figure out whether an object is iterable:
```python
>>> from collections.abc import Iterable
>>> isinstance('abc', Iterable) # str是否可迭代
True
>>> isinstance([1,2,3], Iterable) # list是否可迭代
True
>>> isinstance(123, Iterable) # 整数是否可迭代
False
```
To use `for` loop in sub tag:

```python
'''
Python内置的enumerate函数可以把一个list变成索引-元素对，
这样就可以在for循环中同时迭代索引和元素本身：
'''
>>> for i, value in enumerate(['A', 'B', 'C']):
...     print(i, value)
...
0 A
1 B
2 C
```

## List Comprehension

To generate `list[1*1,2*2,3*3,...,9*9,10*10]`, it is too complicate to write :
```python
>>> L = []
>>> for x in range(1, 11):
...    L.append(x * x)
...
>>> L
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

In python we can:
```python
>>> [x * x for x in range(1, 11)]
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

This trick help us produce shorter code, such as:
```python
>>> [x * x for x in range(1, 11) if x % 2 == 0]
[4, 16, 36, 64, 100]

>>> [m + n for m in 'ABC' for n in 'XYZ']
['AX', 'AY', 'AZ', 'BX', 'BY', 'BZ', 'CX', 'CY', 'CZ']
```

在一个列表生成式中，`for`前面的`if...else`是表达式，而`for`后面的`if`是过滤条件，不能带`else`.

```python
>>> d = {'x': 'A', 'y': 'B', 'z': 'C' }
>>> [k + '=' + v for k, v in d.items()]
['y=B', 'x=A', 'z=C']

>>> L = ['Hello', 'World', 'IBM', 'Apple']
>>> [s.lower() for s in L]
['hello', 'world', 'ibm', 'apple']

>>> [x for x in range(1, 11) if x % 2 == 0]
[2, 4, 6, 8, 10]

###This is wrong###
>>> [x if x % 2 == 0 for x in range(1, 11)]
  File "<stdin>", line 1
    [x if x % 2 == 0 for x in range(1, 11)]
                       ^
SyntaxError: invalid syntax

>>> [x if x % 2 == 0 else -x for x in range(1, 11)]
[-1, 2, -3, 4, -5, 6, -7, 8, -9, 10]
```

## Generator

Sometime lists get too large, and only several elements we will use in the future. Generator helps us generate elements while looping.

This is how it looks:
```python
>>> L = [x * x for x in range(10)]
>>> L
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
###use () instead of [], then we have a generator###
>>> g = (x * x for x in range(10))
>>> g
<generator object <genexpr> at 0x1022ef630>
```
Then we can do this:
```python
>>> g = (x * x for x in range(10))
>>> for n in g:
...     print(n)
... 
```

This is a function that generates Febonacci series:
```python
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        print(b)
        a, b = b, a + b
        n = n + 1
    return 'done'
```
`a, b = b, a + b` is equivalent to
```python
t = (b, a + b) # t是一个tuple
a = t[0]
b = t[1]
```
And this will transform the function into a generator:
```python
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        yield b# change print() to yield()
        a, b = b, a + b
        n = n + 1
    return 'done' 
```

$a+b$
