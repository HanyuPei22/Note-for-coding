# Project Oriented Programming

## 作用域

形如`_xxx` or `__xxx`：非公开变量，不能直接引用

形如`_xxx_` ：特殊变量，可以引用

Example:

```python
def _private_1(name):
    return 'Hello, %s' %name

def _private_2(name):
    return 'Hell0, %s' %name

def greeting(name):
    if len(name)>3 :
        return _private_1(name)
    else:
        return _private2_(name)
```

Outside users don't have to know about private's detail.

## OOP

从面相流程（以前的），转变为面相对象的；

以学生成绩表为案例：
```python
#take student as a object with property:name and score
class Student(object):
# __int__ has 2 "_" both sides
    def __int__(self,name,score):
        self.name = name
        self.score = score

    def print_score(self):
        print('%s,%s' % self.name,self.score)
```

The class can play a role of paradigm, therefore when building a instance we should fill in some necessary properties like this:

```python
class Student(object):
    
    def __int__(self,name,score):
        self.name = name
        self.score = score
```

If we use `__int__`, we __cannot__ deliver empty parameter, instead we should create instance like this:
`bart = Student('Bart',98)`

First parameter of `__int__` is __always__ `self`, which means instance itself and allows us attach different properties to `self`.

OOP's important significance would be data encapsulation,which means we define a function in class `Student` to access the data we need.

Example of data encapsulation:
```python
class Student(object):

    def __int__(self,name,score):
        self.name = name
        self.score = score

    def print_score(self)#this is called method
        print('%s,%s' % (self.name,self.score))
```

to define a method, everything is same with defining function except first parameter is self

## 访问限制

```python
class Student(object):

    def __int__(self,name,score):
        self.__name = name
        self.__score = score

    def print_score(self)#this is called method
        print('%s,%s' % (self.__name,self.__score))
```

then, we cannot access `.__name` and `.__score`

if we want to access, do:

```python
class Student(object):
    ...

    def get_name(self):
        return self.__name

    def get_score(self):
        return self.__score
``` 

One of the benefit is that we can check whether the input parameter is right.

```python
class Student(object):
    ...
    
    def set_score(self,score):
        if 0 <= score <= 100:
            self.__score = score
        else:
            raise ValueError('Bad score')
    
```

## 继承&多态

we can do:
```python
class Animal(object):
    def run(self):
        print('Animal is running...')

class Dog(Animal):
    pass

class Cat(Animal):
    pass

dog = Dog()
dog.run()

cat = Cat()
cat.run()

#Animal is running...
#Animal is running...
```

we can improve it by:
```python
class Dog(Animal):
    
    def run(self):
        print('Dog is running')

class Cat(Animal):
    
    def run(self):
        print('Cat is running')

#Output:
#Dog is running
#Cat is running
```