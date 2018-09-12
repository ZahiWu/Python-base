# Python-base

### 1 编码规则
　　每种编程语言都有独特的编码规则，合理使用注释、合理使用空行、语句的分隔、模块的导入方式、命名规则和代码缩进，能够提高程序的可读性和易移植性。
##### 1.1 合理使用注释
+ 使用（#）号后面跟注释内容

```Python
a = 10  #变量
```

　　此外，如果要在代码中使用中文注释，则必须在Python代码的开始位置加上注释说明：

```Python
#-*-coding:UTF-8-*-
```

　　如果Python代码可能在Windows操作系统以外的平台下运行，则在开始位置加上注释说明：

```Python
#!/usr/bin/python
```

+ 使用（'''）或（"""）号注释整段内容

```Python
'''
this is a simple example
print hello world
'''
print('hello world')
```
##### 1.2 合理使用空行
　　空行的作用在于分隔两段不同功能或者不同含义的代码，便于以后代码的维护或者重构。一般情况下，编写程序代码时应该在**函数与函数之间、类的方法之间、类和函数之间**设置空行，用来表示一段新代码的开始。

```Python
class B:
    def funX(self):
        print('funX()')

    def funY(self):
        print('funY()')

if __name__=='__main__':
    a = B()
    a.funX
    a.funY
```
##### 1.3 语句的分隔
　　对于Python语言主要通过换行来识别语句的结束，也支持分号作为一条语句的标识。如果要在**一个物理行中使用多个逻辑行**，应使用（;）号进行分割：

```python
x = 1; y = 2; z = 3
```

　　如果逻辑行太长，则可以在**多个物理行编写一个逻辑行**，Python语言可以使用反斜线（\）：

```python
str = 'This is a string.\
This line continues the first string'
print(str)
```

输出为
```
This is a string.This line continues the first string
```
##### 1.4 模块导入方式
 - 使用import语句导入模块

```python
import sys
print(sys.path)  
print(sys.argv)
```

 - 使用from...import...语句

```python
from sys import path
from sys import argv
print(path)
print(argv)
```

　　推荐使用第一种方法导入，如果导入的模块比较多，且很多模块中包含的函数和方法具有相同的名称，使用第二种方法，阅读程序时就很难弄清楚究竟属于哪种函数和方法，因此在编写程序时应尽量避免使用这种方法。
##### 1.5 命名规则
+ 变量名首字母一般为小写字母或下划线，其他字符可由字母、下划线或数字组成
+ 模块名首字符一般为小写字母，其他可由字母、下划线和数字组成，.py格式的文件本身就是一个模块，因此文件名就是模块名
+ 类名首字母为大写，其他字母采用小写
+ 对象名使用小写字母，类的私有变量和私有方法则以两个下划线作为前缀
+ 函数名首字母通常为小写字母，之后的单词通过下划线或单词首字母增加函数名的可读性

```python
#变量名
_salary = 5000

#类名
class Teacher:    #类名首字母必须大写
    __name = ""    #类的私有变量，两个下划线前缀

    def __init__(self,name):    #类的私有方法，两个下划线前缀
        self.__name = name

    def getName(self):    #方法名首字母小写，其后单词首字母大写
        return self.__name
#对象名   
if __name__ == '__main__':
    teacher = Teacher('Mary')    #对象名使用小写字母
    print (teacher.getName())
```

##### 1.6 代码缩进
　　代码缩进指的是在每行代码前键入空格或制表符来表示代码之间的层次关系，Python语言采用代码缩进和冒号（:）来区分代码块之间的层次关系。

```python
def factorial(n):
    if n == 0:
        return 1
    else:
        return n*factorial(n-1)
```
### 2 数据类型和数据结构
　　不同的编程语言包含不同的数据类型，Python语言提供了下列几种内置的数据类型和数据结构：数字类型，字符串类型、列表（list）、元组（tuple）、字典（dictionary）。
##### 2.1 数字类型
　　Python语言包含：整型，长整型，浮点型和复数型。Python只有双精度浮点型数据。

```python
#整型  python3中没了长整型
a = 10
type(a)
Out[1]: int

#浮点型
b = 10.0
type(b)
Out[2]: float

#复数型
c = 10 + 5j
type(c)
Out[3]: complex

#布尔型 在Python2中是没有布尔型的，它用数字0表示False，用1表示True。到Python3中，把True和False定义成关键字了，但它们的值还是1和0，它们可以和数字相加。
d = True    #一定要大写
type(d)
Out[4]: bool

e = False    #一定要大写
type(e)
Out[5]: bool

a,b,c,d,e = 10,10.0,10+5j,True,False
print(type(a),type(b),type(c),type(d),type(e))

<class 'int'> <class 'float'> <class 'complex'> <class 'bool'> <class 'bool'>
```
##### 2.2 字符串类型

###### 2.2.1 引号的使用

　　Python语言中使用单引号（'）、双引号（"）和三引号（'''）来表示字符串类型的数据。

