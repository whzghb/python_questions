

```python
a = 1
b = 1
print(id(a),id(b))
print('小整数',a is b)
#以下证明，同一程序中，都是指向小整数对象池中的同一份数据
```

    1545169936 1545169936
    小整数 True
    


```python
a = -5
b = -5
c = -6
d = 256
e = 256
f = 257
print(id(a),id(b),id(c),id(d),id(e),id(f))
#小整数对象池，-5到256
```

    1545169744 1545169744 610123422704 1545178096 1545178096 610123422160
    


```python
a = "abcdefhfwaekfe"
b = "abcdefhfwaekfe"
print("无空格字符串",a is b)
#intern机制
```

    无空格字符串 True
    


```python
a = "hello world"
b = "hello world"
print('有空格字符串',a is b)
```

    有空格字符串 False
    


```python
a = [1,2,3,4]
b = [1,2,3,4]
print("数组",a is b)
a = (1,2,3,4)
b = (1,2,3,4)
print('元组',a is b)
#除了小整数和无空格字符串，均为False
```

    数组 False
    元组 False
    


```python
a = 10240.0000
b = 10240.0000
print(id(a),id(b))
print("整数",a is b)
#在pycharm(python版本为3.6)中此处id(a)与id(b)相同，结果为True,在python3.6命令行id不同，结果为False
#可能pycharm做了优化，如果已有定义，另一个引用直指向它，而不是另开空间
```

    610123604112 610123604184
    整数 False
    


```python
print(1 in [1,0] == True)
#这里python使用了比较运算符链
#1 in [1,0] == True
#将被转为
#(1 in [1, 0]) and ([1, 0] == True)
#就像a<b<c会被转化为a<b and b <c
print((1 in [1,0]) == True)
#加个括号就行了
```

    False
    True
    


```python
print('hello world'[::-1])
print('hello world'[::-2])
#字符串逆转
```

    dlrow olleh
    drwolh
    


```python
#list.reverse(),修改自己
aList = [123, 'xyz', 'zara', 'abc', 'xyz']
aList.reverse()
print(aList)
#reversed(list)得赋值给另一变量，且变成了一个生成器
aList = [123, 'xyz', 'zara', 'abc', 'xyz']
a = reversed(aList)
print('a:',a)
print('next:',next(a))
for i in a:
    print(i)
```

    ['xyz', 'abc', 'zara', 'xyz', 123]
    a: <list_reverseiterator object at 0x0000008E0E363E48>
    next: xyz
    abc
    zara
    xyz
    123
    


```python
import random
# print(ord('A'))
# print(chr(122))
print(chr(90))
print(chr(65))
res = ""
for i in range(6):
    j = random.randrange(6)
#     print(j)
    if i == j:
        res += str(chr(random.randrange(65,91)))
    else:
        res += str(random.randrange(0,10))
print(res)
import string, random
res = ''.join(random.choice(string.ascii_uppercase + string.digits) for x in range(6))
print(res)
```

    Z
    A
    18U527
    PRCDZQ
    


```python
# if not "blah" in 'fjablah'’:
#     print('ok')
# else:
#     print('notok')
if "blah" not in 'fablahfjak': 
    print('ok')
else:
    print('notok')
```

    notok
    


```python
s = "This be a string"
if s.find("is") == -1:
    print ("No 'is' here!")
else:
    print ("Found 'is' in the string.")
```

    Found 'is' in the string.
    


```python
def is_number(s):
    try:
        float(s)
        return True
    except ValueError:
        return False
print(is_number(738.839))
print(is_number('fa21'))
```

    True
    False
    


```python
import random
a = [1,2,3,4]
random.shuffle(a)
print(a)
```

    [2, 3, 1, 4]
    


```python
import re
DATA = "Hey, you - what are you doing here!?"
print(re.findall(r"[\w']+", DATA))
```

    ['Hey', 'you', 'what', 'are', 'you', 'doing', 'here']
    


```python
a = 'hello world'
print(a[-3:-1])
```

    rl
    


```python
print("{0:010d}".format(4))
a = '4'
print(a.zfill(3))
```

    0000000004
    004
    


```python
import time
time.strftime('%Y-%m-%d %H:%M:%S',time.localtime())
```




    '2018-08-11 21:32:37'




```python
from os import listdir
from os.path import isfile, join
onlyfiles = [f for f in listdir('c:\\') if isfile(join('c:\\',f))]
print(onlyfiles)
```

    ['bootmgr', 'BOOTNXT', 'chromedriver.exe', 'DBAR_Ver.txt', 'dell.sdr', 'hiberfil.sys', 'InstallConfig.ini', 'pagefile.sys', 'swapfile.sys']
    


