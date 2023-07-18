# 一、变量和简单数据类型

## 每个变量指向一个值——与该变量相关联的信息——变量是可以赋给值的标签

变量名包含字母，数字，下划线，但不以数字开头

## 字符串

单引号和双引号都可以定义一个字符串，用单引号定义，句子中双引号看作普通符号，不需要转义，反之同理

## 方法——可对数据进行的操作

改变字符串大小写：

name.title()

 name.upper()

name.lower()

删除字符串空白：

name.rstrip()

name.lstrip()

name.strip()

列表：

**添加**：

list.append(元素) 将新元素添加到列表末**尾**

list.insert（位置，元素）添加到列表**中** a.insert(0,7) 将7这个新元素添加到列表a的第一个位置，即a[0]，原来的元素右移

**删除**：

list.pop(元素位置)  弹出列表中某个元素，并可继续使用他 如A是一个列表，a是其中第三个元素

b是一个变量，b=A.pop(2)等价于b=A[2]

list.remove(元素)当不知道元素位置时，使用此方法。不会像pop一样返回值。只删除列表中第一个指定的值，若该值在列表中出现多次，则需要多次删除。

**排序**：

list.sort()   永久性排序   list.sort(reverse=Ture) 反向排序，永久性

list.reverse()  反转列表元素原来的排列顺序 也是永久性 再次调用reverse即可返回原来的排序

## 字典：

get(指定键，指定键不存在时返回的值（可选)）

items()

keys()

values()

##  f字符串

在字符串中想要使用某个字符串变量的值来创建完整的消息，用大括号括起来变量

print（f”hello,{full_name.title()}!welcome to china!")

message=f”hello,{full_name.title()}!welcome to china!"

其中，full_name是一个字符串变量

## 数——整数，浮点数

书写很大的数时，利用下划线分组

age=14_0000_0000

全大写将某个变量视为常量，没有常量类型

# 二、列表

## []表示列表，逗号分隔元素，元素可以不是同种类型

a=['monday',7,8,5]

列表元素的索引从0 开始，类似数组

## 修改，添加，删除列表元素

修改——访问该元素，重新赋值  list[-a]表示访问倒数第a个元素

添加——方法append（），方法insert（）。

删除——del**语句**     del A[1]，删除第二个元素

pop()方法，remove()方法

## 组织列表

sort() 方法，按照某种方式

sorted()  函数进行临时排序 sorted(list,reverse=Ture) 对函数进行反向临时排序 按照某种方式

reverse（）方法 倒着排列列表 永久性

函数 len(list) 返回列表长度值

# 三、操作列表

## for循环，遍历整个列表

for 变量 in list***:***

​    注意缩进，执行操作

## 数值列表

range（）**函数** range(1,5)生成1，2，3，4   range(5) 从0开始生成0，1，2，3，4  range(2,11,2) 第三个参数为步长，生成2，4，6，8，10  

for num in range(n):可让这个for循环循环n次

list()**函数** 将range（）结果直接转化为列表

A=list(range(1,6)) print(A)   结果为[1,2,3,4,5]

### 对数值列表的统计运算函数——min(list)  max(list)  sum(list)

### 列表解析——将for循环和创建新元素的代码合并成一行——A=[values**2 for value in range(1,11)]

## 切片

list[1:4] 即创建包含list[1],list[2],list[3]的切片 

list[:4] 创建包含list[0]...list[3]的切片

list[2:] 创建包含list[2]...到最后一个元素的切片

list[-3:] 创建包含list列表中最后三个元素的切片

使用for循环课遍历切片：for a in A[-3:]:

### 复制列表——创建一个包含整个列表的切片

A=[.....]

B=A[:]

这样A B是两个相同的列表，但并非同一个列表

若A=[......]

B=A

这样实际上是让新变量B关联到已经与A相关联的列表，即A B指向同一个列表

## 元组——不能修改的值组成的列表称为元组

定义：tuple=（200，5，....）

元组由逗号标识，若只定义一个元素的元组，必须在元素后面加上逗号，如A=（3，）

可用for循环遍历元组

可以给元组变量重新赋值：

A=（1，2）

A=（3，4）

此时元组A中元素的值就是3和4 

# if语句

if （条件）：

  操作语句

每条if语句的核心都是一个值为Ture或False的表达式，这种表达式称为**条件测试**,别名布尔表达式。

在检测字符串是否相等时，区分大小写

利用**and**检查多个条件，想当于&&

利用**or**检测某个条件，相当于||

检查元素是否在列表中：if a (not) in list:

检查列表是否为空：if list:

if-else语句：

if ...：

   操作语句

else:

   操作语句

if-elif-else语句:elif相当于else if

如果只想执行一个模块的内容，利用if-elif-else语句；若要执行多个代码块，则使用一系列独立的if语句

