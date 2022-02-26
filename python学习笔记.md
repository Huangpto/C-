python学习笔记

###  print函数

| 输出目的地为显示器 |                                                   |                                                              |
| ------------------ | ------------------------------------------------- | ------------------------------------------------------------ |
| 输出数字           | print(520)   print(98.1)                          | 数字直接输出                                                 |
| 输出字符串         | print('hello')  print("hello")   print("'hello'") | 括号内加上单引号、双引号或三引号（用于告诉机器这个东西不用理解）、不可以不加引号 |
| 输出表达式         | print(3+1)    输出4                               | 3和1是操作数，+是运算符，表达式=操作数和运算符               |

ps:写注释  #

#### 将数据输出到文件中

```python
fp=open(’D:/text.txt’，’a+’)    #以读写的方式打开文件    如果D盘没有TEXT，则会新建   将其赋给一个变量fp
print('hello world',file=fp)    #将hello world输出到文件中    用file=
fp.close()                      #存储盘必须为C盘以外的其他盘
```

Ps:不进行换行输出   print（‘hello’，‘world’，‘python’）

a+的含义：如果文件不存在就创建，存在就在文件的内容后面追加

### 转义字符

转义字符就是反斜杠\加上想要实现的转移功能首字母

| 换行 | 回的 | 水平制表（一组四个位置） | 退格 |
| ---- | ---- | ------------------------ | ---- |
| \n   | \n   | \t                       | \b   |

水平制表：每四个字符就相当于一个\t   hello已经占用了一个\t了，因此，O后面只有三个空格

回车：print('hello\nworld')   在显示器上只显示world，回车回到前面的位置把hello挤掉了——覆盖、

\b：退格，退一格，把O删掉了

### 原字符

不希望字符串中的转义字符起作用，就是在字符串之前加上r或R

print(r‘hello\nworld')

注意事项，最后一个字符不能是反斜杠 （单引号前）   两个可以，三个也可以

### 二进制与字符编码

bit 8位（8个位置  一个字节）

Unicode把世界的字符都汇编在一起，每个字符对应一个编码，python字符串的编码格式

要在二进制前面加上0b才可以被识别

中文英文统称字符，在计算机中可以用十进制 二进制 八进制 十六进制表示，但是在计算机中只转换成二进制

### 保留字和标识符

保留字：有一些单词被赋予了特定意义，这些单词在你给任何对象起名字的时候都不能用(如:true false)

import keyword   

print(keyword.kwlist)

上述两行代码用于查找保留字

标识符:变量、函数、类、模块和其他对象起的名字

规则：同C语言   不能用保留字、区分大小写

### 变量的定义和使用

name='玛丽亚'

print(name)

变量由三部分组成

1.标识：表示对象所存储的内存地址，使用内置函数id(obj)来获取（如str)

2.类型：表示的是对象的数据类型，使用内置函数type（obj)来获取

3.值：表示对象所存储的具体数据，使用print(obj)可以将值进行打印输出

```python
name='玛丽亚'
print（’标识’，id(name))    #输出内存地址
print('类型'，type（name)) #输出数据类型
print('值'，name)      #打印输出值
#值  玛丽亚
```

### 常用数据类型

整数类型 int

|                | 基本数                                    | 逢几进一 | 表示形式      |                |
| -------------- | ----------------------------------------- | -------- | ------------- | -------------- |
| 十进制（默认） | 0，1，2，3，4，5，6，7，8，9              | 10       | 112           |                |
| 二进制         | 0，1                                      | 2        | -0b1110011111 | 以0b开头（0B） |
| 八进制         | 0，1，2，3，4，5，6，7                    | 8        | -0O166        | 以0o开头（0O)  |
| 十六进制       | 0，1，2，3，4，5，6，7，8，9，A,B,C,D,E,F | 16       | -0x11         | 以0x开头(0X)   |
|                |                                           |          |               |                |

```python
print（‘二进制’，0b1110011)  #输出二进制对应十进制的数
```

浮点数类型 float(3.1415926)

布尔类型 bool(True=1   False=0)   ——只可以取两个值，表示真或者假

```python
#布尔类型
f1=True
f2=False
print(f1,type(f1))
print(f2,type(f2))
#布尔值可以用整数计算
print(f1+1)
print(f2+1)
```

字符串类型 str  （人生苦短 ，我用python)——只要加上单引号，双引号，三引号都成为字符串类型（又称不可变的字符序列）

字符串：由0个或多个字符组成的有序字符序列

```python
k1='人生苦短，我用PYTHON'
k2="人生苦短，我用PYTHON"
k3="""人生苦短
我用PYTHON"""
k4='''人生苦短
我用PYTHON'''
print(k1,type(k1))
print(k2,type(k2))
print(k3,type(k3))
```

Ps：单引号和双引号定义的字符串必须在一行

三引号定义的字符串 可以分布在连续的多行    三个单引号和三个双引号

```python
#浮点类型
a=3.1415926
print(a,type(a))
n1=1.1
n2=2.2
print(n1+n2)       #运行结果是3.30000000000003 存储浮点数不精确
from decimal import Decimal        #解决方案 导入模块decimal
print(Decimal('1.1')+Decimal('2.2'))#3.3
```

### 数据类型转换

原因：将不同的数据类型拼接在一起

| 转换之前 | 转换之后 | 使用函数 |
| -------- | -------- | -------- |
| str      | int      | int()    |
| int      | float    | float()  |
| float    | str      | str()    |
| str      | float    | float()  |
| int      | str      | str()    |
| float    | int      | int()    |

```python
#这段代码报错，不清楚原因
name='张三'
age=20
#print('我叫'+name+'今年‘+age+'岁')错误写法    #不可以将字符串和整形数据进行连接    +是连接符
#解决方案：类型转换
print('我叫name今年，str(age)岁')   #将int类型通过str()函数转成了str类型
```

```python
print('-----------str()将其他类型转成str类型--------')
a=10
b=198.8
c=False
print(type(a),type(b),type(c))
print(str(a),str(b),str(c),type(str(a)),type(str(b)),type(str(c)))   #输出结果仍然是10，198.8，False
print('---------int()将其他的类型转int类型--------')

s1='128'
f2=98.7
s3='76.77'
ff=True
s4='hello'
print(type(s1),type(f2),type(s3),type(ff),type(s4))
print(int(s1),type(int(s1)))  #将str转成int，字符串为数字串
print(int(f2),type(int(f2))) #float转成int  只有整数部分
#print(int(s2),type(int(s3)))  #将str转成int不可以因为字符串为小数串
print(int(ff),type(int(ff)))
print(int(s4),type(int(s4)))  #将str转成int类型，字符串必须为整数数字串，非数字串不允许转换
```

| 函数    | 注意事项                                                     |
| ------- | ------------------------------------------------------------ |
| str()   | 也可用引号转换     str(123)='123'                            |
| int()   | 文字类和小数类字符无法转化成整数       str('123')     将str转成int类型，字符串必须为整数数字串，非数字串不允许转换 |
|         | 浮点数转化成整数，抹零取整                                   |
| float() | 文字类无法转成整数 float('9.9')输出结果9.9     如果字符串中发的数据是非数字串，则不允许转换 |
|         | 整数转成浮点数，末尾为.0                                     |

### 注释

单行注释：以#开头，直到换行结束    #单行注释

多行注释：并没有单独的多行注释标记，将一对三引号之间的代码成为多行注释     ’‘’多行

​                                                                                                                                          注释‘’‘

中文编码声明注释：在源文件开头加上中文声明注释，用以指定源码文件的编码格式

​            加上 #coding:gbk

### input函数的使用

1.作用：接受来自用户的输入

2.返回值类型：输入值的类型为str

3.值的存储：使用=对输入的值进行存储

input('大圣想要什么礼物呢？')——里面这句话是一句提示语，在显示器上显示，你仍可以输入你想要输入的数据并且存储到变量中

```python
#从键盘输入两个横竖，计算两个整数的和
a=input('请输入一个加数')
b=input('请输入另一个加数')
print(a+b)                           #输出结果是1020，说明加号在这里的作用是连接
#解决方案——看a和b的数据类型——运用类型转换
#从键盘输入两个横竖，计算两个整数的和
a=input('请输入一个加数')
a=int(a)
b=input('请输入另一个加数')
b=int(b)
print(a+b)
#解决方法2
a=int(input('请输入一个加数'))
b=int(input('请输入另一个加数'))
print(a+b)
```

### 运算符

PS：除法运算有小数位

除法运算：  /

整除运算： //（去掉小数部分，用.0代替）

幂运算：2**2    表示2的2次方

​               2***2   表示2的3次方

两个负数的整除：-9//-2=2

一正一负的整除：-9//4=-3     9//-4=-3     一正一负向下取整

​      #9除以-4结果为-2.2，向下取整，则取比-2.2小的数，则为-3



余数运算：

一正一负：余数=被除数-除数*商

9%-4=-3            =9-（-4）*（-3）=9-12=-3

-9%4=3             =-9-4*（-3）=3

赋值运算符：运算顺序从右到左

| 赋值方式 |                                   |
| -------- | --------------------------------- |
| 参数赋值 | +=、-=、*=、/=、//=、%=           |
| 解包赋值 | a,b,c=20,30,40   要求左右个数相同 |

用id()查看标识（内存地址）

a=b=c=20  只有一个整数对象，内存地址相同 a、b、c都指向这个内存地址

```python
#交换两个变量的值
print(a,b)
a,b=b,a
print(a,b)
#比较运算符
a=10,b=20
print(a>b)   #结果 False
print(a<b)   #结果  True
print(a==b)  #结果  False
print(a！=b) #结果  True
print(a<=b)  #结果  True
print(a>=b) #结果 False
#比较变量的标识
a=10,b=10     #a已经存储了地址，而到b的时候会在内存中看一下有没有10这个对象，也指向这个id
print(a==b)   #True
print(a is b)  #True
print(a is not b)  #False  a 和b的id不相等
```

一个变量由三部分组成；标识、类型、值

运算符比较的是值

比较对象的标识（id地址）：is

| 布尔运算符                                        运算数     | 结果      |
| ------------------------------------------------------------ | --------- |
| and                                        T  T  T F   F T   F F           print（a==1 and b==2) | T F F F   |
| or                                           T T   T F   F T   FF | T T T F   |
| not                                          T  F            | F T(取反) |
| in                                                           |           |
| not in                                                       |           |
| 后面两个运算符可以用于查看某个东西在不在某个东西之中         |           |

```python
s='hello world'
print('w' not in s)     #False
print('s' not in s)     #True
print('w' in s)          #True
print('s' in s)         #False
```

#### 位运算符

| 位运算符（将数据转成二进制进行计算）             |         |
| ------------------------------------------------ | ------- |
| 位与&   ——对应位数都是1，结果数位才是1，否则为零 |         |
| 位或I    ——对应位数都是0，结果数位才是0，否则为1 |         |
| 左移运算符<<      ——高位溢出舍弃，低位补0        | 左移 位 |
| 右移运算符>>      ——低位溢出舍弃，高位补0        | 右移 位 |

八进制，八个位置，前面位置没占满，需要补0