```python
from os import walk

f = []
for (dirpath, dirnames, filenames) in walk('c:\\'):
    print(dirpath,'|||',dirnames,'|||',filenames)
    break
    f.extend(filenames)
    break
```

    c:\ ||| ['$360Section', '$GetCurrent', '$Recycle.Bin', '15175809f16976ff92ba50b87773', '360SANDBOX', '5c3b3a8efd8bb335d8db150455', '798491cc2be876aa5fe9', '8f7d27d5108bb832b0f57cc6c1111ec7', '8fe338943d05999646c025a65d857adb', 'a', 'Apps', 'DELL', 'Documents and Settings', 'Drivers', 'DTLFolder', 'e900b2aeb80d78638ee7', 'e9bc37396aa37bf0ffad', 'f74b0d88bc1491205430652fb5140ba7', 'Git', 'inetpub', 'Intel', 'MASM611', 'MongoDB', 'MyDownloads', 'MySQL-Front', 'Notepad++', 'PerfLogs', 'phantomjs-2.1.1-windows', 'pip', 'Program Files', 'Program Files (x86)', 'ProgramData', 'Proxifier', 'Python27', 'Python34', 'python36', 'Python36-32', 'Sublime Text 3', 'SymCache', 'System Recovery', 'System Volume Information', 'Temp', 'toolsdown', 'Users', 'Windows', 'xshell5'] ||| ['bootmgr', 'BOOTNXT', 'chromedriver.exe', 'DBAR_Ver.txt', 'dell.sdr', 'hiberfil.sys', 'InstallConfig.ini', 'pagefile.sys', 'swapfile.sys']
    


```python
import glob
print(glob.glob("c:\\*.txt"))
```

    ['c:\\DBAR_Ver.txt']
    


```python
"""
windows下实现mkdir -p的操作
"""
import os
def my_mkdir(dir):
    dirs = dir.split('\\')
    if os.path.isdir(dirs[0]):
        for i in range(1,len(dirs)):
            name = os.path.abspath(dirs[0])
            for j in range(1,i+1):
                if name.endswith('\\'):
                    name += dirs[j] + '\\'
                else:
                    name += '\\'+ dirs[j]
            if os.path.isdir(name):
                continue
            else:
                os.mkdir(name)
    else:
        for i in range(len(dirs)):
            name = os.path.abspath('.\\')
            for j in range(i+1):
                name += '\\'+dir.split('\\')[j]
            os.mkdir(name)

# pwd = os.path.abspath('.\\').split('\\')[-1]

my_mkdir('c:\\a\\c\\d')
my_mkdir('c:\\a\\c\\f\\g')
my_mkdir('a\\b\\c')
my_mkdir('a\\d\\e')

```


```python
# count = 0
# with open('app.py','r',encoding='utf-8') as f:
#     for line in f:
#         count += 1
#     print(count)
```


```python
print('十六进制的十进制数',0x12AF)
print('八进制的十进制数',0O1267)
```

    十六进制的十进制数 4783
    八进制的十进制数 695
    


```python
print(int('a',16))
print(int('0xa',16))
# print(int('a'))
print(int(16))
```

    10
    10
    16
    


```python
a = 4
b = 6
c = a/b
print(c)
```

    0.6666666666666666
    


```python
#有什么用？
from __future__ import division
a = 4
b = 6
# c = a.division(b)
# print(c)
```


```python
a=13.946
print("{0:.2f}".format(a))
print("{0:.2f}".format(round(a,2)))
```

    13.95
    13.95
    


```python
#获取素数
def get_su(num):
    no = []
    for i in range(1,num):
        for j in range(2,i-1):
            if i % j == 0:
                no.append(i)
                break

    res = list(i for i in range(1,num))
    for i in no:
        res.remove(i)
    return res
print(get_su(100))
```

    [1, 2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97]
    


```python
#判断列表为空，不要用len判断
a = []
if not a:
    print('列表为空')
```

    列表为空
    


```python
l1 = [1,2,3]
l2 = [4,5,6]
# l1 + l2

# 会修改l1
# l1.extend(l2)
# print(l1)

import itertools
for item in itertools.chain(l1, l2):
    print(item)
```

    1
    2
    3
    4
    5
    6
    


```python
a = [1,2,3]
# 都行
# copy deepcopy
# b = list(a)
# b = a
# b = a[:]
print(b)
```

    6
    


