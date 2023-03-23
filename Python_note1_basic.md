# Python 基础

[toc]

## 数据类型以及变量
### 数据类型
#### 整数：
    
    正常按照数字表达：

    比较大的数字可以加 “_”， 1000000000 == 10000_00_00
    "0x" 开头表示16进制    

#### 浮点数
注意科学计数法, which is

$1.23\times10^{-9}$ === $1.23e9$

#### 字符串
用单引号或者双引号扩起来，如果遇到字符串内部包含的单双引号，则应该：

` 'I\'m \"OK\"' `

用三个点输入多行内容：

```python
print('''line1
...line2
...line3''')
```

#### Bool
只有true和false两种值

    运算方式：and； or； not；
    分别对应：与；或；非；

### 变量
Python是动态语言，在定义变量时候不需要制定变量类型（静态语言则需要）。在处理这样一句时候：`a = 'abc'` python解释器进行如下动作：
   
    1.在内存中创建'abc' 字符串
    2.在内存中创建一个变量a，将其指向'abc'

常见案例：

```python
a = 'abc';
b = a; ##将变量b指向变量a所指向的数据
a = 'XYZ' ##变量a此时指向'XYZ'
print(b) ##最后输出结果是abc
```

## 字符串以及编码
计算机只可以处理数字，因此将各种语言字符对应到数字。ASCII对应的是英文，后来语言增多，诞生整合了各种语言的Unicode。区别在于ASCII采用一个字节，Unicode采用两个字节。但由于Unicode对英文字母采用两个字节编码造成了储存空间浪费，后来采用UTF-8编码（可变长编码），其中英文一个字节，汉字常用三个字节，生僻字符编码为4-6个字节。

计算机中，内存采用Unicode编码，保存到硬盘或者需要传输时候转换成UTF-8编码。

### 格式化字符串
采用如下格式化方式：
`'hi, %s, you have $%d'`
关于占位符：
| 占位符  | 替换内容     | 
| ----   | :----:     |
| %d     | 整数        |
| %f     | 浮点数      |   
| %s     | 字符串      | 
| %x     | 十六进制整数 | 

## List & tuple
### List
```python
>>>class = ['Michael','Bob','Tracy']
>>>class
 ['Michael','Bob','Tracy']

>>>class[0]
'Michael'
>>>class[-1]
'Tracy'
###the last index is len(class)-1###

>>>class.append('Adam')##添加元素
>>>class
['Michael','Bob','Tracy','Adam']

>>> class.insert(1, 'Jack')##指定位置插入元素
>>> class
['Michael', 'Jack', 'Bob', 'Tracy', 'Adam']

>>> class.pop()##删除列表末尾元素
'Adam'
>>> class
['Michael', 'Jack', 'Bob', 'Tracy']

>>> class.pop(1)##删除列表指定位置元素
'Jack'
>>> class
['Michael', 'Bob', 'Tracy']

>>> class[1] = 'Sarah'##修改列表指定位置元素
>>> class
['Michael', 'Sarah', 'Tracy']
```

### Tuple（元组）

tuple和list区别在于tuple，元组在初始化后无法修改

```python
>>> classmates = ('Michael', 'Bob', 'Tracy')

##只有一个元素的tuple定义后需要加一个逗号，避免产生歧义
>>> t = (1,)
>>> t
(1,)
##注：可以正常进行索引，但是无法修改包含的元素

###一个“可变”的元组：
>>> t = ('a', 'b', ['A', 'B'])
>>> t[2][0] = 'X'
>>> t[2][1] = 'Y'
>>> t
('a', 'b', ['X', 'Y'])
##tuple的不变体现在指向不变，这里tuple指向的list没有变化，但是list本身是可以变的##
```

## 使用dict和set
### dict
即字典，dictionary，某些语言称之为map，通过key-value键值对存储，查找速度快。
```python
###define a dict###
>>> d = {'Michael': 95, 'Bob': 75, 'Tracy': 85}
>>> d['Michael']
95

###通过key放入数据
>>> d['Adam'] = 67
>>> d['Adam']
67

###多次放入数据会把之前的数据挤掉
>>> d['Jack'] = 90
>>> d['Jack']
90
>>> d['Jack'] = 88
>>> d['Jack']
88

###由于key不存在时python报错，为了避免之，有以下两种方法

>>> 'Thomas' in d
False###in方法

>>> d.get('Thomas')
>>> d.get('Thomas', -1)
-1##get方法

###采用pop方法删除key，删除key后对应的value也删除
>>> d.pop('Bob')
75
>>> d
{'Michael': 95, 'Tracy': 85}

```
将dict和list相比较：

    1.dict查找、插入速度快，不会随着key增加而变慢
    2.占用较大内存，会浪费内存

注意，dict中的key需要采用不可变对象，比如字符串、整数等，不要采用list这种可变对象

### set
set是一组key的集合，key是不重复的因此重复的元素会被自动删除。
```python
###创建一个set，需要一个list作为输入集合
>>> s = set([1, 2, 3])
>>> s
{1, 2, 3}

###重复元素在set中自动被过滤
>>> s = set([1, 1, 2, 2, 3, 3])
>>> s
{1, 2, 3}

###通过add(key)方法可以添加元素到set中，可以重复添加，但不会有效果：
>>> s.add(4)
>>> s
{1, 2, 3, 4}
>>> s.add(4)
>>> s
{1, 2, 3, 4}

###通过remove(key)方法可以删除元素：
>>> s.remove(4)
>>> s
{1, 2, 3}

###set可以看成数学意义上的无序和无重复元素的集合，因此，两个set可以做数学意义上的交集、并集等操作
>>> s1 = set([1, 2, 3])
>>> s2 = set([2, 3, 4])
>>> s1 & s2
{2, 3}
>>> s1 | s2
{1, 2, 3, 4}
```

### 关于不可变对象的补充
对于不可变对象进行如下操作：
```python
>>> a = 'abc'
>>> a.replace('a', 'A')
'Abc'
>>> a
'abc'
###注意到这里a没有变，那么replace发挥了什么作用呢？

>>> a = 'abc'
>>> b = a.replace('a', 'A')
>>> b
'Abc'
>>> a
'abc'
```
**注意这里a是变量，'abc'是字符串对象。replace方法作用于字符串对象abc，产生效果是创造一个新的字符串'Abc'并且将其返回**


