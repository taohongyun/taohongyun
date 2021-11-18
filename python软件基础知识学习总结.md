注释 ctrl+/

 打印 print（）

## puthon基础知识

### 变量以及类型

#### 变量

```python
小明=2
小红=3
小黄=4
print(小明+小红)
print(小明+小黄)
```



```phthon
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe "C:/Users/pc/PycharmProjects/pythonProject1/hello world.py"
5
6

Process finished with exit code 0
```



小明、小红、小黄是变量的名字

2、3、4为变量的值

=赋值符号

### 变量类型

##### 基础数据类型

> Number数字
>
> >int整型
> >
> >float浮点型
> >
> >boolue布尔
> >
> >complex复数

string(str)字符串

list列表

tuple 元组

dictionary字典

sets集合



### 输出

```python
age = 10
print("我今年%d岁了" % age)
```



```py
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe "C:/Users/pc/PycharmProjects/pythonProject1/hello world.py"
我今年10岁了

Process finished with exit code 0
```

%：占位符 %d：占位符具体的内容

#### 常用格式符号

| 格式符号   | 转换                      |
| ---------- | ------------------------- |
| %c         | 字符                      |
| %s（常用） | 字符串                    |
| %d（常用） | 有符号十进制整数          |
| %u         | 无符号十进制整数          |
| %o         | 八进制整数                |
| %x         | 十六进制整数（小写字母0x) |
| %X         | 十六进制整数（大写字母0X) |
| %f（常用） | 浮点数                    |
| %e         | 科学计数法（小写'e'）     |
| %E         | 科学计数法（大写“E”）     |
| %g         | %f和%e简写                |
| %G         | %f和%E简写                |



```python
age = 11
name = "小明"
score = 99.12

print("我叫%s，今年%d岁了，考试考了%f" %(name,age,score))
```





```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe "C:/Users/pc/PycharmProjects/pythonProject1/hello world.py"
我叫小明，今年11岁了，考试考了99.120000

Process finished with exit code 0

```



#### 其它占位符号（**{}  format 取代  %**  ）

```python
age = 11
name ="小明"
print("我叫{}，今年{}岁了".format(name,age))
```





#### 换行输出（添加\n换行）

```
name = "小明"
print("我叫{}, \n我今年{}岁了。".format(name,age))
```



C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
我叫小明, 
我今年11岁了。

Process finished with exit code 0



### 输入

1. 接收用户输入的数据使用input（）函数

```
a = input("请输入您的内容")
print(type(a))
print("您输入的内容是{}".format(a))
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
请输入您的内容123
<class 'str'>
您输入的内容是123

Process finished with exit code 0
```





### 运算符 

// 取整除

%取余

**指数

```python
a = 10
b = 20
print(a+b)
print(a-b)
print(a*b)
print(a/b)
print(a//b)
print(a%b)
print(a**b)
```



```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
30
-10
200
0.5
0
10
100000000000000000000

Process finished with exit code 0

```



### 复合赋值运算符

| 运算符 | 描述             | 示例              |
| ------ | ---------------- | ----------------- |
| +=     | 加法赋值运算符   | c+=a  c=c+a       |
| -=     | 减法赋值运算符   | c-=a   c=c-a      |
| *=     | 乘法赋值运算符   | c *=a  c=c *a     |
| /=     | 除法赋值运算符   | c/=a   c=c/a      |
| %=     | 取模赋值运算符   | c%=a c=c%a        |
| **=    | 幂赋值运算符     | c ** =a  c=c ** a |
| //=    | 取整除赋值运算符 | c//=a   c=c//a    |



### 常用的数据类型转换

```
a = input("请输入您的内容")
a = eval(a)
print(type(a))
```

将字符串转换成原始数据

```
a = 123
a = float(a)
print(type(a))
```

将整型转换为浮点型

```
a = 123
a = str(a)
print(type(a))
```

将整型转换为字符串



## python逻辑控制

### 比较运算法

```
a = 10
b = 20
print(a!=b)
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
True

Process finished with exit code 0

```

==  等于  !=  不等于  <  小于  >  大于  <=  小于等于  >=  大于等于



### 逻辑运算符



```
a = 10
b = 20
print(a<b and a!=b)
```

 ```python
 C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
 True
 
 Process finished with exit code 0
 
 ```

a and b  a和b都是正确的吗

a or b    a和b其中一个是正确的吗

not a    a不正确吗



### if判断语句

```
age = 12
if age< 18:
    print("不可以去上网吧")
```



```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
不可以去上网吧

Process finished with exit code 0
 
```

### **两个条件判断(**if else)



```
age = 20
if age< 18:
    print("不可以去上网吧")
else:
    print("可以进入网吧上网。")
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
可以进入网吧上网。

Process finished with exit code 0

```



### 多个条件判断(if elif else)