```python
foo = ['a', 'b', 'c', 'd', 'e']
from random import choice
print(choice(foo))
```

    e
    


```python
def split_same(l,n):
    res = [l[n*i:n*(i+1)] for i in range(len(l)//n)]
    if len(l) % n != 0:
        last = l[-(len(l) % n):]
        res.append(last)
    print(res)

def chunks(l, n):
    return [l[i:i+n] for i in range(0, len(l), n)]
l = [i for i in range(30)]
# print(chunks(l,4))

def chunks(l, n):
    """ Yield successive n-sized chunks from l.
    """
    for i in range(0, len(l), n):
        yield l[i:i+n]
list(chunks(range(10, 75), 10))

# 不报错！！！！
# print(l[20:100])
```




    [range(10, 20),
     range(20, 30),
     range(30, 40),
     range(40, 50),
     range(50, 60),
     range(60, 70),
     range(70, 75)]




```python
#扁平二维列表
def l_m2o(l):
    res = [i for j in l for i in j]
    print(res)
    
l = [[4,5,2],[5,6,7],[32,4],[2,3]]
l_m2o(l)
```

    [4, 5, 2, 5, 6, 7, 32, 4, 2, 3]
    


```python
res = map(lambda x,y:x+y,[1,2,3,4],[4,5,6])
print(res)
print(list(res))
```

    <map object at 0x0000008E0E37E240>
    [5, 7, 9]
    


```python
p  = [1, 2]
p[1:1] = [p]
print(p)
# [...]无限嵌套不可打印的列表
```

    [1, [...], 2]
    


```python
from collections import namedtuple
Point = namedtuple('Point', 'x y z')
pt1 = Point(1.0, 5.0, 3.0)
pt2 = Point(2.5, 1.5, 4.0)

from math import sqrt
line_length = sqrt((pt1.x-pt2.x)**2 + (pt1.y-pt2.y)**2 + (pt1.z-pt2.z)**2)
print(line_length)
```

    3.9370039370059056
    


```python
# 可变元组
from recordtype import recordtype
Point = recordtype('Point', 'x y')
pt1 = Point(1.0, 5.0)
pt1 = Point(1.0, 5.0)
pt1.x = 2.0
print(pt1.x)
```

    2.0
    


```python
d = {'a':1,'b':2}
#获取时,如不存在，得到默认值
d.get('a', 0)
#设置时，若key不存在，设置默认值，已存在，返回已存在value
d.setdefault('c', []).append('3')
d.setdefault('c', []).append('3')
print(d.get('c'))

# 更新
d.update({'a':10})
# 设置
d['a'] = 20
print(d)
#初始即默认值
from collections import defaultdict
d = defaultdict(lambda: 'abc') # 0.'abc',None都行
print(d['a'])
#or d = defaultdict(int)
# print(d)
```

    ['3', '3']
    {'a': 20, 'b': 2, 'c': ['3', '3']}
    abc
    


```python
d1 = {'a':1,'b':2}
d2 = {'c':3,'d':4}
d3 = {'a':2,'e':5}
d1.update(d2)
print(d1)

# 若key相同，以括号中的为准，根据d3更新d1
d1.update(d3)
print(d1)

```

    {'a': 1, 'b': 2, 'c': 3, 'd': 4}
    {'a': 2, 'b': 2, 'c': 3, 'd': 4, 'e': 5}
    


```python
d1 = {'a':1,'b':2}
d2 = {'a':2,'e':5}

# 以后面的为准
z = dict(list(d1.items()) + list(d2.items()))
print(z)
```

    {'a': 2, 'b': 2, 'e': 5}
    


```python
keys = ('name', 'age', 'food')
values = ('Monty', 42, 'spam')
print(dict(zip(keys,values)))
```

    {'name': 'Monty', 'age': 42, 'food': 'spam'}
    


```python
class foo(object):
    def abc(self):
        print("ok")

a = foo()
if hasattr(a,'abc'):
    getattr(a,'abc')()
else:
    print("no!!!!")
```

    ok
    


```python
def bar(x,*args,**kwargs):
    print(x,y,z)
    print(kwargs['a'])

x = 3
y = 4
z = 5
bar(x,y,z,a=1, b=2)
```

    3 4 5
    1
    


```python
def bar2(x,y):
    print(x,y)

l = [1,2]
bar2(*l)
```

    1 2
    


```python
first, *rest = [1,2,3,4]
print(first,rest)
first, *l, last = [1,2,3,4]
print(first,l,last)
```

    1 [2, 3, 4]
    1 [2, 3] 4
    


