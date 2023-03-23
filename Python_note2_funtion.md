# 函数

[toc]

## 调用函数

需要调用python内置的函数时，需要知道函数的名称以及需要输入的参数即可调用

还有一个较为实用的内置函数，数据类型转换函数

函数名是一个指向函数对象的引用，可以将函数名赋给一个对象，相当于给函数起别名，以下给出相应的案例：

```python
###这是一些类型转化函数
>>> int('123')
123
>>> int(12.34)
12
>>> float('12.34')
12.34
>>> str(1.23)###转成字符串
'1.23'
>>> str(100)
'100'
>>> bool(1)
True
>>> bool('')
False

###这是将函数名赋予给一个变量的例子
>>> a = abs # 变量a指向abs函数
>>> a(-1) # 所以也可以通过a调用abs函数
1
```

## 定义函数

除了内置函数，也可以自己定义函数，以绝对值函数为例子：

```python
def my_abs(x):
    if x >= 0:
        return x
    else:
        return -x

```
`from abtest import my_abs`可以调用保存在 abtest.py 的 my_abs 函数

对于还没想好怎么写的函数，可以先用pass当成占位符号，就占个位子，执行的时候会跳过这里

内置函数能够检查出不恰当的参数并且报错，在自定义的函数中实现该功能：

```python
def my_abs(x):
    if not isinstance(x, (int, float)):
        raise TypeError('bad operand type')
    if x >= 0:
        return x
    else:
        return -x
```

函数也可以返回多个值？其实只是返回一个tuple：

```python
import math

def move(x, y, step, angle=0):
    nx = x + step * math.cos(angle)
    ny = y - step * math.sin(angle)
    return nx, ny

>>> x,y = move(100, 100, 60, math.pi / 6)
>>> print(x,y)
151.96152422706632, 70.0

>>> r = move(100, 100, 60, math.pi / 6)
>>> print(r)
(151.96152422706632, 70.0)
```