+ 单引号内不能输出含有单引号字符串，可利用转义字符（\）
+ 双引号内能输出含单引号字符串，不能输出含双引号字符串
+ 三引号内可输出含单引号和双引号字符串
**注意：单引号内可输出含双引号字符串，不能输出含三引号字符串；双引号内可输出含三引号字符串。**

输入程序
```python
print('this is a banana')
print("this is a banana")
print('What\'s your name?')
print("What's your name?")
print('''"What's your name?" I asked.''')
```
输出结果为
```python
this is a banana
this is a banana
What's your name?
What's your name?
"What's your name?" I asked.
```
###### 2.2.2 常用转义字符
|转义字符|描述|转义字符|描述|
|:------:|:---:|:-----:|:--:|
|\\(在行尾时)|续行符|\\'|单引号|
|\\"|双引号|\\a|发出系统响声|
|\\b|退格符，删除前一个字符|\\n|换行符|
|\\t|横向制表符|\\v|纵向制表符|
|\\r|回车符，删除前面所有字符|\\f|换页符|
|\\000|空格|||
```python
print('asdfghjkl')
asdfghjkl

print('asdfg\bhjkl')
asdfhjkl

#\b之后要有字符存在
print('asdfghjkl\b')
asdfghjkl

print('asdfg\nhjkl')
asdfg
hjkl

print('asdfg\thjkl')
asdfg   hjkl

print('asdfg\rhjkl')
hjklg

print('asdfg\000hjkl')
asdfg hjkl
```
###### 2.2.3 字符串的各种方法

字符串的各种方法可通过help(str)进行查询。

```Python
name='hello world'
if name.startswith('he'):
    print("Yes,the string starts with 'he'.")
# if 函数（条件）：
#   print('字符串')

Out[1]:Yes,the string starts with 'he'.

if 'o' in name:
    print('Yes,it contains the string "a".')

Out[2]:Yes,it contains the string "a".

name.find('w')
# 查询元素所在序号
Out[3]: 6

name.find('v')
# -1表示“假”
Out[4]: -1
```

##### 2.3 列表
###### 2.3.1 创建列表
列表的元素均包含在方括号中[]，且列表中的元素可以改变
```Python
list=['car','jeep','bike']
print('list')
#加‘’得到的是单纯的字母'list'
print(list)
print(list[2])
list.append('trator')
#扩展元素
print(list)
list.insert(2,'train')
#在序号2的位置处插入元素
print(list)
list.remove('jeep')
#移除‘jeep’
print(list)
list.pop()
#去掉最后一个元素
print(list)

list
['car', 'jeep', 'bike']
bike
['car', 'jeep', 'bike', 'trator']
['car', 'jeep', 'train', 'bike', 'trator']
['car', 'train', 'bike', 'trator']
['car', 'train', 'bike']
```
###### 2.3.2 列表的访问
```Python
list=['car','jeep','bike','train','trator','ariplane']
print(list[-2])
print(list[1:4])
#左闭右开区间
print(list[-3:-1])
print(list[:])

trator
['jeep', 'bike', 'train']
['train', 'trator']
['car', 'jeep', 'bike', 'train', 'trator', 'ariplane']
```
```Python
list1=['car','jeep','bike']
list2=['train','trator','ariplane']
list1.append(list2)
print(list1)
#append是将list2做为一个元素扩展到list1中

list1=['car','jeep','bike']
list2=['train','trator','ariplane']
list1.extend(list2)
print(list1)
#extend是将list2中的所有元素做为多个元素扩展到list1中

list3=['rocket']
list1=list1+list3
print(list1)

list1+=['spaceship']
print(list1)

list1=['car','bike']*2
print(list1)

['car', 'jeep', 'bike', ['train', 'trator', 'ariplane']]
['car', 'jeep', 'bike', 'train', 'trator', 'ariplane']
['car', 'jeep', 'bike', 'train', 'trator', 'ariplane', 'rocket']
['car', 'jeep', 'bike', 'train', 'trator', 'ariplane', 'rocket', 'spaceship']
['car', 'bike', 'car', 'bike']
```
###### 2.3.3 列表的方法
```Python
list1=['car','jeep','bike']
list2=['train','trator','ariplane']
list1.append(list2)
print(list1)

list1=['car','jeep','bike']
list2=['train','trator','ariplane']
list1.extend(list2)
print(list1)

list1=['car','jeep','bike']
list1+=list1
print(list1)
print(list1[1])
print(list1.count(list1[1]))
print(list1.index('jeep'))
#默认从0到最后
print(list1.index('jeep',3,6))

print(list1)
list1.insert(2,'bus')
print(list1)

list1.pop()
#去掉最后一个元素
print(list1)

list1.remove('jeep')
#去掉第一个‘jeep’
print(list1)

list1.reverse()
#对列表进行反转
print(list1)

list1.sort()
print(list1)

['car', 'jeep', 'bike', ['train', 'trator', 'ariplane']]
['car', 'jeep', 'bike', 'train', 'trator', 'ariplane']
['car', 'jeep', 'bike', 'car', 'jeep', 'bike']
jeep
2
1
4
['car', 'jeep', 'bike', 'car', 'jeep', 'bike']
['car', 'jeep', 'bus', 'bike', 'car', 'jeep', 'bike']
['car', 'jeep', 'bus', 'bike', 'car', 'jeep']
['car', 'bus', 'bike', 'car', 'jeep']
['jeep', 'car', 'bike', 'bus', 'car']
['bike', 'bus', 'car', 'car', 'jeep']
```
##### 2.4 元组
###### 2.4.1 创建元组
输入：
```Python
print("My name is %s, I'm %d years old."%('Zahi',10))
#双引号（""）之后紧跟格式化符号（%），没有逗号，输出的字符串用（''）
```
输出结果：
```Python
My name is Zahi, I'm 10 years old.
```
```Python
zoo=('wolf',)
print(zoo[0])
zoo=('wolf')
print(zoo[0])
#第一个表示元组，第二个表示字符串，当元组只有一个元素时，后面要用逗号

wolf
w
```
python格式化符号