```python
def try_to_change_list_contents(the_list):
    print ('got', the_list)
    # 原地修改，影响外部数据
    the_list.append('four')
    the_list += ['five']
    # 重新指向，对外部数据不修改
    the_list = the_list + ['six']
    print ('changed to', the_list)

outer_list = ['one', 'two', 'three']
print ('before, outer_list =', outer_list)
try_to_change_list_contents(outer_list)
print ('after, outer_list =', outer_list)
```

    before, outer_list = ['one', 'two', 'three']
    got ['one', 'two', 'three']
    changed to ['one', 'two', 'three', 'four', 'five', 'six']
    after, outer_list = ['one', 'two', 'three', 'four', 'five']
    


```python
def try_to_change_string_reference(the_string):
    print ('got', the_string)
    # 不可变类型，一修改便重新指向，无法影响外部的数据
    the_string = 'In a kingdom by the sea'
    the_string += 'aaaaaa'
    print ('set to', the_string)

outer_string = 'It was many and many a year ago'
print ('before, outer_string =', outer_string)
try_to_change_string_reference(outer_string)
print ('after, outer_string =', outer_string)
```

    before, outer_string = It was many and many a year ago
    got It was many and many a year ago
    set to In a kingdom by the seaaaaaaa
    after, outer_string = It was many and many a year ago
    


```python
class Test(object):
    pass

class Test2(Test):
    pass

t = Test()
t2 = Test2()
print(type(t) is Test)
print(type(t2) is Test)
print(isinstance(t,Test))
print(isinstance(t2,Test))
# isinstance为子类服务，type不能为子类服务
```

    True
    False
    True
    True
    


```python
class Test3(object):
    # 不一定非要是self，abc也行，但一定得有，放在第一个位置上
    def __init__(abc,name):
        abc.name = name

t = Test3('user1')
print(t.name)
```

    user1
    


```python
class MyClass(object):
    def myPublicMethod(self):
        print ('public method')

    def __myPrivateMethod(self):
        print ('this is private!!')

    def get_private(self):
        self.__myPrivateMethod()

m = MyClass()
m.myPublicMethod()

# 获取私有方法，属性也是一样的
m._MyClass__myPrivateMethod()
m.get_private()
# 所有的方法
print(dir(m))
# ‘private'只是用作，确保子类不会意外覆写父类的私有方法和属性.不是为了保护外部意外访问而设计的！
```

    public method
    this is private!!
    this is private!!
    ['_MyClass__myPrivateMethod', '__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', 'get_private', 'myPublicMethod']
    


```python
class A(object):
    _dict = dict()

    def __new__(cls):
        if 'key' in A._dict:
            print ("EXISTS")
            return A._dict['key']
        else:
            print ("NEW")
            return super(A, cls).__new__(cls)

    def __init__(self):
        print ("INIT")
        A._dict['key'] = self
        print ("")

a1 = A()
a2 = A()
a3 = A()
# __new__最先被调用
```

    NEW
    INIT
    
    EXISTS
    INIT
    
    EXISTS
    INIT
    
    


```python
class Base(object):
    def __init__(self):
        print ("Base created")
        
class ChildB(Base):
    def __init__(self):
        super(ChildB, self).__init__()

b = ChildB() # 打印Base created
print(b) 
# Super让你避免明确地引用基类，这是一点。最大的优势是，当出现多重继承的时候，各种有趣的情况就会出现。
```

    Base created
    <__main__.ChildB object at 0x0000008E0E5A7F60>
    


```python
import collections
e = 'aasssdd'
if isinstance(e, collections.Iterable):
    print('yes')
else:
    print('no')

# if isinstance(e,collections.Iterator):
#     print('Iterator')
# if isinstance(e,collections.Generator):
#     print('Generator')    
# 判断是否可迭代，迭代器，生成器
```

    yes
    