```
#  4的二进制  100——00000100
#  8的二进制  1000——00001000
#比较，对应位数，可知比较后为 00000000即0
print(4&8)    # 0
print(4|8)    #00001100对应12
print(4<<1) #向左移动一个位置
print(4<<2) #向左移动两个位置
print(4>>1) #向右移动一个位置
print(4>>2) #向右移动两个位置
```

| 左/右移运算符                         |      |      |      |      |      |      |          |
| ------------------------------------- | ---- | ---- | ---- | ---- | ---- | ---- | -------- |
| 0                                     | 0    | 0    | 0    | 0    | 1    | 0    | 0        |
| 0（前一位零已经溢出，舍弃）           | 0    | 0    | 0    | 1    | 0    | 0    | 0（补0） |
| 0                                     | 0    | 0    | 0    | 0    | 1    | 0    | 0        |
| 0（高位补零，后面低位超出的就舍弃了） | 0    | 0    | 0    | 0    | 0    | 1    | 0        |

向左移动一位相当于乘以2   4变成8

向右移动一位相当于除以2   4变成2

#### 运算符的优先级（有括号先计算括号）

算数         幂运算 

运算         先乘除后加减 * / // % + -

符          左右移位  <<  >>

位运算符     & I

比较运算符       <  >   >=    <=    ==    !=

 布尔                and    

  运算               or   

​    赋值运算    

### 程序的调试

在行号旁边打一个断点（点击），找小虫子，点击下一句的图标          

### 程序的组织结构

       ### 顺序结构

PS：对象的布尔值：python一切皆对象，所有对象都有一个布尔值（即True或False），获取对象的布尔值，使用内置函数bool()

以下对象的布尔值为False：

False、数值（）、None、空字符串、空列表、空元组、空字典、空集合

其他的都为True

```  python
#测试对象的布尔值
print(bool(False))
print(bool(0))
print(bool(0.0))
print(bool(None))
print(bool(''))       #空字符串
print(bool(""))       #空字符串（只有单引号或者双引号）
print(bool([]))       #空列表
print(bool(list()))   #空列表
print(bool(tuple()))  #空元组
print(bool({}))
print(bool(dict()))   #空字典
print(bool(set()))    #空集合
```

### 单分支结构

###   语法结构

###              if 表达式：

```python
money=1000   #余额
s=int(intput('请输入取款金额'))      #取款金额
if money>=s:
    money=money-s
    print('取款成功，余额为：',money)
```



### 双分支结构(二选一执行)

### 语法结构

```python
if条件表达式：
  条件执行体1
else：
   条件执行体2
```

```python
num=int(input('请输入一段整数'))
if num%2==0:
    print('是偶数')
else:
    print('是奇数')
```

### 多分支结构

```python
if 条件表达式1：              #由表达式1一直判断到最后
  条件执行体1
elif 条件表达式2：
  条件执行体2
elif 条件表达式N：
  条件执行体N
else:
  条件执行体N+1
```

```python
score=int(input('请输入一个成绩'))
if score>=90 and score<=100:
    print('A')
elif score>=80 and score<=89:
    print('B')
elif score>=70 and score<=79:
    print('C')
elif score>=60 and score<=69:
    print('D')
elif 0<=score<=59:   #只有在python才可以这样表达 其他语言不可
    print('E')
else:
    print('请重新输入')
```

### If的嵌套

```
if 条件表达式1：
  if 内层条件表达式：
    内存条件执行体1
  else:
    内存条件执行体2
else:
  if 内层条件表达式：
    内存条件执行体1
  else:
    内存条件执行体2
```

### 条件表达式（结合对象的布尔值判断，尤其是0——False)

条件表达式是if...else 简写

语法结构：       X   if    判断条件 else y

运算规则：

如果判断条件的布尔值为True，执行X；如果为False，则执行y

```python
'''num_a=int(input('请输入第一个整数'))
num_b=int(input('请输入第二个整数'))
if num_a>=num_b:
    print(num_a,'大于等于',num_b)
else:
    print(num_a,'小于',num_b)'''
print('用表达式进行比较')
num_a=int(input('请输入第一个整数'))
num_b=int(input('请输入第二个整数'))
print((num_a,'大于等于',num_b) if num_a>=num_b else (num_a,'小于',num_b) )     #(11, '小于', 22)
print(str(num_a)+'大于等于'+str(num_b) if num_a>=num_b else str(num_a)+'小于'+str(num_b))
#用加号进行字符串连接必须转换成str类型，用str()的意思不是数字变成文字，字符串也包括数字在内
```

### Pass语句

Pass语句什么都不做，只是一个占位符，用在语法上需要语句的地方

什么时候用：先搭建语法结构，还没想好代码怎么写的时候

那些语句一起使用：

if语句的条件执行体

for-in语句的循环体

定义函数时的函数体

```python
answer=input('您是会员吗？y/n')
if answer=='y':
    pass
else:
    pass
```

### range函数的使用

内置函数range()——前面不加任何前缀，可以直接使用的一个函数

用于生成一个整数序列

### 创建range对象的三种方式（记住存储到一个对象中）

1. range(stop)——创建一个[0,stop)之间的整数序列，步长为1
2. range(start,stop)——创建一个[start,stop)之间的整数序列，步长为1
3. range(start,stop,step)——创建一个[start，stop)之间的整数序列，步长为step

返回值是一个迭代器对象——创建之后看不到数据，如果想要看到数据，需要使用list函数

```python
r=range(10)
print(r)
print(list(r))   #用于查看range对象中的整数序列，list是i列表
#[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]默认从0开始，默认相差1（步长）
r=range(1,10)
print(list(r))
r=range(1,10,2)
print(list(r))
'''判断指定的整数在序列中是否存在  in,not in'''
print(10 in r)     #结果为False，10不在r序列中
print(9 in r)
print(10 not in r)
print(9 not in r)
```

range类型的优点：不管range对象表示的整数序列有多长，所有range对象占用的内存空间都是相同的，因为仅仅需要存储start,stop,step，只有用到range对象时，才会去计算序列中的相关元素

in和not in判断整数序列中是否存在（不存在）指定的整数

### 循环结构

分类：while    for-in

语法结构 ：

while 条件表达式：

​    条件执行体（循环体）



选择结构的if和循环结构while的区别

if是判断一次，条件为True执行一行

while是判断n+1次，条件为True执行N次（执行完语句之后，又回去判断条件是否成立）

while循环的执行流程（四部循环法）——初始化的变量与条件判断的变量与改变的变量为同一个

  初始化变量、条件判断、条件执行体（循环体）、改变变量

```python
sum=0
a=1
while a<=100:
    if a%2==0:     #偶数和
        sum+=a
    a+=1
print(sum)

sum=0
a=1
while a<=100:
    if a%2:     #a为偶数布尔值为0 所以计算不进行if语句内的操作
        sum+=a
    a+=1
print(sum)

sum=0
a=1
while a<=100:
    if not bool(a%2):    #取反，当a为偶数，布尔值为真，进行if语句的计算
        sum+=a
    a+=1
print(sum)
```

### for-in循环

in表达从（字符串、序列等）中依次取值，又称为遍历

for-in遍历的对象必须是可迭代对象

#### 语法结构

for 自定义的变量 in 可迭代对象：

​      循环体

循环体内不需要访问自定义变量，可以将自定义变量替代为下划线

目前可迭代对象有序列、字符串

```python
for item in 'python':
    print(item)       #从字符串中取出每一个字母进行输出，并赋给item，并输出item
    #P y t h o n
for r in range(10):     #打印 0 1 2 3 4 5 6 7 8 9
    print(r)
    #循环体内不需要访问自定义变量，可以将自定义变量替代为下划线
for _ in range(5):      #循环执行5次
    print('人生苦短，我用python')   
```

```python
#使用for循环，计算1——100之间的偶数和
sum=0
for item in range(1,101):
    if item%2==0:
        sum+=item
print(sum)
#输出100——999之间的水仙花数
'''153=1*1*1+5*5*5+3*3*3'''
for item in range(100,1000):
    ge=item%10
    shi=item//10%10
    bai=item//100
    if(ge**3+shi**3+bai**3==item):
        print(item)
```

### 流程控制语句break

用于结束循环结构，通常与分支结构if一起使用

for ... in...:

   ...

  if ...:

​      break



while 条件：

​      ...

if ...:

​      break

```python
for item in range(3):      #循环三次 0 1  2
    pwd=input('请输入密码：')
    if pwd=='8888':          #判断语句一定要在常量那加上单引号
        print('密码正确')
        break
    else:
        print('密码不正确')

item=0
while item<3:
    pwd=input('请输入密码')
    if pwd=='8888':
        print('密码正确')
        break
    else:
        print('密码不正确')
    item+=1
```

### 流程控制语句continue

用于结束当前循环，进入下一次循环，通常与分支结构中的if一起使用

for ... in...:

   ...

  if ...:

​      continue



while 条件：

​      ...

if ...:

​      continue

```python
for item in range(1,51):
    if item%5!=0:     #记得加上冒号
        continue
    else:
        print(item)
```

### else语句

if...:          #if表达式不成立时执行else

   ...

else:

   ...



while...:        #没有碰到break时执行else  循环的正常次数执行完就会执行else

   ...

else:

   ...



for...:

   ...

else:

   ...

```python
for item in range(3):
    pwd=input('请输入密码：')    #input前面不能加上int()函数，否则会报错
    if pwd=='8888':
        print('密码正确')
        break
    else:
        print('请重新输入密码')
else:        #与for-in搭配
    print('三次密码均使用错误')
    
a=0
while a<3:
    pwd=input('请输入密码：')
    if pwd=='8888':
        print('密码正确')
        break
    else:
        print('请重新输入密码')
    a+=1
else:
    print('三次密码军输入错误')
```

```python
print()      #换行
print(3)
print()       #换行
print(1)
#输出一个三行四列的矩形
for i in range(1,4):
    for j in range(1,5):       #不换行输出
        print('*',end='\t')    #end='\t'表示空格 注意，此处为反斜杠
    print( )          #每一行输出完成之后换行
#打印一个直角三角形
for i in range(1,10):
    for j in range(1,i+1):
        print('*',end='\t')
    print()
    
for i in range(1,10):
    for j in range(1,i+1):
        print(i,'*',j,end='\t')
    print()
```

### 二重循环中的break和continue用于控制本层循环

break：推出内层循环

continue：继续执行本层循环，只是推出了该次循环，对内层循环没有影响

```python
for i in range(5):       #代表外层要执行5次
    for j in range(1,11):
        if j%2==0:
            break     #退出当前循环结构 循环，执行完本次循环，不进行下一次循环
        print(j)     #再缩进两格是因为在if层下会被认为是当前语句

for i in range(5):
    for j in range(1, 11):
        if j%2==0:
            continue      #退出该次循环
        print(j,end='\t')
    print()
```

### 列表

#### 为什么需要列表

1.变量可以存储一个元素，而列表是一个“大容器”可以存储N多个元素，程序可以方便地对这些数据进行整体基本操作

2.列表相当于其它语言中的数组



可以存储不同类型的数据

变量存储的是对象的ID值（地址）——存储对象的引用地址

变量：ID+类型+值

