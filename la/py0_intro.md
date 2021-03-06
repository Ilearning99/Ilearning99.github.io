# python编程语言入门

## 介绍

python是目前程序员必会的编程语言之一。

### python的优点：

- 易学。它被称作是“可以执行的伪代码”，这说明python的语法与用户自然语言很接近，因而是非常容易上手的，以及程序非常清晰的编程语言。

- 丰富的软件包支持。大部分软件包都有python接口，深度学习包tensorflow，pytorch等，矩阵运算包numpy，数据分析统计包pandas，等等。所以python又有“胶水语言”的称号。

- 开发效率高。python拥有丰富的软件包支持，因此，便于快速的代码迭代。后续代码优化中，可以再根据需要将不同代码模块进行优化，或用其它语言进行改写。由于解释器按行执行代码，python程序也有便于调试的特点。

- 编写脚本。python的最初设计就用于编写自动化脚本，因此，我们可以编写python作为自动开发脚本。

### python与其它语言的关系：

从我个人角度，python会长久的存在，是程序员必备的能力之一，它有其它语言所不可替代的特性，但是python由于最初设计是作为脚本语言，python的代码本身的运行效率要低一些。

## python教程

### 安装

- 下载。在python官网上下载python安装包 [\[下载地址\]](https://www.python.org/downloads/)，选择对应操作系统最新版本的python进行安装。
- 安装。windows环境下注意要将python添加到环境变量中。
- 版本。python现在有两个主流版本2.x和3.x，由于历史原因，3.x并不是2.x的升级版本，两者是并行的关系，最好用3.x版，2.x版本现在已经很少迭代更新。

### 语法

#### 变量

变量在所有编程语言中都是非常重要的概念。

可以这样理解，计算机中需要用到的程序代码和数据都必须存储在计算机内存中，变量就是给这些内存中的代码和数据起一个名字，用一个变量去指向它们，以便程序后续使用。为什么叫做变量，顾名思义，可以修改这个变量，使它指向其它内容。python是一种动态类型语言，这说明，变量可以指向任何内容。而强类型语言，如java、c++等，给变量指定了类型，在这种情况，变量只能指向特定类型的对象。

通过赋值语句给变量赋值，使变量指向内存中对应的内容：

```.python
import turtle
a = "hello world!"
b = turtle.Turtle()
```

如上例，内存中存在一个字符串，使变量a指向该字符串，以便后续使用该字符串。turtle.Turtle()方法在内存中创建了一个turtle对象，使变量b指向该对象，后续可以通过变量来操纵对应的turtle对象。


#### 列表、元组和字符串

列表、元组和字符串都是线性的数据结构。

##### 列表

- 定义

列表通过[]方括号定义，其中包含一系列元素，如下所示：
```.python
a = [1,2,3]
```

- 列表添加元素

通过列表对象的append方法，对现有列表添加元素：
```.python
b = []
b.append(10)
print(b) # ［10］
```

- 索引和切片

可以通过位置索引获取对应位置元素，并对对应元素进行修改，获取列表的切片（连续一段子集，也是列表）：
```.python
print(a[0]) # 1
a[0]=-1
print(a) # [-1,2,3]
print(a[0:1]) # [-1]
```

##### 元组

元组使用()圆括号定义，包含系列元素，可以看作是不可变的列表。

元组不支持任何对其元素修改的操作，但可以使用索引和切片操作。

```.python
a = (1,2,3,4)
print(a[0]) # 1
print(a[0:2]) # (1,2)
```

##### 字符串

字符串使用""或''定义，字符串可以看作是特殊的元组。

注意：
- 字符串的每个位置的元素还是一个字符串。
- 字符串不支持对其修改操作，字符串的拼接操作会在内存中构造一个新的字符串。

##### 共同支持的操作

- len()。返回序列中的元素个数。
- in。一个序列是否包含在另一个序列中。

#### 循环

编写程序主要是为了解放劳动力，通过计算来执行简单重复的工作。循环语句就是为了解决多次执行简单重复工作的问题。比如，打印0到9999。

python中有两种循环，for循环和while循环。

```.python
# for 循环
for i in range(10000):
    print(i)

# while 循环
i = 0
while i < 10000:
    print(i)
    i += 1
```

循环语句是一种复合语句，复合语句简单的说，就是由多条语句组成的代码块，在python中，复合语句第一行由关键词定义，后续语句采用统一的缩进，表示在对应复合语句块中，缩进约定俗成为4个空格。

- for循环。以关键词for开头，需要一个列表作为参数，循环每次获取列表中的一个值赋给循环变量，以便于语句块中的其它代码使用。而配套for循环range函数可以辅助生成具有某些简单规则的序列。
```.python
for name in ['ws','gz']:
    print(f'{name} is a kind person")
```

- while循环。以关键词while开头，包含一个条件判断语句，如果语句为真，则一直执行训练，直到条件语句为假，或者使用break语句跳出循环。
- for循环与while循环的关系。如果不知道循环次数，就需要使用while循环，在python中，while循环可以完全替换for循环，但是，使用for循环代码结构更加紧凑清晰，因此在知道循环次数的情况下，都是使用for循环，其它情况使用while循环。

#### 函数

函数是一个复合语句，是具有特定逻辑功能的代码块，将代码切分成各个功能函数，可以使得程序逻辑更加清晰。如下是一个判断一个数是否为偶数的函数。

```.python
def is_even(num):
    return num%2==0
```

函数以def关键词开始，加函数名，加参数列表，函数结尾是一个return关键词开始的语句，用来返回函数的结果。

##### 实参和形参

一般，把调用函数时，实际传入的值称为实参，因为，这是函数运行时，实际使用的参数值；把函数里使用的参数变量称为形参。

#### 类与对象

python的类是以class为关键词的复合语句，类是自己定义的一种数据类型，可以定义这种类型包含的信息以及可以执行的操作。

```.python
class Person:
    def __init__(self,name):
        self.name = name

    def response(self):
        return "Hello!"

    def hear(self,words):
        if self.name in words:
            return self.response()
        else:
            return ""

me = Person("gz")
print(me.hear("Hello, gz!"))
```

如上所示，定义类以关键词class和类名开头，__init__是python给每个类自带的初始化器，可以初始化该类当前新创建对象的数据域。在类里定义函数，称为方法，表示当前对象可以执行的操作，由于类的方法与当前对象相关，所以每个方法第一个参数都是当前对象，对象调用时默认传入，约定俗成用self代表当前对象参数。

##### is-a关系与has-a关系

有些不同类型对象之间会存在相互关联，主要有两种关系：is-a关系和has-a关系。

##### is-a关系与子类

is-a关系是“是一个”关系，比如，男人是人，在类的关系上，类型男人是类型人的子类，如下是男人类的定义。

```.python
class Man(Person):
    def __init__(self,name):
        super().__init__(name)
        self.gender = "male"
```

()圆括号内包含父类名称，子类能够继承所有父类包含的属性和方法，python自带的super()方法，可以将当前对象转化为父类对象，因而可以调用父类的方法。

##### has-a关系

has-a关系是一种包含关系，比如，每个房子实际都有一个所有人，但是不能说房子是人，在类的关系上说，类型房子有一个类型是人的属性，如下是房子类的定义。

```.python
class House:
    def __init__(self,owner):
        self.owner = Person(owner)
```

#### 导入程序模块

我们不可能在一个文件中写所有的程序，并且当我们写好一个程序后，我们希望能够尽可能多次利用，就需要在当前文件中导入其它模块，如下。

```.python
import turtle
```

例如，需要导入的.py为hello.py，那么导入语句应该写成import hello

##### 相对引用

导入当前目录下的模块

```.python
from .my_file import my_module
```

##### __name__属性

python在导入一个文件的过程中，需要运行该文件的所有代码，这有一个问题，比如，我们需要测试这个文件代码，那么，测试完我们需要注释掉这些所有代码吗？这有些麻烦，有什么办法可以解决呢？

仔细思考这个问题，我们会发现，这两种运行程序的情况是有区别的，当我们希望去测试某段代码时，我们总是从当前文件开始运行，而导入模块是从其它文件import当前文件并运行。python的设计者，通过一个内置属性__name__对这两种情况加以区分。

对于从命令行运行的情况，\_\_name\_\_的值是字符串"\_\_main\_\_"；而对于import语句，\_\_name\_\_的值是当前模块名。所以，我们可以通过if语句判断情况，进而运行对应代码。

##### setattr

通过setattr给object设置属性和对应的属性值

```.python
setattr(obj, key, value)
```

#### 总结

总地来说，python程序的语句主要分为两大类，基本语句和复合语句

##### 基本语句

- 赋值语句。=,+=,-=
- 算术运算语句。+,-,*,/,%
- 调用函数语句。print,input,...
- 调用类和对象方法语句。

##### 复合语句

- 循环语句。for/while
- 函数定义。def
- 类型定义。class

### 实践

#### turtle包

python3中会自带一个工具包turtle，可以直接import进来，并在程序中使用。turtle是海龟的意思，它来源于早期的人工智能教育家开发的教学机器人。这个机器人外形像一只海龟，它的尾巴系着一支彩笔，可以控制这个机器人移动，尾巴后面的彩笔会在白纸上画出图案。turtle包有着相似的功能。如下说明：

```.python
gz = turtle.Turtle() # 创建Turtle对象
gz.color('yellow') # 设置颜色
gz.forward(100) # 向前移动100个像素
gz.right(90) # 向右转90度
gz.hideturtle() # 隐藏小乌龟
gz.penup() # 抬起画笔
gz.pendown() # 放下画笔
gz.width(5) # 设置线宽5个像素
```

我们可以通过turtle画出很多复杂的图形，示例如下：

```.python
import turtle

gz = turtle.Turtle()
gz.color("blue")
gz.width(5)

for i in range(200):
    gz.right(75)
    gz.forward(i)
```

<img src="./img/turtle.png" width = "400" height = "400" alt="图形效果" align=center />

#### 爬虫

爬虫主要作用是自动获取页面信息，要完成两件事情，发送http请求，解析html页面，都有对应的python包可以使用

##### 发送http请求

使用requests包

- 安装requests包，pip3 install requests
- 发送http请求，response = requests.get("http://www.baidu.com")

##### 解析html文件

使用BeautifulSoup包

- 安装BeautifulSoup包，pip3 install beautifulsoup4
- 解析html文本，soup = BeautifulSoup(response,'html.parser')

##### 正则表达式

```.python
import re

matches = re.search(pattern, string)
```

## jupyter notebook

### dataframe 展示

- 使用display，在jupyter notebook的cell里可以展示dataframe
```.python
import pandas as pd
data = pd.read_excel('data.xlsx')
display(data)
```