#  字典——一系列键值对

alien_0={'color':'green','points':5}  每个键值对之间用**逗号**分开 只有一个键值对时**不需要加逗号**

指定字典名和放在方括号内的键 **alien_0['color'] 即获取与键相关联的值** 也可以对这个键**重新赋值**

字典是动态结构，可随时**添加键值对**，依次指定字典名，方括号括起来的键和相关联的值，如：

alien_0['position']=0 即在字典后又添加了一个新的键值对

Z={} 可以创建**空字典**

可使用del语句删除键值对，如：del alien_0['color']

可使用方法get(键)访问值 alien_0.get('points')

## 遍历字典

### 遍历所有键值对

for key,value in user_0.items():——方法items（）返回一个键值对列表

   print(f"Key：{key}")

### 遍历所有键

for key on user_0.keys():

按特定顺序遍历键：

for key in sorted (user_0.keys()):

### 遍历所有值

for value in users_0.values():

剔除重复项：

for value in set(users_0.values())

#### 集合

可使用花括号直接创建集合：

A={'ss','sss'} 不同于列表和字典，集合不会以特定的顺序存储元素

## 嵌套

### 字典列表——列表中存贮的元素都是字典

列表aliens，字典元素aliens_0,aliens_1...

for alien in aliens:    此时alien变量表示一个字典

​     alien['color']='yellow'  访问这个字典中的值

### 在字典中存贮列表——某个键对应的值是列表元素

### 在字典中存储字典——某个键对应的值是字典元素

# 输入和while循环

## 输入

input（提示）函数，读取字符串

利用函数int()获取数值输入

## while循环

while 条件：

  操作语句

break退出循环；continue返回循环开头

### 利用while循环处理字典和列表：

while list：即当列表不空的时候执行操作语句 

while 元素 in list：即当元素在列表中时执行操作语句 元素出现几次循环就执行几次，可用于删除元素

### 使用用户输入填充字典

responses={}

while Ture：

​    name=input("....")

​    response=input("....")

​    responses[name]=response

# 函数

def 函数名(形参):

   函数体

   return ....

## 实参

位置实参：

基于参数的顺序进行关联

关键字实参：

利用参数的名称值对进行传递

默认值只能放在参数最后，具有默认值的函数传递实参是可选的

例：

def FUNCTION(first,second,third='aaa')

   函数体

   return。。。

## 返回值

可以是简单值，也可以是列表，字典 可将返回值赋给变量

## 可以传递列表，在函数中访问和修改列表——永久性的

### 禁止函数修改列表——实参传递副本（形参不可以写切片）

## 传递任意数量的实参

def function(*tops):

星号创建名为tops的空元组，将实参封装到这个元组中

### 结合位置实参和任意数量实参：任意数量形参必须放在最后

def funtion(size,*tops):

### 使用任意数量的关键字实参——利用**创建空字典，也必须放在最后

# 模块

模块是扩展名 为.py的文件

导入模块：import moudle_name as m ——as是给模块命名别名的 别名是m

导入模块中特定函数：from moudle_name import function_name as f   这个函数的别名是f

from module_name import * 导入这个模块中所有函数，但可能造成函数重名现象

# 类

class A:

   def \_init_(self,first,second):

   def fun1(self):

   def fun2(self):

**A是类名,首字母大写，类中的函数叫做方法，self相当于this指针，必须位于其他形参的前面，属性即数据成员，\_init_()是构造函数**

## 创建实例：

my_dog=Dog('aaa',6)  会调用构造函数，传递参数对属性进行赋值

访问实例的属性和方法，都可利用**句点表示法**

无须利用实参定义的属性可以在构造函数中指定默认值，不需要在函数的形参中写出

修改属性的值可以利用句点表示法直接访问修改或者通过方法修改

## 继承

class Car:

def \_init_(self,a,b,c)

....

class Ecar(Car):

def \_init_(self,a,b,c)

​    super().\_init_(a,b,c)

​     子类自己的属性



super函数可以调用父类的方法

在子类中，可以重写父类的方法，同名覆盖

实例也可以用作属性

## 导入类——类似函数导入

# 文件

## 读取文件

with open('文件名'，'r') as f:

with是关键字，可以妥善打开和关闭文件

读取每行：

for line in f:
    line = line.strip()
    if line == '':
        continue

split方法可以分隔一行中的内容  a,b=line.split('分隔标识')

另外，readlines（）方法可以 读取每一行，并将他们存储在列表中

## 写入文件

with open('文件名'，'w') as f:     省略模式实参，将以只读打开文件

写入空文件：f.write('')方法  不会自动换行

**附加到文件下**：

with open('文件名'，'a') as f:

再利用write()方法









