```python
a=10
lst=['hello','world',11]
print(id(lst))       #查看列表的地址
print(type(lst))     #查看列表的类型(list)
print(lst)           #输出列表
```



#### 列表的创建（使用中括号、调用内置函数list()以及列表生成式)

列表需要使用中括号[],元素之间使用英文的逗号进行分隔,且需要赋值给对象（变量）还有赋值运算符

lst=list(['hello','world',11])

['F','f']

 变量实际上存储的是列表的ID

```
lst=list(['hello','world',11])
print(lst)
```

#### 列表的特点

1.列表元素按顺序有序排序

2.索引映射唯一一个数据      lst[0]——从前往后索引      lst[-1]——从后往前索引 依次为-1、-2

索引：返回字符串中的单个字符    使用[]获取字符串中的一个或多个字符

```python
#TempConvert.py
TempStr=input("请输入带有符号的温度值：")
if TempStr[-1] in ['F','f']:    #[]获取字符串中一个或多个字符 <>[m]
    C=(eval(TempStr[0:-1])-32)/1.8
    print("转换后的温度是{:.2f}C".format(C))
elif TempStr[-1] in ['C','c']:
        F=1.8*eval(TempStr[0:-1])+32
        print("转换后的温度是:{:.2f}F".format(F))
else:
    print("输入格式错误")
'''     ''输入带有符号的温度值’‘[0]   #索引第一个字符'''
```

3.列表可以存储重复数据

4.任意数据类型混储

5.根据需要动态分配内存和回收内存

```python
lst=list(['hello','world',11])
print(lst)
print(lst[0],lst[-3])
```

#### 列表的查询操作

获取列表中指定元素的索引——index

1.如果列表中有 相同元素值返回列表中相同元素的第一个元素的索引

2.如果查询的元素在列表中不存在，则会抛出ValueError

3.还可以在指定的start和stop之间进行查找

```python
lst=list(['hello','world','hello',11])
print(lst.index('hello'))      #中间使用的是实心点
#print(lst.index('python'))
#print(lst,index('hello',1,3))        #不包括3
print(lst.index('hello',1,4))
```

#### 获取列表中的单个元素

1.正向索引从0到N-1         举例：lst[0]    lst[N-1]

2.逆向索引从-N到-1          举例：lst[-N]    lst[-N]

3.指定索引不存，抛出IndexError

#### 获取列表中的多个元素

语法格式：    列表名[start:stop:step]

##### 切片操作

切片的结果：返回字符串中一段字符子串   <    字符串>[M：N]

