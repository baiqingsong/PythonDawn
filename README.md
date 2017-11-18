# Python的学习

* [python基础](#python基础)
    * [数据类型](#数据类型)
    * [print语句](#print语句)
    * [注释](#注释)
    * [变量](#变量)
    * [raw字符串和多行字符串](#raw字符串和多行字符串)
    * [Unicode字符串](#unicode字符串)
    * [运算符](#运算符)
    * [list](#list)
    * [tuple](#tuple)
    * [判断和循环](#判断和循环)
    * [dict和set](#dict和set)
    * [函数](#函数)
    * [切片](#切片)
    * [索引迭代](#索引迭代)
    * [列表](#列表)
* [python的进阶](#python的进阶)
    * [高阶函数](#高阶函数)
    * [map函数](#map函数)
    * [reduce函数](#reduce函数)
    * [filter函数](#filter函数)
    * [sorted函数](#sorted函数)
    * [返回函数](#返回函数)
    * [闭包](#闭包)
    * [匿名函数](#匿名函数)
    * [装饰器](#装饰器)
    * [模块](#模块)
    * [类](#类)
    * [继承](#继承)
    * [特殊方法](#特殊方法)


## python基础
[https://docs.python.org/2/library/functions.html](https://docs.python.org/2/library/functions.html "官网地址")

### 数据类型
整数，浮点数，布尔值（True，False），空值（None）

### print语句
print语句可以向屏幕上输出指定文字，多个字符串可以用`,`（逗号）隔开

### 注释
Python中的注释用`#`符号开头

### 变量
Python中的变量不需要关键字，只需要变量名和赋值就可以了。不过变量名还是要区分大小写和书写规范。
变量本身类型不固定的语言称之为动态语言。

### raw字符串和多行字符串
如果一个字符串中包含多个需要转义的字符，对每个字符都进行转义很麻烦，
所以Python为了避免这种麻烦，在字符串前加上个前缀`r`，表示这是个raw字符串，
里面的字符就不需要转义了。  
但是r'...'表示法不能表示多行字符串，也不能表示包含`'`和`"`的字符串  
如果要表示多行字符串可以'''...'''  
还可以在多行字符串前面添加前缀`r`，这样就把多行字符串也变成了一个raw字符串

### Unicode字符串
以Unicode表示的字符串用u'...'表示  
多行：u'''...'''  
raw+多行：ur'''...'''  
如果中文字符串在Python环境瞎遇到了UnicodeDecodeError这个错误，需要在第一行添加注释
# -*- coding: utf-8 -*-
作用时搞事Python解释器，用UTF-8编码读取源代码。

### 运算符
运算符and，or，not  
布尔类型还可以与其他数据类型做and，or和not运算，例如：
```
    a = True
    print a and 'a=T' or 'a=F'
```
这段代码返回的结果不再时一个布尔类型而是字符串'a=T'  
1.在计算`a and b`时，如果a时False，则根据与运算法则，整个结果必定时False，因此返回a；
如果a时True，则整个计算结果必定取决与b，因此返回b。  
2.在计算`a or b`时，如果a时True，则根据或运算法则，整个计算结果必定为True，因此返回a；
如果a时False，则整个计算结果必定取决于b，因此返回b。  
在Python中，把`0`，`空字符串''`，和`None`看成False，其他数字和非空字符串都看成True。

### list
list是一种有序的集合，用`[]`表示  
空list：[]  
list集合中可以存放不同类型的数据  
取出第一个对象可以用集合名称L[0] 来表示  
需要注意的是越界会报IndexError错误。  
可以用L[-1]来表示最后一个元素  
倒数第二`-2`，倒数第三`-3`，需要注意的是也不要越界问题。  
添加元素：append方法或者insert方法  
append方法是加到最后，insert两个参数，第一参数是索引，加到的位置。  
删除元素：pop方法  
默认删除最后一个元素，并且返回元素本身，也可以传索引参数，删除位置上的元素，并且返回元素本身  

### tuple
tuple是另一种有序的列表，译为“元组”。tuple一旦创建完毕，就不能修改了。  
tuple用括号`()`表示  
tuple不能添加，删除和替换。所以tuple是不变的，但是需要注意的是不变指的是指向。
例如tuple里面有个指向list的元素，我们可以改变list里面的值，因为指向的还是这个list。
当然要是想让所有的值都不变，可以将tuple中的list集合改成tuple类型，嵌套就可以了。  
需要注意的是：用`()`既可以表示tuple，又代表括号，所以，氮元素tuple要多加一个`,`，例如：
```
(1,)
```
多个元素最后的`,`加不加效果一样  

### 判断和循环
if语句：if后直接加表达式，然后用`:`表示代码块开始  
Python代码的所经规则。具有相同缩进的代码被视为代码块。注意不能将4个空格和Tab键混用。
如果有else，要和if的缩进一样，并且else后加`:`表示代码块开始  
Python中的else if写成`elif`  

for循环，如果遍历list集合
```
L = ['h', 'e', 'l', 'l', 'o']
for name in L:
    print name
```
这里的name变量是在for循环中定义的，意识是一次取出list集合中的每个元素，并且把元素赋值给name。  

### dict和set
dict表示带键值对的集合用`{}`表示，里面按照key:value写出  
可以用len()来计算大小  
取出元素可以直接dict[key]，但是key如果不存在，会出现KeyError错误。  
为了避免KeyError错误，可以用in操作符
```
if 'h' in dict:
    print dict['h']
```
还可以：
```
print dict.get('h')
```
如果存在则返回对应的值，如果不存在则返回None  
dict的第一个特点是查找速度快，无论是10个元素还是10万个元素的查询速度都是一样的，
而list的查找速度随着元素的个数增加而逐渐下降。
不过dict的缺点是占用的内存大，会浪费很多内容，而list正好相反。
dict的第二个特点是存储的键值对没有顺序，打印出来的是无序的结果。
dict的第三个特点是作为key的元素必须不可变，例如字符串，整数等，但是list不能作为key。  
dict的新增和更新直接赋值就可以了。  
dict的循环
```
for key in dict
    print key
```
当然，也可以根据key获取到value


set持有一系列的元素，但是set的元素没有重复，并且是无序的。  
创建set的方式是调用set()并传入一个list，list的元素将作为set的元素：
```
s = set(['h', 'e', 'l', 'l', 'o'])
```
判断元素是否存在可以用`in`操作符  
set的特点是无序的，唯一的，所以保存依然是不可变元素。  
当然遍历也和list相似
```
for name in s:
   print name
```
set的新增：add()方法
set的删除：remove()方法  
如果remove的元素不存在则会报KeyError错误，所以remove方法前需要先判断。  

### 函数
定义一个函数要用def关键字，后面依次函数名，括号，括号中的参数和冒号，然后函数体，最后return。
注意的是没有返回值是return None,可以简写成return  
Python可以返回多个值，其实质是tuple，括号省略后的显示。  
Python的函数中可以有默认参数，直接给参数赋值，需要注意的是：
默认参数智能定义在必需参数的后面。  
如果想让一个函数能接收任意个参数，可以定义为：
```
def fn(*args):
    print args
```
可变参数名字前面有个`*`符号，我们可以传入0个，1个或者多个参数给可变参数。  
其实质就是Python解释器把传入的一组参数组装成一个tuple传递给可变参数。   

### 切片
为了方便list获取元素  
```
L[0:3]
L[:3]
```
从索引0开始取，知道索引3为止，但不包括索引3.如果是从0开始，0可以省略  
```
L[:]
```
可以表示赋值出一个新的list
还可以传第三个参数，表示每N个取一个
```
L[::2]
```
这个表示每两个元素取出一个来  
切片的对象除了list也可以是tuple，只不过tuple取出后还是tuple.  
当然切片也可以从后面去，用-1，-2表示，例如：
```
L[-2:]
```
```
L[-2:-1]
```
上面的这两个是不同的，上面的取出是倒数两个元素，后面的那个取出的是倒数第二个元素，是一个元素。  
字符串也可以做切片操作，例如：
```
'ABCDEFG'[:3]
```
值应该是'ABC',相当于字符串的截取。更加方便。

### 索引迭代
如果我们想在for循环的时候不仅仅取出值，还想取出对应的索引，我们利用enumerate方法
```
for index, name in enumerate(L):
    print index,name
```
enumerate方法取出的相当于两个元素的tuple,相当于(index, element)形式。  
dict迭代中同时取出key和value方法：
```
for key, value in d.items():
    print key,value
```
items()有一个对应的iteritems()方法，
iteritems不把dict转换成list，而是在迭代过程中不断给出tuple，
所以，iteritems不占用额外的内存。

### 列表
range方法可以直接生成数字的集合，例如
```
range(1,10)
```
此句的结果是[1, 2, 3, 4, 5, 6, 7, 8, 9]  
如果想生成[1*1, 2*2, 3*3, ..., 10*10]  
```
[i * i for i in range(1, 11)]
```
这种写法就是Python特有的列表的生成式，利用列表生成式，可以非常简介的代码生成list  

可以通过一个复杂的列表生成式把它变成一个HTML表格
```
tds = ['<tr><td>%s</td><td>%s</td></tr>' % (name, score) for name, score in d.iteritems()]
print '<table>'
print '<tr><th>Name</th><th>Score</th>'
print '\n'.join(tds)
print '</table>'
```
注：字符串可以通过%进行格式化，用指定的参数替代%s。
字符串的join()方法可以把一个list拼接成一个字符串。  
把打印出来的结果保存一个html文件，可以看到浏览器中的效果：
```
<table border="1">
<tr><th>Name</th><th>Score</th><tr>
<tr><td>Lisa</td><td>85</td></tr>
<tr><td>Adam</td><td>95</td></tr>
<tr><td>Bart</td><td>59</td></tr>
</table>
```
条件过滤
```
[i * i for i in range(1, 11) if i % 2 == 0]
```
打印出来的结果[4, 16, 36, 64, 100]  
for循环嵌套
```
[m + n for m in 'ABC' for n in '123']
```
上面的结果和编译成下面的这样：
```
L = []
for m in 'ABC':
   for n in '123':
       L.append(m + n)
```

## python的进阶

### 高阶函数
高阶函数是将函数当作参数的函数例如：
```
def add(x, y, f):
    return f(x) + f(y)
```
此函数中x和y是普通参数，f是函数，而add是高阶函数  

### map函数
map()是Python内置的高阶函数，它接收一个函数f和一个list，
并通过把函数f一次作用在list的每个元素上，得到一个新的list并返回。  
例如：将list[1, 2, 3, 4]中每个元素做平方处理
```
def f(x):
    return x * x
print map(f, [1, 2, 3, 4])
```
map函数不改变原有的list，而是返回一个新的list。  

### reduce函数
reduce函数是Python内置的一个高阶函数，接收一个函数f和一个list，
reduce函数传入的函数f必须接收两个函数，reduce对list的每个元素反复调用函数f，并返回最终结果值。
```
def f(x, y):
    return x + y
print reduce(f, [1, 2, 3, 4])
```
返回的结果是10，是先前两个元素调用f函数相加，然后结果和第三个元素调用f函数继续相加，
然后继续。。。最后和最后的一个元素调用f函数相加  

### filter函数
filter函数是Python内置的一个高阶函数，传函数f和list两个参数，
函数f的作用是对每个元素进行判断，返回True和False，
filter根据判断结果自动过滤掉不符合条件的元素，返回由符合条件元素组成的新list。
```
def f(x):
    return x % 2 == 1
print filter(f, [1, 2, 3, 4, 5, 6, 7, 8, 9])
```
此函数的作用是删除偶数，保留基数。  
例如，非空选择
```
def is_not_empty(x):
    return s and len(s.strip()) > 0
filter(is_not_empty, ['h', 'e', 'l', 'l', 'o', ' ', None])
```
此函数是筛选出非空的元素，其中strip()是取出空白符，可传参数，删除首位参数字符。  

### sorted函数
sorted函数是Python中的一个高阶函数，可以接收一个需要排序的list，默认是从小到大，
如果要自定义排序方式，可以传入第二个函数参数  
```
def reversed_cmp(x, y):
    if x > y:
        return -1
    if x < y:
        return 1
     return 0
 print sorted([1, 2, 3, 4], reversed_cmp)
```

### 返回函数
Python的函数不但可以返回interesting，str，list，dict等数据类型，还可以返回函数。  
```
def calc_sum(lst):
    def lazy_sum():
        return sum(lst)
    return lazy_sum
f = calc_sum([1, 2, 3, 4])
```
上面的调用calc_sum函数并不返回集合相加的结果，而是返回一个函数，
如果想要list相加的结果需要调用f()。  
注：返回函数目的是为了延迟计算。  

### 闭包
内层函数引用了外层函数的变量（参数也算是变量），然后返回内层函数的情况，称为闭包。  

### 匿名函数
匿名函数用关键字lambda表示，格式为lambda 参数:表达式  
匿名函数有个限制，就是智能有一个表达式，不写return，返回值就是该表达式的结果  
```
map(lambda x: x * x, [1, 2, 3, 4])
```
返回的结果是[1, 4, 9, 16]  

### 装饰器
decorator是Python的一个高阶函数，它接收一个函数作为参数，然后返回一个新的函数。  
使用decorator用Python提供的`@`语法，这样可以避免手动编写f=decorate(f)这样的代码。  
```
def log(f):
    def fn(**args, **kw):
        print 'call ' + f.__name__ + '()...'
        return f(**args, **kw)
    return fn
@log
def factorial(n):
    return reduce(lambda x,y: x * y, range(1, n + 1))
print factorial(10)
```
@log表示修饰下面方法，目的是给之后的方法加一句打印方法名的作用。  
如果需要装饰的时候传递参数，那么需要在原有的基础上再次嵌套一层装饰。
```
def log(prefix):
    def log_decorator(f):
        def wrapper(**args, **kw):
            print '[%s]%s()...'%(prefix, f.__name__)
                return f(**args, **kw)
        return wrapper
    return log_decorator
@log('DEBUG')
def factorial(n):
    return reduce(lamda x, y: x * y, range(1, n + 1))
print factorial(10)
```
此修饰两层嵌套，将最外层函数的参数传了进去。  
为了避免装饰的时候新的方法覆盖了原有的方法的名称和属性等，需要在装饰器上添加
@functools.wraps
```
def log(prefix):
    def log_decorator(f):
        @functools.wraps(f)
        def wrapper(**args, **kw):
            print '[%s]%s()...'%(prefix, f.__name__)
                return f(**args, **kw)
        return wrapper
    return log_decorator
@log('DEBUG')
def factorial(n):
    return reduce(lamda x, y: x * y, range(1, n + 1))
print factorial(10)
```

@functools.partical是Python的一个偏函数，可以把一个参数多的函数编程一个参数少的新函数，
少的参数需要在创建时指定默认值，这样，新函数调用的难度就降低了。  
```
import functools
int2 = functools.partial(int, base=2)
int2('1000000')
```
此函数目的是将2进制的数字变成10进制的数字。原int默认是10进制  

### 模块
Python里面也包含包和模块，每个包下必须包含__init__.py，即使该文件内容为空，也必须含有  
模块导入：import 模块的路径和模块名称  
方法调用：模块名称`.`方法名称  
如果只用到某些方法：from math import pow, sin, log  
给方法起别名：from logging import log as logger  
如果导入的模块不存在，则报ImportError错误  
当新版本的一个特性与旧版本不兼容时，该特性将会在旧版本中添加到__future__中，
以便旧的代码能在旧版本中测试新特性。  

### 类
Python中类用class关键字定义  
实例创建：类名+`()`  
属性：对象+`.`+属性名
创建类时，__init__方法被最先调用，第一个参数时self
```
class Person(object):
    def __init__(self, name, gender, **kw):
        self.name = name
        self.gender = gender
        for k, v in kw.iteritems():
            setattr(self, k, v)
        
xiaoming = Person('Xiao Ming', 'Male')
xiaoming.name = 'Xiao Ming'
xiaohong = Person('Xiao Hong', 'Female')
```
如果属性前加`__`表示私有的，不可被外界访问
```
class Person(object):
    def __init__(self, name):
        self.name = name
        self.__job = 'student'
```
类属性：类名+`.`+属性名称  
当实例属性和类属性重名时，实例属性优先级高，它将屏蔽掉对类属性的访问。  
如果没有实例属性，有类属性的情况下，如果调用实例属性，则返回类属性的值。  
可以给类中动态添加方法，通过types.MethodType()，三个参数分别时方法的实现，对象，类名。但是动态创建方法的不常用  
在class中定义的全部是实例方法，实例方法第一个参数self是实例本身。
要在class中定义类方法，需要标记`@classmethod`,该方法将绑定到Person类上，而非类的实例。
类方法的第一个参数将传入类本身，通常将参数名命名为cls，cls.cout实际上相当于Person.count
```
class Person(object):
    count = 0
    @classmethod
    def how_many(cls):
        return cls.count
    def __init__(self, name):
        self.name = name
        Person.count = Person.count + 1
        
        
print Person.how_many()
p1 = Person('Bob')
print Person how_many()
```

### 继承
继承需要注意：继承类和__init__中super  
```
class Person(object):
    def __init__(self, name, gender):
        self.name = name
        self.gender = gender
```
```
class Student(Person):
    def __init__(self, name, gender, score):
        super(Student, self).__init__(name, gender)
        self.score = score
```
子类中一定要先初始化父类，否则没有父类中的相关属性  
isinstance()可以判断一个变量的类型，包括自定义类型  
两个参数，第一个是对象名称，第二个是类的名称，返回布尔类型  
Python支持多重继承，多重继承的目的是从两种继承树中分别选择出继承出子类，以便组合功能使用  
type()函数，获取变量的类型，返回一个Type对象  
dir()函数获取变量的所有属性  
如果知道属性名称，可以使用getattr()和setattr()函数，设置属性和获取属性  
getattr(mClass, 'name')不设置默认值，如果属性不存在报错  
getattr(mClass, 'name', 'Bob')设置默认值Bob  
setattr(mClass, 'name', 'Bob')  

### 特殊方法
Python的相关特殊方法：  
__str__    __nonzero__    __getitem__    __add__     __neg__  
__repr__   __getattr__    __setitem__    __sub__     __abs__  
__lt__     __setattr__    __delitem__    __mul__     __int__  
__le__     __delattr__    __reversed__   __floordiv__ __long__  
__eq__     __get__        __contains__    __mod__    __float__  
__ne__     __set__       __setslice__     __divmod__  __oct__  
__gt__     __delete__     __delslice__    __pow__     __hex__  
__ge__     __call__        __lshift__     __and__     __index__  
__cmp__    __len__         __rshift__     __xor__     __enter__  
__hash__    __iter__      __div__         __or__      __exit__  

在设置成绩的时候做出判断
```
class Student(object):
    def __init__(self, name, score):
    self.name = name
    self.__score = score
    @property
    def score(self):
        return self.__score
    @score.setter
    def score(self, score):
        if score < 0 or score > 100:
            raise ValueError('invalid score')
        self.__score = score
```
注：第一个score(self)是get方法，用@property装饰，第二个score(self, score)是set方法，
用@score.setter装饰，@score.setter是前一个@property装饰后的副产品。  

如果只添加name，gender，score3个属性，可以利用__slots__来实现
```
class Student(object):
    __slots__ = ('nam', 'gender', 'score')
    def __init__(self, name, gender, score):
        self.name = name
        self.gender = gender
        self.score = score
```
__slots__的目的是限制当前类所能拥有的属性，如果不需要添加任意动态的属性，使用__slots__也能节省内存。  