|符号|描述|
|:------:|:---:|
| %c|字符及其ASCII码|
| %s|字符串|
| %d|整数|
| %u|无符号整型|
| %o|无符号八进制数|
| %x %X|无符号十六进制数（大小写）|
| %f|浮点数字，可指定小数点后的精度|
| %e %E|用科学计数法格式化浮点数（大小写）|
| %g %G|%f、%e和%f、%E的简写|
格式化操作符辅助指令:

|符号|描述|
|:------:|:---:|
|*|定义宽度或者小数点精度|
|-|左对齐|
|+|显示正负号|
|<<sp>sp>|在正数前面显示加号（+）|
|#|在八进制数前显示（0），在十六进制数前显示（0x）或（0X）|
|0|显示的数字前面填充'0'而不是默认的空格|
|%|'%%'输出一个单一的'%'|
|(var)|映射变量(字典参数)|
|m.n.|m 是显示的最小总宽度,n 是小数点后的位数(如果可用的话)|
###### 2.4.2 元组的访问
元组的访问主要包括两种方式：索引（index）和切片（slice）。  
1）索引可以称为下标，例如tuple[0]表示元组tuple的第1个元素，tuple[-1]表示元组tuple的最后一个元素。
2）切片方法是提取元组的部分，例如tuple[1:3]表示从第2个元素开始，到第4个元素结束，不包含第4个元素，是半开区间。tuple[:]返回整个元组，tuple[:-1]返回除最后元素的整个元组。
```Python
zoo=('wolf','elephant','penguin')
print('Number of animals in the zoo is',len(zoo))

Number of animals in the zoo is 3

new_zoo=('monkey','dolphin',zoo)
print('Number of animals in the new_zoo is',len(new_zoo))
print('All animals in new zoo are',new_zoo)
print('Animals brought from old zoo are',new_zoo[2])
print('Last animal brought from old zoo is',new_zoo[2][2])

Number of animals in the new_zoo is 3
All animals in new zoo are ('monkey', 'dolphin', ('wolf', 'elephant', 'penguin'))
Animals brought from old zoo are ('wolf', 'elephant', 'penguin')
Last animal brought from old zoo is penguin
```
###### 2.4.3 元组的“打包”和“解包”
创建元组的过程为“打包”，将元组中各个元素赋值给多个变量的过程为“解包”。
```Python
zoo=('wolf','elephant','penguin')
#打包过程

a,b,c=zoo
print('a=',a)
print('b=',b)
print('c=',c)
#解包过程，变量的个数与元组元素个数相同，否则出错

a= wolf
b= elephant
c= penguin

```
##### 2.5 字典
##### 2.5.1 字典的创建
字典是使用（key-value）来表示的内置数据结构，表示方法如下：  
**d={key1:value1,key2:value2}**   
其中，   
1）键和值之间使用冒号隔开   
2）各个键-值对之间使用逗号隔开  
3）所有的键-值都在大括号{}内
```Python
dict={'No.1':'History','No.2':'Chinese','No.3':'English'}
print(dict)

print('%s,%(No.2)s,%(No.3)s'%dict)
#%s表示整个字典，%(No.2)s表示键为No.2的值

{'No.1': 'History', 'No.3': 'English', 'No.2': 'Chinese'}
{'No.1': 'History', 'No.3': 'English', 'No.2': 'Chinese'},Chinese,English
```
##### 2.5.2 字典的访问
```Python
dict={'a':'History','b':'Chinese','c':'English'}
print(dict['c'])
dict['c']='electics'
#改变值
print(dict)
dict['d']='Mathematics'
#增加
print(dict)
del(dict['a'])
#删除
print(dict)
print(dict.pop('b'))
#返回‘b’的值并删除‘b’的键值对
print(dict)



{'b': 'Chinese', 'c': 'electics', 'a': 'History'}
{'b': 'Chinese', 'c': 'electics', 'a': 'History', 'd': 'Mathematics'}
{'b': 'Chinese', 'c': 'electics', 'd': 'Mathematics'}
Chinese
{'c': 'electics', 'd': 'Mathematics'}
```
##### 2.5.3 字典的方法
```Python
dict={'a':'History','b':'Chinese','c':'English'}
dict.clear()
#清空字典
print(dict)

dict={'a':'History','b':'Chinese','c':'English'}
print(dict.keys())
print(dict.values())
print(dict.get('a','electrics'))
print(dict.get('d'))
print(dict.get('d','electrics'))
#用get获得键的值，如果存在键则获得相应的值，若不存在则默认输出为NONE或者定义的值
print(dict)
dict2={'d': 'electics', 'e': 'Mathematics'}
dict.update(dict2)
#用update将dict2中的元素加到dict中
print(dict)

{}
dict_keys(['b', 'c', 'a'])
dict_values(['Chinese', 'English', 'History'])
History
None
electrics
{'b': 'Chinese', 'c': 'English', 'a': 'History'}
{'b': 'Chinese', 'd': 'electics', 'c': 'English', 'a': 'History', 'e': 'Mathematics'}
```
字符串、列表和元组的比较情况