```
score = 20
if score >90:
    print("学习非常优秀")
elif score >80 and score <=90:
    print("学习优秀")
elif score >70 and score <=80:
    print("学习优良")
elif score >60 and score <=70:
    print("学习及格")
else:
    print("学习不及格")
```



```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
学习不及格

Process finished with exit code 0

```



### if嵌套格式

```
piao = 1
knife = 11
if piao == 1:
    print("可以进入火车站")
    if knife <= 10:
        print("可以通过安检")
    else:
        print("刀具过长无法通过安检")
else:
    print("无票无法进入火车站")
```



```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
可以进入火车站
刀具过长无法通过安检

Process finished with exit code 0

```



### while循环

```
a = 0
while a <10:
    a += 1
    print("哈哈哈")
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
哈哈哈
哈哈哈
哈哈哈
哈哈哈
哈哈哈
哈哈哈
哈哈哈
哈哈哈
哈哈哈
哈哈哈

Process finished with exit code 0
```



###  for循环

```
for a in range(0,10):
    print("哈哈哈和")
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
哈哈哈和
哈哈哈和
哈哈哈和
哈哈哈和
哈哈哈和
哈哈哈和
哈哈哈和
哈哈哈和
哈哈哈和
哈哈哈和

Process finished with exit code 0

```



### break（结束当前的循环）



```
for a in range(1,10):
    print("哈哈哈和")
    if a == 5:
        break
```



```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
哈哈哈和
哈哈哈和
哈哈哈和
哈哈哈和
哈哈哈和

Process finished with exit code 0

```





### continue（结束当次循环）



```
for a in range(1,10):

    if a == 5:
        continue
    print("哈哈哈{}".format(a))
```



```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
哈哈哈1
哈哈哈2
哈哈哈3
哈哈哈4
哈哈哈6
哈哈哈7
哈哈哈8
哈哈哈9

Process finished with exit code 0

```



### 随机数（random）

```
import random
a= random.randint(1,5)
print(a)
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
2

Process finished with exit code 0

```

随机生成1到5中任意整数



### 下标和切片

#### 下标:

通过[]来选择第几位的下**(索引值从0开始)**



```
a = "qwertyuiop"
print(a[1])
print(a[3])
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
w
r

Process finished with exit code 0

```



#### 切片:

[起始:结束:步长]  

步长默认为1 

结束不输入数值就是从起始到最后全部数值

```
a = "qwertyu"
print(a[0:7:3])
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
qru

Process finished with exit code 0
```



### 字符串的常见操作和列表

#### find

在开始和结束之间，寻找某一个字符在什么位置**(索引值从0开始)** 

没有找到的会报-1

```
a = "qwertyu"
print(a.find("w"))
```



```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
1

Process finished with exit code 0

```



#### index

类似于find，但index没有找到会报错

```
a = "qwertyu"
print(a.index("m"))
```



```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
Traceback (most recent call last):
  File "C:\Users\pc\PycharmProjects\pythonProject1\123.py", line 2, in <module>
    print(a.index("m"))
ValueError: substring not found

Process finished with exit code 1

```

#### count

在开始和结束之间，寻找某个字符出现的次数

```
a = "哈哈哈啊啊嘿"
print(a.count("哈"))
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
3

Process finished with exit code 0

```

#### replace

在开始和结束之间，寻找替换某个字符

**("替换前","替换后"，替换的次数)**

```
a = "哈哈哈啊啊嘿"
print(a.replace("啊","哦",1))
```



```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
哈哈哈哦啊嘿

Process finished with exit code 0

```



#### split

在开始和结束之间，分割某段字符串

**"" 为要分割的位置**

```
a = "哈哈哈啊啊嘿"
print(a.split("啊啊"))
```



```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
['哈哈哈', '嘿']

Process finished with exit code 0

```



#### capitalize 与 title

capitalize：第一个首字母大写

title：所有首字母大写

```
a = "how are you."
print(a.capitalize())
```

```
a = "how are you."
print(a.title())
```



#### startswith 与 endswith

startswith：检查是否以""内的内容作为开始 

endswith：检查是否以""内的内容作为结束

```
a = "how are you."
print(a.startswith("are"))
```

```
a = "how are you"
print(a.endswith("you"))
```



#### lower 与 upper

lower 所有的字母变成小写

upper 所有的字母变成大写

```
a = "how are you"
print(a.lower())
```

```
a = "how are you"
print(a.upper())
```



#### lstrip ，rstrip，strip

istrip：删除左边空格

rstrip：删除右边空格

strip：删除左右两边空格

```
print(a.lstrip())
```

```
print(a.rstrip())
```

```
print(a.strip())
```



#### isdigit

判断是否是数字类型

```
a = "123"
print(a.isdigit())
```

  

#### join

将某个字符插入到每个字符之间