```python
"""
抽象类是通过定义抽象方法，要求子类必须继承，从而达到归一化的效果。
抽象类是从上往下，定义好了应该要实现的方法，子类必须根据要求来实现。
接口是从下往上，去找不同类中相同的方法，调用方法相同，但实际的内容不同。
"""
# 抽象类
import abc #利用abc模块实现抽象类

class All_file(metaclass=abc.ABCMeta):
    all_type = 'file'
    @abc.abstractmethod #定义抽象方法，无需实现功能
    def read(self):
        '子类必须定义读功能'
        pass

    @abc.abstractmethod #定义抽象方法，无需实现功能
    def write(self):
        '子类必须定义写功能'
        pass

# class Txt(All_file):
#     pass
#
# t1=Txt() #报错,子类没有定义抽象方法

class Txt(All_file): #子类继承抽象类，但是必须定义read和write方法
    def read(self):
        print('文本数据的读取方法')

    def write(self):
        print('文本数据的读取方法')

class Sata(All_file): #子类继承抽象类，但是必须定义read和write方法
    def read(self):
        print('硬盘数据的读取方法')

    def write(self):
        print('硬盘数据的读取方法')
        
wenbenwenjian=Txt()
yingpanwenjian=Sata()
#这样大家都是被归一化了,也就是一切皆文件的思想
wenbenwenjian.read()
yingpanwenjian.write()
print(wenbenwenjian.all_type)
print(yingpanwenjian.all_type)

# 鸭子模型,接口
class Duck():
  def walk(self):
    print('I walk like a duck')
  def swim(self):
    print('i swim like a duck')

class Person():
  def walk(self):
    print('this one walk like a duck')
  def swim(self):
    print('this man swim like a duck')

d = Duck()
p = Person()

# 并不在意是Duck的实例对象还是Person的实例对象,只要有walk和swim方法就行
# 接口
def test(arg):
    arg.walk()
    arg.swim()

test(d)
test(p)
```

    文本数据的读取方法
    硬盘数据的读取方法
    file
    file
    I walk like a duck
    i swim like a duck
    this one walk like a duck
    this man swim like a duck
    


```python
# 因为在python3.x之后全是新式类，测试不出结果，继承搜索方式都是广度优先再往上搜索，
# C1没有找D1，D1有，所以执行。
# 此处所以打印的都是最后继承的class D中的输出，如果在python2中，经典类是深度优先，会
# 先找到C1，但是C1没有此方法，继续往上找到A，执行A中的foo方法，如果A没有的话，回
# 到最下面找D1，再没有再往上，一直没有就报错
class A(object):
    """
	新式类
    作为所有类的基类
    """
    def foo(self):
        print ("class A")

class A1():
    """
	经典类
    作为所有类的基类
    """
    def foo(self):
        print ("class A1")

class C(A):
    pass

class C1(A1):
    pass

class D(A):
    def foo(self):
        print ("class D")

class D1(A1):
    def foo(self):
        print ("class D1")

class E(C, D):
    pass

class E1(C1, D1):
    pass

e = E()
e.foo()

e1 = E1()
e1.foo()
```

    class D
    class D1
    


```python
# 给实例添加方法与属性
class Test4(object):
    pass

t = Test4()

def test(self):
    print("this is test",self.name)
    
def test2():
    print("this is test2")

# 给类添加方法，所有的实例都能调用    
Test4.test2 = test2()

t.name = "name1"
# 给实例添加方法，只有当前实例能用
t.test = test(t)
t.test
t.test2
print(t.name)
```

    this is test2
    this is test name1
    name1
    


```python
class bcolors(object):
    HEADER = '\033[95m'
    OKBLUE = '\033[94m'
    OKGREEN = '\033[92m'
    WARNING = '\033[93m'
    FAIL = '\033[91m'
    ENDC = '\033[0m'

b = bcolors()
print("{0}aaaaaaaa{1}".format(b.HEADER,b.ENDC))
print("{0}aaaaaaaa{1}".format(b.OKBLUE,b.ENDC))
print("{0}aaaaaaaa{1}".format(b.FAIL,b.ENDC))
```

    [95maaaaaaaa[0m
    [94maaaaaaaa[0m
    [91maaaaaaaa[0m
    


```python
# 模板，具体方法具体改
class UpperAttrMetaclass(type):
    # cls future_class_name, future_class_parents, future_class_attr
    # cls 需要实例化的类,python解释器提供
    # clsname 类名即下文的Test
    # bases 父类即object
    # dct 参数,如下文的abc,bcd
    def __new__(cls, clsname, bases, dct):
        uppercase_attr = {}
        for name, val in dct.items():
            if not name.startswith('__'):
                uppercase_attr[name.upper()] = val
            else:
                uppercase_attr[name] = val
        return super(UpperAttrMetaclass, cls).__new__(cls, clsname, bases, uppercase_attr)

# python2
# class Test():
#     __metaclass__=UpperAttrMetaclass
    
class Test(object,metaclass=UpperAttrMetaclass):
    abc = "I dont Know"
    def bcd(self):
        print("this is bcd")

print(hasattr(Test,'ABC')) # True
print(hasattr(Test,'abc')) # False
print(hasattr(Test,'BCD')) # True
print(hasattr(Test,'bcd')) # False
```

    True
    False
    True
    False
    