|数据结构|元素是否可变|元素是否必须同一类型|句法|
|:---:|:---:|:---:|:---:|
|字符串|否|是|'world'|
|列表|是|否|[12,'world']|
|元组|否|否|('a',)|
### 3 变量
变量命名规则：

+ 变量名的首字母必须是英文字母（大小写均可），或下划线（ _ ）
+ 除首字母外，其他字符可以由英文字母、下划线或者数字组成
+ 变量名对大小写是敏感的

##### 3.1 变量赋值
python每一次新的赋值操作都将新建一个变量，即使变量名相同，但是变量的标识不同
```Python
salary = 2000
print(id(salary))

167012432

salary = 2000
print(id(salary))

167012624
```
python中可以一条语句中为多个变量进行赋值操作
```Python
a,b,c=2,5,8

print('a=',a)
a= 2

print('b=',b)
b= 5

print('c=',c)
c= 8
```
##### 3.2 全局变量
全局变量指的是能够被不同的函数、类或文件所共享的变量。全局变量可以被文件内的任何函数访问，也可以被外部文件访问。一般情况下，在函数块之外定义的变量都可以是全局变量。为了代码易读，最好在文件的开始位置定义全局变量。
```Python
salary1 = 2000  #定义全局变量
salary2 = 5000  #定义全局变量
def sum():
    global salary1
    salary1 = 2500  #重新定义全局变量
    print('salary1=',salary1)
    print('salary2=',salary2)
    return('salary1 + salary2',salary1 + salary2)

def sub():
    global salary2
    salary2 = 6000  #重新定义全局变量
    print('salary1=',salary1)
    print('salary2=',salary2)
    return('salary2 - salary1',salary2 - salary1)

sum()
salary1= 2500
salary2= 5000
Out[22]: ('salary1 + salary2', 7500)

sub()
salary1= 2500
salary2= 6000
Out[23]: ('salary2 - salary1', 3500)
```

```Python
salary1 = 2000  #定义全局变量
salary2 = 5000  #定义全局变量
def sum():
    salary1 = 2500  #定义局部变量
    print('salary1=',salary1)
    print('salary2=',salary2)
    return('salary1 + salary2',salary1 + salary2)

def sub():
    salary2 = 6000  #定义局部变量
    print('salary1=',salary1)
    print('salary2=',salary2)
    return('salary2 - salary1',salary2 - salary1)

sum()
salary1= 2500
salary2= 5000
Out[25]: ('salary1 + salary2', 7500)

sub()
salary1= 2000
salary2= 6000
Out[26]: ('salary2 - salary1', 4000)
```
最好是将所有变量放在单独的文件中，使用import语句导入，便于修改和管理
##### 3.3 局部变量
局部变量指的是只能在函数或者代码块范围内使用的变量，函数或者代码一旦结束，局部变量的生命周期也将结束。
```Python
def func(x):
    print('started x=',x)
    x=2
    print('changed x=',x)

x=50 #全局变量
func(x)
print('end x=',x)   #函数结束后局部变量不在起作用，全局变量的赋值起作用

started x= 50
changed x= 2
end x= 50
```
### 4 运算符和表达式
##### 4.1 赋值运算符
赋值运算时最简单的运算符，使用赋值符号“=”表示。
##### 4.2 算术运算符

|运算符|名称|说明|实例|
|:--:|:--:|:--:|:--:|
|+|加|两个对象相加|3+5输出8，'a'+'b'输出'ab'|
|-|减|负数或两个对象相减|-5.1为负数，50-24输出26|
|\*|乘|数相乘或字符串重复|2\*4输出8，'la'\*3输出'lalala'|
|/|除|两个数相除|13/3输出4.333333333333333|
|**|幂|x**y将返回x的y次幂|3**2输出9|
|%|取模|返回除法的余数|9%2输出1|
|//|整除|x除以y对结果向下取整数|13//3输出4，-13//3输出-5|
下表实例变量a值为字符串"Hello"，b变量值为"Python"：