切片的范围：[start，stop）——切出来之后变成一个新的列表对象，另存，只拷贝对象，不拷贝ID

 step默认为1：简写为[start,stop]

step为正数：[:stop:step]:切片的第一个元素默认是列表的第一个元素

​                       [start::step]——切片的最后一个元素默认是列表的最后一个元素

​          从start开始往后计算切片

step为负数：[:stop:step]——切片的第一个个元素默认是列表的最后一个元素

​                       [start::step]——切片的最后一个元素默认是列表的第一个元素

​          从start开始往前计算切片

```python
lst=[10,20,30,40,50,60,70,80]
print('原列表',lst)
print('原列表',id(lst))
lst2=lst[1:6:1]
print('切的片段',id(lst2))
print(lst[1:6])  #默认步长为1
print(lst[1:6:])
print(lst[1:6:2]) #步长2
print(lst[:6:2]) #默认从0开始
print(lst[1::2])
print('步长为负数的情况')
print(lst[::-1])    #逆序输出
print(lst[7::-1])
print(lst[6:0:-2])  #不包括lst[0]
```

#### 列表元素的查询操作

判断指定元素在列表中是否存在

​      元素  in   列表名

​      元素  not in 列表名

#### 列表元素的遍历

for 迭代变量 in 列表名：

​      操作

```python
lst=[10, 20,30,40,50,60,70,80]
print(10 in lst)
print(100 in lst)
print(10 not in lst)
print(100 not in lst)
#遍历列表中的元素
for item in lst:
    print(item)
```

#### 列表元素的增加操作

| 增加操作 | 切片     | 在列表的任意位置添加至少一个元素 |
| -------- | -------- | -------------------------------- |
|          | append() | 在列表的末尾添加一个元素         |
|          | extend() | 在列表的末尾至少添加一个元素     |
|          | insert() | 在列表的任意位置添加一个元素     |

```python
lst=[10, 20,30]
print(id(lst))
lst.append(100)
print(lst)
print(id(lst))     #标识都相同，说明没有创建新的列表对象
#lst指向的id首都一样，只不过尾巴会加上int相对应的字节
lst2=['hello','world']
lst.append(lst2)     #把lst2整体作为一个元素放到了lst中
print(lst)
lst.extend(lst2)    #把lst2中的每一个元素都单独放到lst的末尾，一次性添加多个元素
print(lst)
#在任意位置上添加一个元素
lst.insert(1,90)
print(lst)
#切片,在任意位置上添加N多个元素
lst3=[True,False,'hello']
lst[1:]=lst3  #没有结束，说明一直到最后一个元素都会被删掉，没有步长，用等于号
print(lst)    #删除的部分用新的列表去替换
```

#### 列表元素的删除操作

| remove（） | 一次删除一个元素、重复元素值删除第一个、元素不存在抛出ValueError |
| ---------- | ------------------------------------------------------------ |
| pop()      | 删除一个指定索引位置上的元素、指定索引不存在抛出IndexError（超出索引范围）、不指定索引，删除列表中的最后 一个元素 |
| 切片       | 一次至少删除一个元素                                         |
| clear()    | 清空列表（会产生新的列表对象）                               |
| del        | 删除列表                                                     |



```python
lst=[10, 20,30,40,50,60,30]
lst.remove(30)   #以列表中移除一个元素，如果有重复元素只移除第一个元素
print(lst)
lst.pop(1)
print(lst)
lst.pop()  #如果不指定参数（索引），将删除列表中的最后一个元素
print(lst)
#切片——会产生一个新的列表对象
newlst=lst[1:3]
print('原列表',lst)       #原列表不发生任何改变
print('切片后的列表',newlst)
#如何用切片使其不产生新的列表对象，但是删除原列表的内容
lst[1:3]=[] #用空列表替代，[1,3）的位置
print(lst)
#清楚列表中的所有元素
lst.clear()
print(lst)
#del将列表对象删除
del lst
print(lst)
```

#### 列表元素的修改操作（改变指向的ID）

为指定索引的元素赋一个新值

为指定的切片赋予一个新值



```python
lst=[10,20,30,40]
#一次修改一个值
lst[2]=100
print(lst)
lst=[10,20,30,40]
#一次修改一个值
lst[2]=100
print(lst)
lst[1:3]=[300,400,500]   #把20、30去掉，用300、400、500替代
print(lst)
```



#### 列表元素的排序操作

常见的两种方式

1.调用sort（）方法，列表中的所有元素默认按照从小到大的顺序进行排序，可以指定reverse=True，进行降序排序

2.调用内置函数sorted()，可以指定reverse=True，进行降序排序，原列表不发生改变——会产生新的列表对象，原列表不发生任何改变

PS：内置函数，啥都不需要，直接拿过来用

```python
lst=[20,40,10,98,54]
print('排序前',lst)
lst.sort()
print(lst)
#用id()可以知道没有产生新的列表，因为一样
#排序是在原来的基础上进行的
#通过指定关键字参数，将列表中的元素进行降序排序
lst.sort(reverse=True)    #降序排序
print(lst)
lst.sort(reverse=False)   #升序排序
print(lst)
print('使用内置函数进行排序')
lst=[20,40,10,98,54]
newlist=sorted(lst)
print(newlist)
#指定关键字参数，实现列表参数的降序排序
desc_list=sorted(lst,reverse=True)
print(desc_list)
up_list=sorted(lst,reverse=False)
print(up_list)
```

#### 列表生成式（生成列表的公式）------列表中的元素要有一定的规则

语法格式：   [i*i for i in range(1,10)]

range(1,10) 会产生一个1-9的整数序列

```python
lst=[i for i in range(1,10)]  #方括号中存的是产生的整数序列，整数序列是i，列表中存储的就是i的值
print(lst)
lst2=[i*i for i in range(1,10)]  #i*i的意思就是表面意思   i*i被称为表示列表元素的表达式(列表中真正包含的那个元素的值)
print(lst2)
lst3=[i*2 for i in range(1,6)]
print(lst3)
```

### 字典

python内置的数据结构之一，与列表一样是一个**可变序列**（可以执行增删改操作）

以键值对的方式存储数据，字典是一个无序的序列，列表是一个有序序列其中序指的是排列，第一个放进列表的就在第一个位置上

scores={'张三'：100，'李四'：98}冒号之前称为键，冒号之后称为值，即键值对

字典需要经过哈希函数计算key再决定存储位置，因此放在字典当中的键必须是一个不可变序列，如int,str，不可执行增删改操作

​     eg：s='hello'  如果想要给s再加上一个python，那就重新开辟一段存储空间'hello python'

字典的实现原理：字典的实现原理与查字典类似，python中字典是根据使用hash函数计算key查找value所在的位置

#### 字典的创建

最常用的方式：

使用花括号        scores={'张三'：100，'李四'：98}  #记得存储到变量当中

使用内置函数     dict(name='jack',age=20)

```python
scores={'张三':100,'李四':98}
print(scores)
print(type(scores))

student=dict(name='jack',age=20)    #等号左侧是键，等号右侧是值，字符串记得加上单引号、赋值给变量
#{'name': 'jack', 'age': 20}    #只要是字符串都会有单引号
print(student)

#空字典
d={} #无键值对
print(d)
```

#### 字典中元素的获取

一： []  举例：scores['张三']

二：get()   举例：scores.get('张三')

区别：

[]如果字典中不存在指定的key，抛出keyError异常（键不存在）

get()如果字典中不存在指定的key，并不会抛出keyError而是给出None，可以通过参数设置默认的value，以便指定的key不存在时返回value的值

```python
scores={'张三':100,'李四':98}
print(scores['张三'])   #给出丈夫输出妻子
print(scores.get('张三'))
print(scores.get('麻七',99))  #99是在查找'麻七’所对的value不存在时，提供的一个默认值
```

#### key的判断

in   ——指定的Key在字典中存在返回True——'张三' in scores

not in ——指定的key在字典中不存在返回True——'Marry' not in scores

#### 字典元素的删除

del scores['张三']

#### 字典元素的新增、修改

scores['Jack']=90

```python
scores={'张三':100,'李四':98}
print('张三' in scores)
print('张三' not in scores)
print('Marry' in scores)
del scores['张三']
print(scores)
scores.clear()      #清空所有元素
print(scores)
scores={'张三':100,'李四':98}
scores['陈六']=98
print(scores)
scores['陈六']=100    #也可以相当于修改
print(scores)
```

#### 获取字典视图的三个方法

keys()——获取字典中所有的key

values()——获取字典中所有value

items()——获取字典中所有的key，value对

```python
scores={'张三':100,'李四':98}
keys=scores.keys()
print(keys)  #视图
print(type(keys))    #keys类型
print(list(keys))    #转换成由键组成的列表
values=scores.values()
print(list(values))
print(type(values))   #values类型
items=scores.items()
print(items)    #dict_items([('张三', 100), ('李四', 98)])——被一组方括号括起来了方括号是原组的意思
print(list(items))  #[('张三', 100), ('李四', 98)]两个元素，每个元素是一组元组（）
```

#### 字典元素的遍历

for item in scores:

   print(item)       #输出的是键

```python
scores={'张三':100,'李四':98}
for item in scores:
    print(item) #输出键

for item in scores:
    print(item,scores[item],scores.get(item))
```

#### 字典的特点

1.都是键值对

2.key不允许重复，value可以重复  

3.元素是无序的

4.key重复会出现值覆盖的情况

5.key必须是不可变对象——int str （列表是可变的）

6.字典可以根据需要动态地伸缩

7.字典会浪费较大的内存——存放位置之间可能会有很多个空没存放，是一种使用空间换时间的数据结构

字典会根据键去计算存储位置

```python
scores={'张三':98,'张三':100}
print(scores)
scores={'张三':98,'Marry':98}
print(scores)
lst=[10,20,30]
lst.insert(1,100)
print(lst)
```

#### 字典生成式

内置函数zip()

用于将可迭代的对象作为参数，将对象中对应的元素打包成一个元组，然后返回由这些元组组成的列表

现在有两个列表 items=[‘fruit','books','others']

​       prices=[96,78,85]  把items作为key，prices作为values

如果key和value个数不相等，那么zip()在打包的时候就会元素少的为基准

```python
items=['Fruit','Books','Others']
prices=[10,20,30]
d={item:price  for item ,price in zip(items,prices)}  #item是单数，代表单个的意思
    #items:prices 表示遍历的items是键，prices是做值的
print(d)
d={item.upper():price for item ,price in zip(items,prices)}    #大写item.upper()
print(d)
```

### 元组（数据结构）

定义：python的数据结构之一，是一个不可变序列

可变序列：列表、字典   可以对序列执行增、删、改操作，对象地址不发生更改

不可变序列：字符串、元组  没有增、删、改操作，**操作之后对象地址发生改变**

语法结构：

t=('python','hello',90)   括号内的元素就是元组的内容——与列表的区别仅在于一个是方括号，另一个是（）

#### 元组的创建方式——输出括号全部内容，原封不动

t=（‘python','hello',90）

使用内置函数tuple    t=tuple( ('python','hello',90) )

只包含一个元组的元素需要使用逗号和小括号  t=(10,)  ,如果不加上逗号，计算机会以为这是他本身的数据类型，哪怕你加上括号了如10 int

```python
t=('python','hello',90)
print(type(t))
print(t)
t=tuple(('python','world',98))
print(t)
print(type(t))
t2='python','world',98    #省略了小括号也可以创建元组
print(type(t2))
print(t2)
t3=('python',)
print(t3)
print(type(t3))
lst=[]
lst1=list()
d={}
d2=dict()
t4=()
t5=tuple()
print('空列表',lst,lst1)
print('空字典',d,d2)
print('空元组',t4,t5)
s='python'
s=s+'world'    #python world
```

#### 为什么要将元组设计成不可变序列

1.在多任务环境下，同时操作对象时不需要加锁——可查看，但是不可以使用增删改操作，不会对内容产生改变

2.因此，在程序中尽量使用不可变序列



一旦创建不可变类型的对象，对象内部的所有数据就不能再被修改了，这样就避免了由于修改数据而导致的一个错误

注意事项：元组中存储的是对象的引用

1.如果元组中对象本身存储的是不可变对象，则不能再引用其他对象（增添元素）

2.如果元组中的对象是可变对象，则可变对象的引用不允许改变，但数据可以增删改

元组不允许修改元素

```python
t=(10,[20,30],9)  #[20,30]是可变的，其他两个元素不可变
#不可以将t[1]=100因为中间元素存的不是数值，而是引用（指向），可以向列表中添加元素
t=(10,[20,30],9)
print(t)
print(type(t))
print(t[0],type(t[0]),id(t[0]))
print(t[1],type(t[1]),id(t[1]))
print(t[2],type(t[2]),id(t[2]))
t[1].append(100) #由于[20,30]列表，而列表是可变序列，所以可以向列中添加元素，而列表的内存地址不变
print(t,id(t[1]))   #列表地址不变
```



### 元组的遍历

用索引，如t[1]、t[2]——要知道索引的范围

元组是可迭代对象，所以可以用for... in...进行遍历

t=tuple(('python','hello',90))

for item in t:

   print(item)

```python
t=('python','hello',90)
print(t[0])
print(t[1])
print(t[2])
for item in t:
    print(item)
```

### 集合（set）

定义：

1.python语言提供的内置数据结构

2.与列表、字典一样都属于可变类型的序列

3.集合是没有value的字典，**只有**键，也运用hash函数计算

#### 集合的创建方式

s={'python','hello',98}——使用花括号，类似于列表

使用内置函数set()

注意事项：集合当中的元素不允许重复

​                   集合是无序的，如：最后一个放的元素，可能在输出时是第一个输出的

```python
s={2,2,3,4,5,6,7,7}
print(s)
s1=set(range(6)) #range(6)产生一个0——5的整数，将其变成集合
print(s1,type(s1))
print(set([3,4,4,5,6])) #将列表当中的元素转成集合中的元素同时去掉了重复元素
s2=set((3,4,5,5,6,7))
print(s2) #将原组类型的元素转成集合类型
s3=set('python')
print(s3,type(s3)) #{'o', 'p', 'n', 't', 'h', 'y'} <class 'set'>
s4=set({12,323,2123,12,12,123,12121323})
print(s4,type(s4))
s6={}  #空集合？空字典？
print(type(s6))   #字典类型
s7=set()  #定义一个空集合
print(type(s7))
```

#### 集合的相关操作

集合元素的判断操作： in或not in 

集合元素的新增操作： 1. add()，一次添加一个元素

​                                        2.update()至少添加一个元素

集合元素的删除：1.remove(),一次删除一个指定元素，如果指定元素不存在则会抛出异常KeyError

​                               2.discard()，一次删除一个指定元素，如果指定元素不存在也不会抛出异常

​                               3.pop()，一次只删除一个任意元素，括号内不能指定参数

​                               4.clear()，清空集合

```python
s={10,20,30,40,50,60,70,80,90,100}
print(10 in s)
print(23123 in s)
s.add(101)
print(s)
s.update({200,400})  #添加多个元素记得用上花括号
print(s)
s.update([123,222]) #可以添加列表
print(s)
s.update((12313,11111111)) #可以添加元组
print(s)
s.remove(100)
print(s)
s.discard(500)
print(s)
s.discard(11111111)
print(s)
s.pop()
print(s)
s.pop()
print(s)
s.clear()
print(s)
```

#### 集合间的关系

| 关系                           | 操作                   |                                    |
| ------------------------------ | ---------------------- | ---------------------------------- |
| 两个集合是否相等               | 可以使用运算符==或！=  |                                    |
| 一个集合是否是另一个集合的子集 | 调用issubset进行判断   | B是A的子集                         |
| 一个集合是否是另一个集合的超集 | 调用issuperset进行判断 | A是B的超集（意思就是说B是A的子集） |
| 两个集合是否没有交集           | 调用isdisjoint进行判断 |                                    |

```python
s={10,20,30,40}
s2={30,40,20,10}
print(s==s2)
print(s!=s2)
s1={10,20,30,40,50,60}
s2={10,20,30,40}
s3={10,20,90}
print(s2.issubset(s1))
print(s3.issubset(s1))
print(s1.issuperset(s2))
print(s1.issuperset(s3))
print(s1.isdisjoint(s2))
print(s2.isdisjoint(s3))
s4={100,200,300}    #有交集False
print(s4.isdisjoint(s1))   #没有交集 True
```

#### 集合的数学操作

差集：A集合减去A与B集合有交集的数据所剩的元素

对称差集：B集合减去A与B集合有交集的数据所剩的元素

操作之后原集合不变

```python
s1={10,20,30,40}
s2={20,30,40,50,60}
print(s1.intersection(s2))  #求交集
print(s1 & s2) #求交集
print(s1.union(s2)) #求并集
print( s1| s2)#求并集
print(s1.difference(s2)) #求差集
print(s1-s2) #求并集
print(s1.symmetric_difference(s2)) #求对称差集
print(s1^ s2) #求对称差集(数字键6)
```

#### 集合生成式

元组无生成式，因为元组不可变序列

将列表生成式改为花括号即可

{ i*i for i in range(1,10)}

```python
lst=[ i*i  for i in range(10)]
print(lst)
s={ i*i for i in range(10)}
print(s)
```

字典当中的键实际上就是set

### 字符串

字符串是基本数据类型，是一个不可变的字符串序列

#### 字符串的驻留机制

仅保存一份相同 且不可变字符串的方法，不同的值被存放再字符串的驻留池中，python的驻留机制对相同的字符串只保留一份拷贝，后续创建相同的字符串时，不会开辟新空间，而是把该字符串的地址赋给新创建的变量

创建字符串可以用单引号、双引号、三引号   a、b、c都指向相同的地址

```python
a='python'
b="python"
c='''python'''
print(a,id(a))
print(b,id(b))
print(c,id(c))
```

驻留机制的几种情况**（交互模式）**

1.字符串的长度为0或1时

2.符合标识符的字符串（标识符：数字、字母、下划线）——如果不全为标识符，内容相同但是分开存储，存储地址不相同

3.字符串只再编译时进行驻留，而非运行时 b='ab'+'c'  c=' '.join(['ab','c'])  b是在运行之前就连接好了的，c通过join方法（运行时）对列表中的数据进行连接

4.[-5，256]之间的整数数字

sys中的intern方法强制2个字符串指向同一个对象，先说明 import sys

pycharm对字符串进行了优化处理，所以原本不驻留的，在pycharm中强制驻留

##### 字符串驻留机制的优缺点

当需要值相同的字符串时，可以直接从字符串池里拿来使用，避免频繁的创建和销毁，提升效率和节约内存，因此拼接字符串和修改字符串时比较影响性能的

在需要进行字符串拼接时建议使用str类型的join方法，而非'+'，因为join()方法时先计算出所有字符中的长度，然后再拷贝，只new一次对象，效率要比'+'高

拼接修改字符串都会产生新的字符串对象

#### 字符串的常用操作

查询：建议使用find()、rfind()因为子串不存在时，不会报错

| 方法名称 | 作用                                                         |
| -------- | ------------------------------------------------------------ |
| index()  | 查找子串substr第一次出现的位置，如果查找的子串不存在时，则会抛出ValueError |
| rindex() | 查找子串substr最后一次出现的位置，如果查找的子串不存在时，则抛出ValueError |
| find()   | 查找子串substr第一次出现的位置，如果查找的子串不存在时，则返回-1 |
| rfind()  | 查找子串substr最后一次出现的位置，如果查找的子串不存在时，则返回-1 |

逆向索引从-1开始

```python
s='hello,hello'
print(s.index('lo')) #字符串也相当于列表
print(s.find('lo'))
print(s.rfind('lo'))
```

字符串的大小写转换操作的方法：

| 方法名称      | 作用                                                         |
| ------------- | ------------------------------------------------------------ |
| X.upper()     | 把字符串中所有的字符都转换成大写字母                         |
| X.lower()     | 把字符串中所有的字符都转换成小写字母                         |
| .swapcase()   | 把字符串中所有的大写字母转换成小写字母，把所有小写字母都转成大写字母 |
| .capitalize() | 把第一个字符转换为大写，把其余字符转换为小写                 |
| .title()      | 把每个单词的第一个字符转换为大写，把每个单词的剩余字母转换为小写 |

```python
s='hello,python'
a=s.upper() #会产生一个新的字符串对象
print(a)
print(s) #原来的不变
print(id(s))
print(s.lower())
print(id(s))
print(id(s.lower()))  #地址不一样，产生了新的字符串对象
print(s.lower()==s) #内容一样，但是地址不相等，没有驻留
s2='hello,Python'
print(s2.swapcase())
print(s2.title())
```

#### 字符串内容对齐操作的方法

| 方法名称   | 作用                                                         |
| ---------- | ------------------------------------------------------------ |
| X.center() | 居中对齐，第一个参数指定宽度，第二个参数指定填充符，第二个参数是可选的，默认是空格，如果可设置宽幅小于实际宽度则返回原字符串 |
| X.ljust()  | 左对齐，第一个参数指定宽度，第二个参数指定天重复，第二个参数是可选的，默认是空格，如果可设置宽幅小于实际宽度则返回原字符串 |
| X.r just() | 右对齐，第一个参数指定宽度，第二个参数指定填充符，第二个参数是可选的，默认是空格，如果可设置宽幅小于实际宽度则返回原字符串 |
| X.zfill()  | 右对齐，左边用0填充，该方法只接受一个参数，用于指定字符串的宽度，如果指定的宽度小于等于字符串的长度，则返回字符串本身 |

```python
s='hello，Python'
print(s.center(20,'*')) #****hello，Python****
print(s.ljust(20,'*'))  #hello，Python********
print(s.ljust(10))#hello，Python
print(s.ljust(20))
print(s.rjust(20,'*'))
print(s.rjust(20))
print(s.rjust(10))
print(s.zfill(20))
print(s.zfill((10)))
print('-8910'.zfill(8))
```

#### 字符串劈分操作的方法

| 方法名称   | 作用                                                         |
| ---------- | ------------------------------------------------------------ |
| split(sep) | 从字符串的左边开始劈分，默认的劈分字符是空字符串，返回的值都是一个列表 |
|            | 以通过参数sep指定劈分字符串是的劈分符  "A,B,C".split(",")结果为['A','B','C'] |
|            | 通过参数maxsplit指定劈分字符串时的最大劈分字数，在经过最大次劈分之后，剩余的子串会单独作为一部分 |
| rsplit()   | 从字符串的右边开始劈分，默认的劈分字符是空格字符串，返回的值都是一个列表 |
|            | 以通过参数sep指定劈分字符串是的劈分符                        |
|            | 通过参数maxsplit指定劈分字符串的最大劈分次数，在经过最大次劈分之后，剩余的子串会单独作为一部份 |

```python
s='hello world python'
print(s.split()) #['hello', 'world', 'python']
s1='hello|world|python'
print(s1.split()) #['hello|world|python']在这个地方没有空格，因此分割之后还是一个字符串
print(s1.split(sep='|')) #用字符串进行分割
print(s1.split(sep='|',maxsplit=1)) #maxsplit从左侧进行分割，分割次数为1,如果像分成上一个print则分成三段，hello一段,world一段，python一段
s='hello world python'
print(s.rsplit())
print(s1.rsplit('|'))
print(s1.rsplit(sep='|',maxsplit=1)) #['hello|world', 'python']
```

#### 判断字符串操作的方法

| 方法           |                                                              |
| -------------- | ------------------------------------------------------------ |
| isidentifier() | 判断指定的字符串是不是合法的标识符                           |
| isspace()      | 判断指定的字符串是否全部由空白组字符组成（回车、换行、水平制表符） |
| isalpha()      | 判断指定的字符串是否全部由字母组成                           |
| isdecimal()    | 判断指定的字符串是否全部由十进制的数字组成                   |
| isnumerical()  | 判断指定的字符串是否全部由数字组成、                         |
| isalnum()      | 判断指定字符串是否全部由数字和字母组成                       |

```python
s='hello,python'
print(s.isidentifier()) #合法的标识符是数字字母下划线，而其中有逗号
print('hello'.isidentifier())
print('张三_'.isidentifier()) #True

print('\t'.isspace()) #True
print('abc'.isalpha()) #True
print('张三'.isalpha())#True 中文也属于字母
print('张三1'.isalpha()) #False
print('123'.isdecimal()) #True
print('123'.isnumeric()) #True
print('123四'.isnumeric()) #True
print(''.isnumeric()) #认为罗马数字也是数字
print('abc1'.isalnum()) #True
print('abc!'.isalnum())
```

#### 替换与合并

| 功能         | 方法名称  | 作用                                                         |
| ------------ | --------- | ------------------------------------------------------------ |
| 字符串替换   | replace() | 第一个参数指定被替换的字符，第二个参数指定替换子串的字符串，该方法返回替换后得到的字符串，**替换前的字符串不发生变化**，调用该方法时可以通过第三个参数指定最大替换次数 |
| 字符串的合并 | join()    | 将**列表或元组**中的字符串合并成一个**字符串**               |

```python
s='hello,python'
print(s.replace('python','java')) #hello,java
s1='hello,python,python,python'
print(s1.replace('python','java',2)) #hello,java,java,python

lst=['hello','java','python']
print('|'.join(lst)) #hello|java|python
print(''.join(lst)) #空 hellojavapython字符串类型(文本)

t=('hello','java','python')
print(''.join(t)) #hellojavapython
print('*'.join('python')) #p*y*t*h*o*n把python当成一个字符串序列
```

#### 字符串的比较

|      |      |      |      |      |      |
| ---- | ---- | ---- | ---- | ---- | ---- |
| >    | >=   | <=   | <    | ==   | !=   |

比较规则：首先比较两个字符串中的第一个字符，如果相等则继续比较下一个字符，依次比较下去，直到两个字符串中的字符不相等时，其比较结果就是两个字符串的比较结果，两个字符串中的所有后续字符将不再被比较

 比较原理：两上字符进行比较时，比较的是其ordinal value（原始值），调用内置函数ord可以得到指定字符的ordinal value。与内置函数ord对应的是内置函数chr，调用内置函数chr时指定ordinal value可以得到其对应的字符

```python
print('appele'>'app') #True
print('aplle'>'banana') #False 97小于98
print(ord('a'),ord('b')) #97 98
print(chr(97),chr(98)) #unicode前128项就是ASCII码
print(ord('杨')) #26472
a=b='python'
c='python'
print(a==b) #==# 比较的是value的值是否相等，is比较的是Id是否相等
print(b==c)
print(a is b) #True 说明ABC指向同一个内存空间
print(a is c) #True
print(id(a),id(b),id(c))  #id一样，字符串常量会被驻留，而不会产生新的字符串常量
```

####  字符串的切片操作

字符串时不可变类型，不具备增删改等操作，切片操作将产生新的对象

```python
s='hello,python'
s1=s[:5]  #指定结束位置，则默认切0-4
print(s1)
s2=s[6:] #指定起始位置，不指定结束位置 默认结束位置是最后一个
s3='!'
newstr=s1+s3+s2
print(s2) #python 说明原来的字符串没有发生改变
print(newstr) #hello!python
print('完整写法：[start:stop:step]')#与列表类似
print(s[1:5:1]) #索引结束位置是4
print(s[::2]) #0 2 4 6 8 10从零开始到最后一个元素
print(s[::-1]) #倒置，默认从字符串的最后一个元素开始，第一个字符串为结束位置，因为步长为-1
print(s[-6::-1]) #从-6开始，到第一个元素
```

#### 格式化字符串

字符串的拼接操作会产生新的字符串，造成内存空间的浪费，采用格式化字符串，就是按一定格式输出的一个字符串

格式化字符串的两种方式

一、%作占位符 %s——字符串    %i或%d——整数     %f——浮点数

例如：    ’我的名字叫：%s，今年%d岁了‘ %  (name,age)

二、{}作占位符

’我的名字叫：{0}，今年{1}岁了，我真的叫{0}‘**.**format(name,age) 标{0}会用format的第一个元素去替换

```python
name='张三'
age=20
print('我叫%s，今年%d岁' % (name,age)) #我叫张三，今年20岁
print('我叫{0},今年{1}岁'.format(name,age))
print(f'我叫{name},今年{age}岁') #前面写一个f表示f-string格式化字符串
print('%d' % 99) #记得加上单引号
print('%10d' % 99) #表示宽度        99
print('hellohello')
print('%f' % 3.1415926) #保留小数点后6个数字
print('%.3f' % 3.1415926) #只保留三位小数 .3表示小数点后三位
print('%10.3f' % 3.1415926) #宽度和精度
print('{0}'.format(3.1415926)) #全部输出
print('{0:.3}'.format(3.1415926)) #.3表示一共三位数 3.14
print('{0:.3f}'.format(3.1415926)) #.3f表示三位小数
print('{0:.4}'.format(3.1415926)) #0表示占位符的顺序，也可以省略不写
print('{:.4}'.format(3.1415026))
print('{:10.3f}'.format(3.1415926)) #同时控制宽度和精度
```

#### 字符串的编码转换

为什么需要字符串的编码转换：

字符串在网络当中进行传输，如A计算机中的字符串传送到B计算机中，则需要字节传输，此时需要将字符串str转成二进制数据传送到B计算机，B计算机再将二进制数据转换成字符串开始进行显示

##### 编码与解码的方式

byte代表一个二进制数据（字节类型的数据）

编码：将字符串转换为二进制数据（bytes）——用encode()

解码：将bytes类型的数据转换成字符串类型——用byte.decode()

```PYTHON
s='天涯共此时' #接下来进行编码操作
print(s.encode(encoding='GBK')) #GBK简体中文，一个中文占两个字节 b'\xcc\xec\xd1\xc4\xb9\xb2\xb4\xcb\xca\xb1'    b表示byte类型
print(s.encode(encoding='UTF-8')) #在UTF-8这种编辑格式中，一个中文占三个字节   总之，不同编码格式占用不同的字节数，这个编码会比上面那个多出5个字节
byte=s.encode(encoding='GBK') #编码
print(byte.decode(encoding='GBK')) #解码
# print(byte.decode(encoding='UTF-8')) 报错——编码格式和解码格式要相同，用GBK编码就用GBK解码
byte=s.encode(encoding='UTF-8')
print(byte.decode(encoding='utf-8'))
```

### 函数

#### 函数的定义与调用

函数的定义：执行特点任务和完成特定功能的代码

为什么需要函数：复用代码  隐藏实现细节  提高可维护性 提高可读性便于调试

函数的创建：函数名的命名要符合标识符的命名规范

标识符的命名规则： 大小写字母、数字、下划线和汉字等字符及组合 这门python是门好课

注意事项：大小写敏感、首字符不能是数字、不与保留字相同

保留字：被编程语言内部定义并保留使用的标识符——if   elif  

def 函数名(形式参数):

​       函数体

​       [return XXX]

函数的调用：result变量

result=函数名(实参)

print（result）

```
def calc(a,b):
    c=a+b
    return c
result=calc(10,20)
print(result)
```

#### 函数的参数传递

1.位置实参——根据形参对应的位置进行实参传递

calc(10,20)

def calc(a,b):

2.关键字实参——根据形参名称进行实参传递

在函数调用过程中，进行参数的传递，如果是不可变对象，在函数体的修改不会影响实参的值；如果是可变对象，在函数体内的修改会影响到实参的值

N1在函数体内修改不会影响实参的值，因为在函数体内指向改变了，而n1不变

```python
def calc(a,b):
res=calc(b=10,a=20) #等号左侧的名称称为关键字参数，按照关键字的名字去到定义处名字相同的去复制
```

```python
def fun(arg1,arg2):
    print('arg1',arg1)
    print('arg2',arg2)
    arg1=100
    arg2.append(10)
    print('arg1',arg1)
    print('arg2',arg2)

n1=11
n2=[22,33,44]
print(n1)
print(n2)
fun(n1,n2) #位置传参，形参虽然只是单个变量，但是可以传入列表
print(n1)
print(n2) '''11
[22, 33, 44]
arg1 11
arg2 [22, 33, 44]
arg1 100
arg2 [22, 33, 44, 10]
11
[22, 33, 44, 10]'''
```

#### 函数的返回值

函数返回多个值时，结果为元组

1.如果函数没有返回值——函数执行完毕后，不需要给调用处提供数据，return可以省略不写

2.函数的返回值，如果是1个，直接返回原值，返回原类型，是列表则返回列表（看作一个整体），是整数则返回整数

3.函数的返回值，如果是多个，返回的结果为元组

```python
print(bool(0))
print(bool(8))
def fun(num):
    odd=[] #存奇数
    even=[] #存奇数
    for i in num:
        if i%2:
            odd.append(i)
        else:
            even.append(i)
    return odd,even
lst=[10,29,34,23,44,53,55]
print(fun(lst))  #形参可以是变量，实参可以是列表
```

```python
def fun1():
    print('hello') #return可以不写
fun1()


def fun2():
    return 'hello'
res=fun2() #要对返回值进行存储
print(res)

def fun3():
    return 'hello','world'
print(fun3())
```

#### 函数的参数定义

函数定义默认值参数：函数定义时，给形参设置默认值，只有与默认值不符的时候才需要传递实参

```python
def fun(a,b=10): #b是在函数的定义处，所以b是形参，而且进行了赋值，所以b成为默认值形参
    print(a,b)

fun(100)#只传一个参数
fun(20,30)#a=20,b=30
```

##### “个数可变”的位置参数（在形参位置只可以定义一个）

定义参数时，可能无法事先确定传递的位置实参的个数时，使用可变的位置参数

使用*定义个数可变的位置形参

结果为一个元组

```python
def fun(*args): #函数定义时，可变的位置参数
    print(args)
    print(args[0])

fun(10)
fun(10,20)
fun(30,405,50)
```

##### “个数可变”的关键字形参（在形参位置只可以定义一个）

定义函数时，无法事先确定传递的关键字实参的个数时，使用可变的关键字形参

使用**定义个数可变的关键字形参

结果为一个字典

```python
def fun1(**args):
    print(args)

fun1(a=10)
fun1(a=20,b=30,c=50)'''{'a': 10}
{'a': 20, 'b': 30, 'c': 50}'''
```

注意事项：在一个函数的定义过程中，既有个数可变的关键字形参，也有个数可变的位置形参，要求个数可变的给位置形参放在个数可变的关键字形参之前

```python
def fun1(**args):
    print(args)

fun1(a=10)
fun1(a=20,b=30,c=50)
print()
def fun3(*args,**ages):
    pass
```

##### 补充

1.将列表中的每个元素都转换为位置实参——在函数调用的时候使用*

2.将字典中的每个键值对都转换为关键字实参——在函数调用的时候使用**

```python
def fun(a,b,c):
    print(a,b,c)

fun(10,20,30) #位置传参
lst=[11,22,33]
fun(*lst) #函数调用时，列表中的每个元素都转换为我们的位置实参传入
fun(a=100,c=300,b=200) #关键字传参
dic={'a':111,'b':222,'c':333}
fun(**dic)
```

```
def fun(a,b,c,d):
    print(a,b,c,d)
fun(10,20,30,40)
fun(a=10,b=20,c=30,d=40)
fun(10,20,c=30,d=40)
def fun2(a,b,*,c,d,**args): #在*之后只可以用关键字传递——关键字形参使用*
    print(a,b,c,d)
fun2(10,20,c=30,d=40)
def fun3(a,b,c,d,*args,**args2): #这里要把*去掉
    pass
```

### 变量的作用域

变量的作用域：程序代码能访问该变量的区域

局部变量：在函数内定义并使用的变量，只在函数内部有效，局部变量使用global声明，这个变量就会成为全局变量

全局变量：函数体外定义的变量，可作用于函数内外

```python
name='张三'
def fun():
    print(name)
fun()
def fun3():
    global age
    age=20
    print(age)
fun3()
print(age)
```

#### 递归函数

如果在一个函数的函数体内调用了该函数本身，这个函数就成为递归函数

递归的组成部分：**递归调用与递归终止条件** ——if...else

递归调用过程：

   每递归调用一次函数，都会在栈内存分配一个栈帧

   每执行完一次函数，都会释放相应的空间

递归的优缺点：
   缺点：占用内存多，效率低下

   优点：思路和代码简单

```
def fun(n):
    if n==1:
        return 1
    else:
        res=n*fun(n-1) #先调用函数，再返回
        return res
print(fun(6))
```

```python
def fid(n): #求斐波那契数列的某一项，该项为前两项之和
    if n==1:
        return 1
    elif n==2:
        return 1
    else:
        return fid(n-1)+fid(n-2)
res=fid(6)
print(res)
for i in range(1,7): #(1,7)是让这个操作循环六次，并且可以用1去引出斐波那契数列
    print(fid(i))
```

### Bug

注意事项：input输入的所有类型均为str类型

```
age=input('请输入你的年龄')
print(type(age))
if int(age)>=18:
    print('成年人')
```

思路不清晰导致出现Bug解决方案：
1.使用print()函数

2.使用’#‘暂时注释部分代码

#### 被动掉坑问题的解决方案——使用异常处理机制，可以在异常出现时及时捕获，然后内部“消化”，让程序继续运行

##### try...except多个except结构（由小到大）顺序查找对应的错误类型：

```python
try:
    n1=int(input('请输入一个整数'))
    n2=int(input('请输入第二个整数'))
    result=n1/n2
    print('输出结果为',result)
except ZeroDivisionError:
    print('除数不能为零')
print('程序结束')

'''多个except结构   Exception指的是错误的类型，如ValueError
try:
     可能会出现异常的代码
except Exception1:
     异常处理的代码
except Exception2:
     异常处理的代码
except Exception3:
     异常处理的代码
except BaseException: #直接写Baseexception，不用写错误类型，可以取别名   BaseException as e:
     异常处理的代码'''
```

#### try...except...else结构

如果try块中没有抛出异常，则执行else块，如果try中抛出异常，则执行except块

#### try...exccept...else...finally结构

finally块无论是否发生异常都会被执行，能常用来释放try块中申请的资源

出错就执行except、finally

不出错就执行try、else、finally

```python
try:
    a=int(input('请输入第一个整数'))
    b=int(input('请输入第二个整数'))
    result=a/b
except BaseException as e: #给Baseexception起个别名 e
    print('出错了',e) #出错了 invalid literal for int() with base 10: 'a'后面这串是e所带有的东西
else:
    result=a/b
    print('计算结果为：',result)
finally:
    print('谢谢您的使用')
```

#### 常见的异常类型

| 类型              | 描述                           |
| ----------------- | ------------------------------ |
| ZeroDivisionError | 除（或取模）零（所有数据类型） |
| IndexError        | 序列中没有此索引               |
| KeyError          | 映射中没有这个键               |
| NameError         | 为声明、初始化对象             |
| SyntaxError       | 语法错误                       |
| ValueError        | 传入无效的参数                 |

```python
'''print(10/0) #ZeroDivisionError'''
lst=[11,22,33,44]
'''print(lst[4]) #IndexError'''
dict={'name':'张三','age':20}
'''print(dict['gernder']) #KeyError'''
'''print(a) #NameError 没有定义'''
'''int a=20 # SyntaxError python变量没有数据类型'''
'''a=int('hello') #字符串不能变成十进制整数 ValueError'''
```

#### traceback模块打印异常信息

```python
import traceback
try:
    print(10/0)
except: #可以不写错误类型，直接加上冒号
    traceback.print_exc()
```

### 编程思想

|        | 面向过程                                                     | 面向对象                                 |
| ------ | ------------------------------------------------------------ | ---------------------------------------- |
| 区别   | 事务比较简单，可以用线性的思维去解决（一个个具体的步骤组成） | 事物比较复杂，使用简单的线性思维无法解决 |
| 共同点 | 面向过程和面向对象都是解决实际问题的一种思维方式             |                                          |
|        | 二者相辅相成，并不是对立的。解决整个复杂问题，通过面向对象方式便于我们从宏观上把握事物之间复杂的关系，方便我们分析整个系统；具体到微观操作，仍然使用面向过程方式来处理 |                                          |

#### 类和对象

类：多个类似事物组成的群体的统称，能够帮我们快速理解和判断事物的性质

数据类型：不同的数据类型属于不同的类，使用内置函数type()查看数据类型

对象：100、99、520都是int类之下包含的相似的不同个例，这个个例专业术语称为实例或对象

python一切皆对象，字典对象 元组对象 列表对象

#### 类（类对象）

对象由三部分组成：类型 ID 值

类对象的组成：类属性、实例方法、静态方法、类方法

直接写在类里面的变量

静态方法用@staticmethod修饰

#### 对象的创建

对象的创建又称类的实例化

语法：  实例名=类名（）

```
class Student: #Student为类的名称，由一个或多个单词组成，每个单词的首字母大写,其余小写（行业规则）
    pass
print(id(Student))
print(type(Student)) #类 类型
print(Student) #<class '__main__.Student'>这段代码就是它的value值
```

类对象：**Student**(native_place  def info(self)  def cm(cls)  def sm())

实例对象：name age info() ——通过类指针指向类对象，由此知实例对象属于该类

实例方法调用的两种方式：对象名.方法名    类名.方法名（类的对象名）  ——类的对象实际上就是方法定义处的self  

初始化方法用的是左右两边各两个'下划线'

```python
class Student: #类对象！=类的对象
    native_pace='吉林' #直接写在类内的变量 称为类属性，必须写
    def __init__(self,name,age): #初始化方法 ，在self（必须写）后面可以继续写别的——赋值操作（后面添加的属于局部变量）
        self.name=name #name的值赋给self.name——实例属性
        self.age=age #习惯上左右两边名称相同
    def eat(self): #实例方法——self要写，否则写点别的，在类之外定义的称为函数，在类内定义的称为方法，self是自身，要求传入student的对象
        print('学生在吃饭')
    @staticmethod
    def method(): #不允许写self
        print('我使用了staticmethod进行修饰，所以我是静态方法')
    @classmethod
    def cm(cls):
        print('我是类方法，因为我使用了classmethod进行修饰')

stu=Student('Jack',20) #因为init有两个参数，创建实例对象创建，实例对象=类的对象
print(type(stu))
print(id(stu))
print(stu) #实际上输出的是该对象十六进制的地址
stu.eat() #使用类方法 等价于 Student.eat(stu),都是调用eat方法
print(stu.name) #输出实例属性
print(stu.age) #调用时用.即可
```

#### 类属性、类方法、静态方法

类属性：类中方法外的变量称为类属性，被该类的所有对象所共享

类方法：使用@classmethod修饰的方法，使用类名直接访问的方法  （）中传输的是class——默认参数，cls表示不需要传输

静态方法：使用@staticmethod修饰的方法，使用类名直接访问的方法

print(Student.native_place) #访问类属性

Student.cm() #调用类方法——因为没有传入参数，所以用类名调用

Student.sm() #调用静态方法

```
class Student: #类对象！=类的对象
    native_pace='吉林' #直接写在类内的变量 称为类属性，必须写
    def __init__(self,name,age): #初始化方法 ，在self（必须写）后面可以继续写别的——赋值操作（后面添加的属于局部变量）
        self.name=name #name的值赋给self.name——实例属性
        self.age=age #习惯上左右两边名称相同
    def eat(self): #实例方法——self要写，否则写点别的，在类之外定义的称为函数，在类内定义的称为方法，self是自身，要求传入student的对象
        print('学生在吃饭')
    @staticmethod
    def method(): #不允许写self
        print('我使用了staticmethod进行修饰，所以我是静态方法')
    @classmethod
    def cm(cls):
        print('我是类方法，因为我使用了classmethod进行修饰')

stu=Student('Jack',20) #因为init有两个参数，创建实例对象=类的对象
stu1=Student('张三',30)
print(stu.native_pace)
print(stu1.native_pace)
Student.native_pace='天津'
print(stu.native_pace)
print(stu1.native_pace)
stu1.native_pace='大东北'
print(stu1.native_pace)
print(stu.native_pace)
Student.cm() #调用类方法
Student.method() #调用静态方法
```

#### 动态绑定属性和方法

python是动态语言，在创建对象之后，可以动态地绑定属性和方法

```python
class Student:
    def __init__(self,name,age): #初始化时传入的name、age是实例对象所共有的属性
        self.name=name
        self.age=age
    def eat(self):
        print(self.name+'在吃饭')
stu1=Student('张三',20)
stu2=Student('李四',30)
print('为stu2动态绑定性别属性')
stu2.gender='女' #性别属性只适用于当前绑定的这个对象
print(stu1.name,stu1.age)
print(stu2.name,stu2.age,stu2.gender)
stu1.eat()
stu2.eat()
def show():
    print('定义在类之外的称为函数') #将这个函数去绑定在stu1这个对象上，绑定之后则变成方法
stu1.show=show
stu1.show()
```

### 面向对象的三大特征（与语言无关）

封装：提高程序的安全性

   将数据（属性）和行为（方法）包装到类对象中。在方法内部对属性进行操作，在类对象的外部调用方法。这样，无需关心方法内部的具体实现细节，从而隔离了复杂度

   在python中没有专门的修饰符用于属性的私有，如果该属性不希望在类对象外部被访问，前边使用两个“_"。

继承：提高代码的复用性

多态：提高程序的可拓展性和可维护性

```python
class Car: ##点击旁边的加号包起来
    def __init__(self,brand): #实例属性
        self.brand=brand
    def start(self):
        print('汽车已启动')
car=Car('宝马X5') 
car.start()
print(car.brand
```

```python
class Student:
    def __init__(self,name,age):
        self.name=name
        self.__age=age  #年龄不希望被类的外部被使用，所以加了两个__，但是不希望被使用不是不可以使用
    def show(self):
        print(self.name,self.__age)
stu=Student('张三',20)
stu.show() #可以输出 name和age
print(stu.name)
'''print(stu.__age) #程序报错'''
print(dir(stu)) #查找与age有关的信息 '_Student__age'
print(stu._Student__age)  #通过该种方式访问
```

#### 继承

如果一个类没有继承任何类，则 默认继承object

python支持多继承 定义子类时，必须在其构造函数中调用父类的构造函数

class 子类类名（父类1，父类2，）

   pass

```python
class Person(object): #也可以不写object
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def info(self):
        print(self.name,self.age)
class Student(Person):
    def __init__(self,name,age,stu_no):
        super().__init__(name,age)  #用super调用父类的__init__,再传入name,age
        self.stu_no=stu_no #子类独有的
class Teacher(Person):
    def __init__(self,name,age,teachofyear):
        super().__init__(name,age)
        self.teachofyear=teachofyear
stu=Student('张三',20,'1001') #创建Person类的对象
teacher=Teacher('李四',34,10) #创建Teacher类的对象
stu.info() #调用info()，从Person类继承过来的
teacher.info()
```

```python
class A(obeject):
    pass
class B(object):
    pass
class C(A,B):
    pass
```

#### 方法重写

如果子类对继承自父类的某个属性或方法不满意，可以在子类中对其（方法体）进行重新编写

子类重写后的方法中可以通过super().XXX()调用父类中被重写的方法

```python
class Person(object): #也可以不写object
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def info(self):
        print(self.name,self.age)
class Student(Person):
    def __init__(self,name,age,stu_no):
        super().__init__(name,age)  #用super调用父类的__init__,再传入name,age
        self.stu_no=stu_no #子类独有的
    def info(self): #左边的圆圈意味着重写
        super().info()
        print(self.stu_no) #只输出学号，因此还要再调用父类的输出姓名、年龄
class Teacher(Person):
    def __init__(self,name,age,teachofyear):
        super().__init__(name,age)
        self.teachofyear=teachofyear
    def info(self):
        super().info()
        print(self.teachofyear)
stu=Student('张三',20,'1001') #创建Person类的对象
teacher=Teacher('李四',34,10) #创建Teacher类的对象
stu.info() #调用info()，从Person类继承过来的
teacher.info()
```

#### object类

object类时所有类的父类，因此所有类都有object类的属性和方法

内置函数dir()可以查看指定对象所有属性

Object有一个_  str_方法，用于返回一个对于”对象的描述”，对应与内置函数str()经常用于print()方法，帮我们查看对象的信息，所以我们经常会对 _ str  _ ()  进行重写

```python
class Student():
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def __str__(self): #重写父类的方法
        return '我的名字是{0}，今年{1}岁了'.format(self.name,self.age)

stu=Student('张三',20)
print(dir(stu)) #可以查询到许多属性和方法，但是都是从object类继承过来的
print(stu)  #默认调用__str__(),返回字符串的内容
print(type(stu)) #Student类型
```

#### 多态

简单地说，多态就是具有多种形态，它指的是：即便不知道一个变量所引用的对象到底是什么类型，仍然可以通过这个变量调用方法，在运行过程中根据变量所引用对象的类型，动态决定调用哪个对象中的方法

python的变量没有数据类型

#### 静态语言和动态语言关于多态的区别

静态语言（Java）实现多态的三个必要条件：继承、方法重写、父类引用指向子类对象

动态语言的多态崇尚“鸭子类型”当看到一只鸟走路起来像鸭子、游泳起来像鸭子、收起来也像鸭子，那么这只鸟就可以被称为鸭子。再鸭子类型中，不需要关心对象是什么类型，到底是不是鸭子，只关心对象的行为

```python
class Animal(object):
    def eat(self):
        print('动物会吃')
class Dog(Animal):
    def eat(self): #重写父类的方法，则之后调用会使用自己的内容
        print('狗吃骨头')
class Cat(Animal): ##重写父类的方法，则之后调用会使用自己的内容
    def eat(self):
        print('猫吃鱼')
class Person:
    def eat(self):
        print('人吃五谷杂粮')
def fun(obj): #定义一个函数，obj形参
    obj.eat()
fun(Cat()) #传入一个Cat类型的对象
fun(Dog()) #传入一个Dog类型的对象
fun(Animal()) #传入一个Animal类型的对象
fun(Person()) #fun也会调用eat方法
```

#### 特殊属性和特殊方法

|          | 名称        | 描述                                                         |
| -------- | ----------- | ------------------------------------------------------------ |
| 特殊属性 | __ dict__   | 获得类对象或实例对象所绑定的所有属性和方法的字典             |
| 特殊方法 | __ len __() | 通过重写__ len __()方法，让内置函数len()的参数可以是自定义类型 |
|          | __ add__()  | 通过重写__ add__()方法，可是自定义对象具有“+” 功能           |
|          | __  new__() | 用于创建对象                                                 |
|          | __ init__() | 对创建的对象进行初始化                                       |

dir()查看对象具有哪些属性和方法

```python
class A:
    pass
class B:
    pass
class C(A,B):
    def __init__(self,name,age):
        self.name=name
        self.age=age
x=C('Jack',20)  #X是C类型的一个实例对象
class D(A):
    pass
print(x.__dict__) #获得实例对象所绑定的所有属性的字典，实例对象只负责调用
print(C.__dict__) #获得类对象所绑定的所有属性和方法的字典，方法仅存在类当中
print(x.__class__) #输出对象所属的类 <class '__main__.C'>
print(C.__bases__) #输出C类的父类元组 (<class '__main__.A'>, <class '__main__.B'>)

print(C.__base__) #输出最近的父类，看C类定义时那个父类看前面就输出哪个
print(C.__mro__)  #查看类的层次结构 (<class '__main__.C'>, <class '__main__.A'>, <class '__main__.B'>, <class 'object'>)  C继承了A、B、 object
print(A.__subclasses__()) #查看A的子类 以列表的形式呈现
```

```python
a=20
b=100
c=a+b #两个整数类型的对象相加操作
'''实际上是调用了d=a.__add__(b)进行运算'''
print(c)
d=a.__add__(b)
print(d)
class Student:
    def __init__(self,name):
        self.name=name
stu1=Student('张三')
stu2=Student('李四')
'''s=stu1+stu2
print(s)'''  #报错，两个类不可以相加，如果要执意相加
class Student:
    def __init__(self,name):
        self.name=name
    def __add__(self, other):
        return self.name+other.name

stu1 = Student('张三')
stu2 = Student('李四')
s=stu1+stu2
print(s)
s=stu1.__add__(stu2)
print(s)
print('-------------------------------------')
lst=[11,22,33,44]
print(len(lst))  # lst是内置函数，计算列表长度
print(lst.__len__())
class Student:
    def __init__(self,name):
        self.name=name
    def __add__(self, other):
        return self.name+other.name
    def __len__(self):
        return len(self.name)
stu1=Student('张三')
print(len(stu1)) #必须在类内添加__len__(self)
stu2=Student('Jack')
print(len(stu2))
```

```python
class Person(object):
    def __init__(self,name,age):   #初始化完成后把self传给p1
        print('__init__方法被调用了，self的id值为{0}',format(id(self))) #320
        self.name=name
        self.age=age
    def __new__(cls,*args,**kwargs):
        print('__new__被调用执行了，cls的id值为{0}',format(id(cls))) #448
        obj=super().__new__(cls)
        print('创建对象的id为{0}',format(id(obj))) #320
        return obj#return返回给self
print('object这个类的id为：{0}'.format(id(object)))  #768
print('Person这个类对象的Id为：{0}'.format(id(Person))) #448
p1=Person('张三',20) #创建对象执行Person
print('p1这个Person类的实例对象的id:{0}'.format(id(p1))) #320 因为定义p1的时候Person传到cls
```

### 类的浅拷贝与深拷贝

#### 变量的赋值操作

只是形成两个变量，实际上还是指向同一个对象

```type
class CPU():
    pass
class Disk():
    pass
class Computer():
    def __init__(self,cpu,disk):
        self.cpu=cpu
        self.disk=disk
cpu1=CPU() #创建实例对象，将该对象赋给cpu1 即让cpu1指向该实例对象
cpu2=cpu1 #让cpu2也指向实例对象
print(cpu1) # 输出type id 值   id的值是十进制的
print(cpu2)
```

#### 浅拷贝

python拷贝一般都是浅拷贝，拷贝时，对象包含的子对象内容不拷贝，因此，元对象与拷贝对象会引用同一个子对象

```python
class CPU():
    pass
class Disk():
    pass
class Computer():
    def __init__(self,cpu,disk):
        self.cpu=cpu
        self.disk=disk
cpu1=CPU() #创建实例对象，将该对象赋给cpu1 即让cpu1指向该实例对象
cpu2=cpu1 #让cpu2也指向实例对象
print(cpu1) # 输出type id 值
print(cpu2)
print('类的浅拷贝')
disk=Disk() #创建一个硬盘类的对象
computer=Computer(cpu1,disk)
import copy #导入浅拷贝
computer2=copy.copy(computer) #拷贝之前，computer的值包含cpu和disk，分别指向原来的实例对象cpu、computer；拷贝之后仍然指向原来的实例对象，computer1变成原对象，拷贝（id改变），子对象cpu,disk不拷贝
print(disk)
print(computer,computer.cpu,computer.disk)
print(computer2,computer2.cpu,computer2.disk)
```

#### 深拷贝

使用copy模块的deepcopy函数，递归拷贝对象中包含的子对象，元对象和拷贝对象所有的子对象也不相同

```python
class CPU():
    pass
class Disk():
    pass
class Computer():
    def __init__(self,cpu,disk):
        self.cpu=cpu
        self.disk=disk
cpu1=CPU() #创建实例对象，将该对象赋给cpu1 即让cpu1指向该实例对象
cpu2=cpu1 #让cpu2也指向实例对象
print(cpu1) # 输出type id 值
print(cpu2)
print('类的浅拷贝')
disk=Disk() #创建一个硬盘类的对象
computer=Computer(cpu1,disk)
import copy #导入浅拷贝
computer2=copy.copy(computer) #拷贝之前，computer的值包含cpu和disk，分别指向原来的实例对象cpu、computer；拷贝之后仍然指向原来的实例对象，computer1变成原对象，拷贝（id改变），子对象cpu,disk不拷贝
print(disk)
print(computer,computer.cpu,computer.disk)
print(computer2,computer2.cpu,computer2.disk)
print('深拷贝')
computer3=copy.deepcopy(computer)
print(computer,computer.cpu,computer.disk)
print(computer3,computer3.cpu,computer3.disk) #沈拷贝之后形成的computer3 computer3.cpu computer3.disk的id都会变，赋值给computer3去指向该对象，该对象包含cpu,disk，又指向深拷贝后的地址
```

### 模块

函数与模块的关系：一个模块可以包含N多个函数，类，语句 类包含类属性类方法 静态方法 实例属性  一个程序由N个模块组成

在python（pycharm）中一个扩展名为.py的文件就是一个模块

使用模块的好处：

   方便其它程序和脚本的导入并使用

   避免函数名和变量名冲突（两个模块有重名变量但是不互相影响）

   提高代码的可维护性

   提高代码的可重用性

#### 自定义模块

创建模块：创建一个.py文件，名称尽量不要与Python自带的标准模块（int、str)名称相同

##### 导入模块

import 模块名称 [as 别名]

from 模块名称import 函数/变量/类

```python
import math
print(id(math))
print(type(id))
print(math)
print(math.pi) #Π的值——使用模块当中的一些方法
print(dir(math))
print(math.pow(2,3),type(math.pow(2,3))) #求2的三次方
print(math.ceil(9.001)) #找出最接近他的最大的整数
print(math.floor(9.99999)) #与上式相反
```

```python
from math import pi #只导入math中的pi
print(pi)
print(pow(2,3)) #不属于math中的Pow
```

```python
import demo3 #会报错，所以要找到本模块所属一级文件，找到Make Directory as，再点击Source Root即可
print(demo3.add(10,20))
print(demo3.div(12,4))
```

导入自定义模块

```python
def add(a,b): '''自定义模块'''
    return a+b
def div(a,b):
    return a/b
```



```python
from demo3 import add
print(add(10,20)
```



### 以主程序形式运行

在每个模块的定义中都包括一个记录模块名称的变量_name_,程序中可以检查该变量，以确定他们在哪个模块中执行。如果一个模块不是被导入到其他程序中执行，那么它可能在解释器的顶级模块中执行。顶级模块的__ name__  变量的值为 __ main__

if __  name__ =__ 'main'__:

```python
def add(a,b): #模块文件
    return a+b

if __name__=='__main__': #不想出现30
    print(add(10,20)) #把print放在该语句当中，意思是 只有点击运行demo3时，才会执行运算
```

```python
import demo3 #会报错，所以要找到本模块所属一级文件，找到Make Directory as，再点击Source Root即可 '''导入模块的文件——主程序'''
print(demo3.add(100,200)) #不想要demo3中的30出现，则返回该模块所在文件写入if __name__=='__main__':
```

### 包

python中的包是一个分层次的目录结构，它将一组功能相近的模块组织在一个目录下，一个python程序有N多个包

作用：代码规范、避免模块名称冲突

包与目录的区别：

   包含__ init__.py文件的目录称为包

   目录里通常不包含__ init__.py文件

包的导入： import 包名.模块名

报的创建：单击右键——new——package

目录的创建：单击右键——new——directory

导入带有包的模块时注意事项：

   使用import方式进行导入时，只能跟包名或模块名

   使用from...import可以导入包、模块，函数，变量等等

```python
a=10 #包下的模块A
```

```python
import package.modelA #导入包：包名.模块名称 '''.py文件'''
print(package.modelA.a) #输出model A中的a

import package.modelA as a #给package.modelA起别名a
print(a.a) #输出a中的a

from package import modelA
from package.modelA import a
```

### python中常用的内置模块

| 模块名   | 描述                                                         |
| -------- | ------------------------------------------------------------ |
| sys      | 与Python解释器及其环境操作相关的标准库                       |
| time     | 提供与时间相关的各种函数标准库                               |
| os       | 提供了访问操作系统服务功能的标准库                           |
| calendar | 提供了与日期相关的各种函数的标准库                           |
| urllib   | 用于读取来自网上（服务器）的数据标准库                       |
| json     | 用于使用JSON序列化和反序列化对象                             |
| re       | 用于在字符串中执行正则表达式匹配和替换                       |
| math     | 提供标准算数运算函数的标准库                                 |
| decimal  | 用于进行精确控制运算精度、有效数位和四舍五入操作的十进制运算——浮点数不精确 |
| logging  | 提供了灵活的记录事件、错误、警告和调试信息的日志             |

```python
import sys
print(sys.getsizeof(24))  #获取对象所占的内存大小
print(sys.getsizeof(45))
print(sys.getsizeof(True))
print(sys.getsizeof(False))
import time
print(time.time()) #秒
print(time.localtime(time.time())) #转换成具体的时间
import urllib.request #urllib是一个包，request是包当中的一个模块
print(urllib.request.urlopen('http://www.baidu.com')) #打开网址，读取百度服务器返回的东西
import math
print(math.pi)
```

### 第三方模块的安装及使用

第三方模块的安装（windows+R——输入CMD（在线安装方式）——输入pip install schedule——在下面那行输入python进入交互式应用程序——在下面那行输入import schedule）

![image-20220124234033157](C:\Users\Huang\AppData\Roaming\Typora\typora-user-images\image-20220124234033157.png)

pip install 模块名

注意事项：如果程序报错，将鼠标悬停在schedule上，点一下schedule旁边的小灯泡安装包

停止运行可以点击旁边红色的小方块

第三方模块的使用

import 模块名

```python
import schedule
import time
def job_():
    print('嘿嘿嘿——————')

schedule.every(3).seconds.do(job_) #每三秒执行一次job
while True:
    schedule.run_pending() #启动
    time.sleep(1) #使用time模块休眠1秒
```

### 编码格式的介绍

UTF-8  GBK

### 文件的读写原理

文件的读写俗称：IO操作 (input & output)

操作原理：python操作文件——打开或新建文件——读、写文件——关闭资源

.py文件经过解释器（os——操作系统资源被调用）——操作——硬盘

队列顺序：读写先进先出

#### 文件的读写操作

内置函数open()创建文件对象

通过IO流将磁盘文件中的内容与程序中的对象中的内容进行同步：程序（对象——映射磁盘上的真实文件）——input——文件（磁盘中）

语法：

file=open(filename [,mode,encoding])

file 被创建的文件对象

Open 创建文件对象的函数

filename 要创建或打开的文件名称

mode 打开模式默认为只读

encoding 默认文本文件中字符的编写格式为gbk

读 r

写 w

```python
file=open('scratch.txt','r') #前提：存在一个scratch.txt文件——可能用python打开会乱码，点击右UTF-8即可
print(file.readlines()) #读取内容——以列表的形式呈现
file.close()
```

### 常用的文件打开模式

文件的类型（按文件中数据的组织形式）

文本文件：存储的是普通”字符"文本，默认为unicode字符集，可以使用记事本程序打开

二进制文件：把数据内容用“字节”进行存储，无法用记事本打开，必须使用专用的软件打开，举例：mp3音频文件，jpg图i片，.doc文档

| 打开模式 | 描述                                                         |
| -------- | ------------------------------------------------------------ |
| r        | 以只读模式打开文件，文件的指针将会放在文件的开头             |
| w        | 以只写模式打开文件，如果文件不存在则创建，如果文件存在，则覆盖原有内容，文件指针在文件开头 |
| a        | 以追加模式打开文件，如果文件不存在则创建，文件指针在文件开头，如果文件存在，则在文件末尾追加内容，文件指针在原文件末尾 |
| b        | 以二进制方式打开文件，不能单独使用，需要与其他模式一起使用，rb或者wb |
| +        | 以读写方式打开文件，不能单独使用，需要与其他模式一起使用，a+ |

```python
file=open('b.txt','w')
file.write('helloworld')
file.close()
file=open('b.txt','w')
file.write('p') #用p替换helloworld
file.close()
file=open('b.txt','a')
file.write('p') #因为由此前面的代码，不能点击一次就增加一个p，所以要另外打开一个源程序作为主程序运行
file.close()
```