```
a = "今天天气晴朗。"
print("1".join(a))

```





### 列表

#### 列表循环遍历

**通过for**

```
a = "张山","四四","四千"

for q in a:
    print(q)
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
张山
四四
四千

Process finished with exit code 0

```



```
a = "张山","四四","四千"

b = len(a)
print(b)
for c in range(b):
    print(c)
    print(a[c])
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
3
0
张山
1
四四
2
四千

Process finished with exit code 0
```

**通过while**

```
a = "张山","四四","四千"
len = len(a)
b = 0
while b<len:
    print(a[b])
    b+=1
```





### 列表的常见操作

#### 增加元素

append

在结尾添加元素

注意列表为中括号

```
a = ["11","22","33"]
a.append('44')
print(a)
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
['11', '22', '33', '44']

Process finished with exit code 0

```

insert

在任意位置添加元素

```
a = ["11","22","33"]
a.insert(0,'44')
print(a)
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
['44', '11', '22', '33']

Process finished with exit code 0

```

extend

当要把列表添加到列表时，可以用extend将列表分解成元素添加到另一个列表中

```
a = ["11","22","33"]
b = ["44","55"]
a.extend(b)
print(a)
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
['11', '22', '33', '44', '55']

Process finished with exit code 0

```



#### **修改元素**

```
a = ["11","22","33","44","55"]
a[2]="99"
print(a)
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
['11', '22', '99', '44', '55']

Process finished with exit code 0

```

#### 查找元素

分为in\not in\index\count四种

```
a =["11","22","33","44"]
b = input("请输入")
if b in a:
    print("正确")
if b not in a:
    print("错误")
```

```
a =["11","22","33","44","11"]
print(a.count("11"))
print(a.index('22'))
```



#### 删除元素

dle

直接del删除

```
a =["11","22","33","44","11"]
del a[2]
print(a)
```

pop

删除之后可以让删除的内容显示出来

```
a =["11","22","33","44","11"]
print(a.pop(3))
print(a)
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
44
['11', '22', '33', '11']

Process finished with exit code 0

```

remove

根据内容直接删除

```
a =["11","22","33","44","11"]
print(a.remove("22"))
print(a)
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
None
['11', '33', '44', '11']

Process finished with exit code 0
```



#### 排序元素

一般用于数字

sort用于顺序排序

加入reverse=True变为倒序排序（注意T为大写）



```
a =[56,74,22,75]
a.sort(reverse=True)
print(a)
```



```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
[75, 74, 56, 22]

Process finished with exit code 0

```

​                                                                                      



### 元祖

元祖类似于列表，但元祖内容不能修改，且元组使用小括号，列表使用大括号

### 字典

字典的每个元素是由两个部分组成的

键（key）  值（value）

取值不能像列表一样通过下标取值可以通过键来取值



### 字典常用操作方法

#### 查看元素

```
a = {1:11,2:22,"名字":"小王","爱好":"唱歌"}
print(a.get("名字"))
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
小王

Process finished with exit code 0

```

**加上.get 查找字典里没有的不会报错**



#### 修改及添加元素

```
a = {1:11,2:22,"名字":"小王","爱好":"唱歌"}

a["名字"] = "小刘"
a["性别"] = "男"
print(a)
```

**字典里没有的元素，直接添加**



#### 删除元素

```
a = {1:11,2:22,"名字":"小王","爱好":"唱歌"}

del a["爱好"]
print(a)
```

del 删除字典内的某一个数据

```
a = {1:11,2:22,"名字":"小王","爱好":"唱歌"}

a.clear()
print(a)
```

clear清除字典内全部数据（不删除字典本身）



#### len



```
a = {1:11,2:22,"名字":"小王","爱好":"唱歌"}

print(len(a))
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
4

Process finished with exit code 0
```

查看有多少对 键值



#### keys/values



```
a = {1:11,2:22,"名字":"小王","爱好":"唱歌"}

print(a.keys())
print(a.values())
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
dict_keys([1, 2, '名字', '爱好'])
dict_values([11, 22, '小王', '唱歌'])

Process finished with exit code 0

```

返回一个所有的键/值的列表



#### items

```
a = {1:11,2:22,"名字":"小王","爱好":"唱歌"}

print(a.items())
```



```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
dict_items([(1, 11), (2, 22), ('名字', '小王'), ('爱好', '唱歌')])

Process finished with exit code 0
```

返回一个所有的键：值的元祖的列表



#### 遍历

通过for in来遍历

```
a = {1:11,2:22,"名字":"小王","爱好":"唱歌"}

for key in a.keys():
    print(key)
for value in a.values():
    print(value)
for item in a.items():
    print(item)
for key,value in a.items():
    print(f"key={key},对应的value为{value}")
```

遍历所有的key

遍历所有的value

遍历所有的key和value

遍历所有对应的key和value