|操作符|描述|实例|
|:------:|:---:|:---:|
|+|字符串连接|a + b 输出结果： HelloPython|
|\*|重复输出字符串|a*2 输出结果： HelloHello|
|\[  \]|通过索引获取字符串中字符|a[1]输出结果：e|
|[ : ]|截取字符串中的一部分|a[1:4] 输出结果 ell|
|in|如果字符串中包含给定的字符返回 True|H in a 输出结果 1|
|not in|如果字符串中不包含给定的字符返回 True|M not in a 输出结果 1|
|r或R|放置于字符串的引号前，按照字面来使用，转义字符失效|print (r'\n') 输出\n 和 print (R'\n') 输出\n|
|%|格式字符串||
```python
a='Hello';b='python'

a+b
Out[38]: 'Hellopython'

a*2
Out[39]: 'HelloHello'

a[1]
Out[40]: 'e'

a[1:4]
Out[41]: 'ell'
#从第2个元素到第5个元素，不包含第5个元素，半开区间

'H' in a
Out[43]: True

'M' not in a
Out[44]: True

print(r'/n')
/n

print(R'/n')
/n
```
##### 4.3 关系运算符
所有关系运算符返回的结果均为True或False。

|运算符|名称|说明|实例|
|:--:|:--:|:--:|:--:|
|<|小于|x< y,返回x是否小于y|5<3输出False|
|>|大于|x>y,返回x是否大于y|5>3输出True|
|<=|小于等于|x<=y,返回x是否小于等于y|3<=6输出True|
|\>=|大于等于|x>=y,返回x是否大于等于y|3>=6输出False|
|==|等于|对象是否相等|3==5输出False|
|!=|不等于|比较两个对象是否不等|2!3输出Ture|
##### 4.4 逻辑运算符

|运算符|名称|说明|实例|
|:--:|:--:|:--:|:--:|
|not|逻辑“非”|若x为True,则返回False，否则返回True|x=True;not x输出False|
|and|逻辑“与”|若x为False, x and y返回False，否则返回y的计算值|x=False；y=True;x and y输出False|
|or|逻辑“或”|若x为True, x or y返回True，否则返回y的计算值|x=True；y=True;x or y输出True|
##### 4.5 运算符优先级
python中的运算符优先级从小到大如下
```Python
lambda：Lambda表达式
if-else：条件表达式
or：逻辑或
and：逻辑与
not：逻辑非
in，not in：成员测试
is，is not：身份测试
<，<=，>，>=，!=，==：比较
|：按位或
^：按位异或
&：按位与
<<，>>：移位
+，-：加减运算
*，/，%：乘，除，取余
+x，-x：正负号
~x：按位翻转
**：指数
x[index]，x[index:index]，x(arguments)，x.attribute：小标，切片，调用函数，属性引用
(expressions...),[expressions...],{kys:value...}：绑定或显示元组，显示列表，显示字典
```
### 5 结构化程序设计
##### 5.1 条件语句(if...elif...else)
```Python
if (表达式1):
    语句1
elif（表达式2）:
    语句2
else：
    语句3
```
```Python
#-*-coding:UTF-8-*-
number=10
guess=int(input('Enter an integer:'))
#如果不加int，出来的是字符不是数字
if guess==number:
    print('Congratuations,you guess it.')
    print('but you do not win any prizes')
elif guess<number:
    print('No,it is a little bigger than that')
else:
    print('No,it is a little smaller than that')

print('Done')

Enter an integer:25
No,it is a little smaller than that
Done
```
##### 5.2 while循环
```Python
while (表达式)：
    ...
else：
    ...
```
```Python
number=10
running=True

while running:
    guess=int(input('Enter an integer:'))
    if guess==number:
        print('Congratuations,you guess it.')
        running=False
    elif guess<number:
        print('No,it is a little bigger than that')
    else:
        print('No,it is a little smaller than that')
else:
    print('The while loop is over.')
print('Done')

Enter an integer:12
No,it is a little smaller than that
Enter an integer:8
No,it is a little bigger than that
Enter an integer:10
Congratuations,you guess it.
The while loop is over.
Done
```
##### 5.3 for...in循环
```Python
for i in range(6):
    print(i)
else:
    print('the loop is over.')

for i in range(1,6):
    print(i)
else:
    print('the loop is over.')

for i in range(1,6,2):
    print(i)
else:
    print('the loop is over.')     

0
1
2
3
4
5
the loop is over.
1
2
3
4
5
the loop is over.
1
3
5
the loop is over.
```
##### 5.4 break语句和continue语句
```Python
while True:
    s = input('Enter something:')
    if s=='quit':
        break
    print('Length of the string is',len(s))
print('Done')

Enter something:hello python
Length of the string is 12

Enter something:you best
Length of the string is 8

Enter something:quit
Done
```
break 同样适用于for循环。
```Python
while True:
    s = input('Enter something:')
    if s=='quit':
        break
    if len(s)<3:
        print('Too small')
        continue
    print('Length of the string is',len(s))
print('Done')

Enter something:a
Too small

Enter something:b
Too small

Enter something:abc
Length of the string is 3

Enter something:quit
Done
```
continue跳过代码中的剩余语句，continue同样可以在for循环中使用。
### 6 函数
Python语言的源代码一般由函数（function）、模块（module）和包（package）组成。函数中包含可以重复调用的代码，通过输入参数返回计算结果；模块则是处理某一类问题的函数和类的集合；而包则是由一系列的模块组成的集合。

```graphLR
    A(包) --> B(模块1)
    A -->C(模块2...)
    A -->D(模块3...)
    B -->E(函数)
    B -->F(类)
```

##### 6.1 定义函数
```Python
def 函数名(参数1，参数2...):
    ...
    return
```
如果没有return语句，实际上每个函数在起末尾隐含一句return None。
##### 6.2 函数的形参和实参
定义函数是，圆括号中的参数称为形式参数（形参），与形参对应的的实际参数（实参），调用函数时给定的参数值就是实参。
```Python
def add(a,b):
    add=a+b
    print('the sum of a and b is:',add)
add(3,5)

the sum of a and b is: 8
```
可以事先制定某些参数值，即使用赋值符号（=）指定形参的默认值，d第一个形参不能指定默认值。
```Python
def say(message,times=1):
    print(message*times)

say('hello')
hello

say('hello',3)
hellohellohello   
```
```Python
def func(a,b=55,c=20):
    print('a is',a,',b is',b,',c is',c)

func(1)
a is 1 ,b is 55 ,c is 20

func(1,2)
a is 1 ,b is 2 ,c is 20

func(1,2,3)
a is 1 ,b is 2 ,c is 3
```
##### 6.3 函数的返回值
函数的返回使用return，如果return后不带任何语句，返回值为'None'。
```Python
def func(x,y,z):
    list1=[x,y,z]
    list1.reverse()#反转
    numbers=tuple(list1)#将list1封装成元组
    return numbers

a,b,c=func(2,5,6)
print('a=',a,'b=',b,'c=',c)

a= 6 b= 5 c= 2
```
##### 6.4 递归函数
Python语言允许函数调用自身，在函数内直接或者间接调用自身的函数称为递归函数。递归函数的实现分为递推和回归：  
1.递推：函数调用自身。每次调用都重新执行函数的代码，直到满足递归结束条件为止。  
2.回归：函数从后向前返回的过程。递归函数调用完毕，再按照相反的顺序逐级返回。   
阶乘是递归函数实现的典型例子。阶乘的计算公式如下：

$$
n!=
\begin{cases}
1&n=0\\
n*(n-1)!&n\ge1\\
\end{cases}
$$

1.首先根据条件判断n是否等于0，如果不等于0，每次递推调用函数时传入参数(n-1)。   
2.回归过程依次返回1!，2!...n!
```Python
def factorial(n):
    if n==0:
        return 1
    else:
        return n*factorial(n-1)

factorial(4)
print('4! is:',factorial(4))

4! is: 24
```
```sequence
4!->3!: 递推：4!=4*3!
3!->2!: 递推：3!=3*2!
2!->1!: 递推：2!=2*1!
1!->0!: 递推：1!=1*0!
0!->1!: 回归：1!
1!->2!: 回归：2!
2!->3!: 回归：3!
3!->4!: 回归：4!
```
##### 6.5 Lambda函数
lambda函数的功能是创建匿名函数。lambda函数中只能使用变量和表达式，不能使用条件判断语句和循环语句，格式如下：
**lambda variable1，variable2...：expression**
```Python
x=lambda x:x*x
print(x)
print(x(3))#x成为一个函数，(3)为函数变量
print((lambda x:x*x)(3))#lambda x:x*x也可以直接当做函数名，(3)为函数变量

#输出
<function <lambda> at 0x000000000AF82840>
9
9

def multi(a,b):
    sum=lambda a,b:a+b
    print('sum=',sum(a,b))
    sub=lambda a,b:a-b
    print('sub=',sub(a,b))
multi(5,3)

sum= 8
sub= 2
```
##### 6.6 Generator函数
通过列表生成式，我们可以直接创建一个列表。但是，受到内存限制，列表容量肯定是有限的。而且，创建一个包含100万个元素的列表，不仅占用很大的存储空间，如果我们仅仅需要访问前面几个元素，那后面绝大多数元素占用的空间都白白浪费了。所以，如果列表元素可以按照某种算法推算出来，这样就不必创建完整的list，从而节省大量的空间。在Python中，这种一边循环一边计算的机制，称为生成器（Generator）。
```Python
L = [x * x for x in range(10)]
L
Out[304]: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

g = (x * x for x in range(10))#把[]变为()
g
Out[306]: <generator object <genexpr> at 0x000000000AFD4FC0>

#可以用for...in的方式将g的各个元素输出
for i in g:
    print(i)
0
1
4
9
16
25
36
49
64
81
```
generator函数的功能是每次生成并输出1个数据项，一般用于for...in循环中对数据项进行遍历，也可用于迭代计算。格式如下：
```Python
def 函数名(变量):
    ...
    yield 表达式
```
generator函数与普通函数定义格式相同，区别是：generator函数用yield来返回生成的数据，普通函数用return返回数据，yield返回数据后继续执行程序，return返回数据后终止程序。
```Python
#斐波拉契数列推算
def fib(max):
    n,a,b=0,0,1
    while n<max:
        yield b
        a,b=b,a+b
        n=n+1

fib(6)
Out[312]: <generator object fib at 0x000000000AFB7B48>

for i in fib(6):
    print(i)
1
1
2
3
5
8     
```
##### 6.7 内置函数
常用的内置函数https://docs.python.org/3/library/functions.html#abs
```Python
abs, max, min, len, divmod, pow, round, callable,
isinstance, cmp, range, xrange, type, id, int()
list(), tuple(), hex(), oct(), chr(), ord(), long()
```
```Python
str = 'hello world'

str.capitalize()#首字母大写
Out[317]: 'Hello world'

str.replace("hello", "good")
Out[318]: 'good world'

ip = "192.168.1.123"#‘.’处分割

ip.split('.')
Out[320]: ['192', '168', '1', '123']
```
### 7 模块
  如果程序中需要重复调用某些函数，就可以编写模块来减少工作量。模块（module）是包含**变量、函数和类**的文件，一个Python文件（扩展名.py）就是一个模块。
##### 7.1 模块导入方式

- **import module_name**
上述导入模块 module_name 后调用模块中的函数，必须使用模块名作为前缀 module_name.func()。
- **from module_name import function_name**
上述语句表示从模块中导入函数function_name，使用时无需使用模块名作为前缀。
- **from module_name import ***
导入模块中所有类和函数。
- **from module_name import function_name as short_name**
如果导入模块的类或者函数名过长，可以使用as将类或者函数名命名为较短的别名。

*注意：不同模块中可能含有相同名的函数，最好使用import module_name，不会造成混淆。*
##### 7.2 sys模块
将以下源代码保存为hello.py文件，"E:\Python Test\hello.py"。hello.py中导入了sys模块，sys模块有一个argv变量，用list存储了命令行的所有参数。argv至少有一个元素，因为第一个参数永远是该.py文件的名称。

运行python hello.py获得的sys.argv就是['hello.py']；
运行python hello.py Michael获得的sys.argv就是['hello.py', 'Michael]。
```Python
# -*- coding: utf-8 -*-

import sys

args = sys.argv
if len(args)==1:
    print('Hello, world!')
elif len(args)==2:
    print('Hello, %s!' % args[1])
else:
    print('Too many arguments!')
```
在菜单-->电脑-->运行-->cmd中运行
C:\Users\Administrator>python "E:\Python Test\hello.py"
Hello, world!

C:\Users\Administrator>python "E:\Python Test\hello.py" china
Hello, china!

C:\Users\Administrator>python "E:\Python Test\hello.py" china people
Too many arguments!

##### 7.3 \_ \_builtin\_ \_模块
python 中有许多内置函数，本节只是介绍了部分函数的使用方法。
###### 7.3.1 filter()函数
filter() 函数用于过滤序列，过滤掉不符合条件的元素，返回一个迭代器对象，如果要转换为列表，可以使用 list() 来转换。
该接收两个参数，第一个为函数，第二个为序列，序列的每个元素作为参数传递给函数进行判，然后返回 True 或 False，最后将返回 True 的元素放到新列表中。
**filter(function, iterable)**
function为判断函数 iterable为可迭代对象
```Python
'输出奇数'
def is_odd(n):
    return n % 2 == 1

tmplist = filter(is_odd, [1, 2, 3, 4, 5, 6, 7, 8, 9, 10])
newlist = list(tmplist)'list转化为列表'
print(newlist)

[1, 3, 5, 7, 9]
```
```Python
'过滤出1~100中平方根是整数的数'
import math
def is_sqr(x):
    return math.sqrt(x) % 1 == 0

tmplist = filter(is_sqr, range(1, 101))
newlist = list(tmplist)
print(newlist)

[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```
###### 7.3.2 map()函数
**map(function, iterable1, ...)**     
map( )是 Python 内置的高阶函数，它接收一个函数（function） 和一个或多个序列 （iterable1, ...），并通过把函数 （function） 依次作用在序列（iterable1, ...）的每个元素上，得到一个新的序列并返回。多个序列长短必须相同。
```Python
# 计算平方数
def square(x) :           
...     return x ** 2
list(map(square, [1,2,3,4,5]))
Out[64]: [1, 4, 9, 16, 25]

 # 使用 lambda 匿名函数
list(map(lambda x: x ** 2, [1, 2, 3, 4, 5]))
Out[67]: [1, 4, 9, 16, 25]

# 两个序列相加
def plus(x,y):
    return x+y
list(map(plus, [1,2,3,4,5], [1,2,3,4,5]))
Out[69]: [2, 4, 6, 8, 10]
```
###### 7.3.3 reduce()函数
在 Python3 中，reduce() 函数已经被从全局名字空间里移除了，它现在被放置在 fucntools 模块里，如果想要使用它，则需要通过引入 functools 模块来调用 reduce() 函数。  
  **reduce(func,sequence[,initial])**   
如果给定初始值（initial），首先将initial传递到函数中进行计算，如果sequence为空，则对initial值进行计算。
```Python
from functools import reduce
def add(x,y):
    return x + y

#5+6+7+8+9   
print (reduce(add, range(5, 10)))
35

#11+5+6+7+8+9
print (reduce(add, range(5, 10),11))
46

#sequence为空
print (reduce(add, range(5, 5),11))
11

def func(x,y):
    return x * y

print (reduce(func, range(5, 10)))
15120

#2*5*6*7*8*9
print (reduce(func, range(5, 10),2))
30240

print (reduce(func, range(5, 5),2))
2
```
### 8 包

### 9 面向对象编程（类、对象、属性、方法、继承、多态性）
##### 9.1
### 10 文件
##### 10.1 文件的创建和打开
调用file()函数可以创建或者打开文件。格式如下：  
**file(name[,mode[,buffering]])-->file object**

+ 参数name为希望打开的文件名，如果不存在将创建一个文件并打开
+ 参数mode为文件打开的模式
+ 参数buffering为设置缓存的模式

文件打开模式

|参数|说明|
|---|---|
|r|以只读方式打开文件|
|r+|以读写的方式打开文件|
|w|以写入方式打开文件，首先删除文件原有信息，然后写入新信息；如果文件不存在，则创建一个新文件|
|w+|以读写方式打开文件，首先删除文件原有信息，然后写入新信息；如果文件不存在，则创建一个新文件|
|a|以写入方式打开文件，并在文件末尾追加新信息；如果文件不存在，则创建一个新文件|
|a+|以读写方式打开文件，并在文件末尾追加新信息；如果文件不存在，则创建一个新文件|
|b|以二进制方式打开文件，可以与r、w、a、a+联合使用，rb，rb+，wb，wb+，ab，ab+|
|U|支持所有的换行符号。例如，'\r''\n''\r\n'等表示换行|

##### 10.2 文件的读取和写入
读取文件的方法有3种：

+ 一次性读取文件中所有信息，调用read()方法，然后作为字符串或字节对象返回，f.read(size) 将读取一定数目的数据，size 是一个可选的数字类型的参数。
+ 按行读取文件中的信息，需要调用readline()方法，每次只读取文件中的一行信息，如果希望读取整个文件中的信息，则需要使用“while Ture：”表达式来循环读取文件，到文件末尾仍调用readline()则抛出异常信息，必须在循环中进行判断是否到达文件末尾，结束循环。
+ 一次读取文件中多行信息，需要调用readlines()方法，可以一次读取文件中多行信息。

##### 10.3 文件的删除和重命名

### 11 异常处理

##### 11.1 使用try...except测试异常

##### 11.2 使用raise语句引发异常

##### 11.3 自定义异常

##### 11.4 使用try...finally语句关闭文件
如果在读取文件的过程中，无论是否发生异常都希望关闭文件，则可以使用try...finally语句实现。
```Python
#只读方式打开一个文件，如果文件不存在将抛出错误
f = open('/path/to/file', 'r')
#可以一次读取文件的全部内容
f.read()
#文件使用完毕后必须关闭，因为文件对象会占用操作系统的资源，并且操作系统同一时间能打开的文件数量也是有限的
f.close()
#文件读写时都有可能产生错误，一旦出错，之后的f.close()就不会调用
try:
    f = open('/path/to/file', 'r')
    print(f.read())
finally:
    if f:
        f.close()
```
```Python
import time #导入time模块
try:
    f=file('happy.txt') #创建或打开
    while Ture:
        line=f.readline()
        if len(line)==0:
            break
        time.sleep(2)#程序暂停2秒
        print(line)
finally:
    file('happy.txt').close()
print('Cleaning up...closed the file')
```
### 参考资料
　　笔记主要内容是对Python学习的总结和整理，便于以后回顾和查询，所有的内容都是基于Python3，主要参考的资料有：   
[Python语言在Abaqus中的应用](https://www.amazon.cn/Python%E8%AF%AD%E8%A8%80%E5%9C%A8Abaqus%E4%B8%AD%E7%9A%84%E5%BA%94%E7%94%A8-%E6%9B%B9%E9%87%91%E5%87%A4/dp/B005HMMM2U/ref=sr_1_1?ie=UTF8&qid=1466221012&sr=8-1&keywords=Python+ABAQUS)  
http://blog.csdn.net/zouxy09/article/details/16920541   
[Python基础教程(第2版·修订版)](https://www.amazon.cn/%E5%9B%BE%E7%81%B5%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1%E4%B8%9B%E4%B9%A6-Python%E5%9F%BA%E7%A1%80%E6%95%99%E7%A8%8B-%E8%B5%AB%E7%89%B9%E5%85%B0/dp/B00KAFX65Q/ref=sr_1_1?ie=UTF8&qid=1466225831&sr=8-1&keywords=Python)   
http://www.runoob.com/python3/python3-tutorial.html http://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000
