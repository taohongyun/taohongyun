# 函数

### 

函数就是具有独立功能的代码块，可以提高代码的复用性和精确性（复制粘贴无法提供精确性且很占位置）



### 定义和调用函数



```
def 感悟():
    print("         -----        ")
    print("         人生苦短         ")
    print("         及时行乐         ")
    print("         -----        ")
感悟()
```



```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
         -----        
         人生苦短         
         及时行乐         
         -----        

Process finished with exit code 0
```

**定义：通过def 空格函数名()：**

​					  **代码缩进**

**调用：函数名()**



### 函数参数



```
def 结果(a,b):
    c = a+b
    print('你需要的结果为',c)

结果(1,2)
结果(a=1,b=2)
结果(b=2,a=1)
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
你需要的结果为 3
你需要的结果为 3
你需要的结果为 3

Process finished with exit code 0
```

### 返回值

```
def jieguo(a,b,d):
    c=a+b
    e=c-d

    print("得到的结果为",e)
    return e


print(jieguo(1, 2, 3))
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
得到的结果为 0
0

Process finished with exit code 0
```

当需要查看返回值的时候可以在def最后边加上return

如果不加 **return**的话 输出出来的是**None**

(调用完return以后，函数就结束了，后边无论有什么都不会运行，return代表函数结束)



f

### 调用返回值

```
def 结果(a,b):
    c=a+b
    print(c)
    return c

num = 结果(1,2)


def 结果2(x,y,z):
    print(x)
    q=x+y+z
    print(q)
    return q


结果2(num, 2, 3)
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
3
3
8

Process finished with exit code 0

```



**第一个函数的返回值可以作为第二个函数的参数**



# 面向对象



### 什么是面向对象

面向过程和面向对象是当前两种主流的软件开发思想

**洗衣服**

**手洗(面向过程)**

**机洗(面向对象)**

面向对象具有封装性、继承性、多态性的特性。

面向对象是一种对现实世界理解和抽象的方法，是计算机编程技术发展到一定阶段的产物。



### 类、对象、属性、方法

class Car()：类

（类的名称的首字母要大写（变量和函数不需要）

def bycar、def move、def ac；在类里边的函数叫方法

（方法不打印结束了以后需要pass。否则会报错）

car=Car()；对象

```
class Car():
    def bycar(self):
        print("乘坐汽车")
    def move(self):
        print("开动汽车")
    def ac(self):
        print("汽车空调")
car=Car()
car.bycar()
car.move()
car.ac()
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
乘坐汽车
开动汽车
汽车空调

Process finished with exit code 0

```





通过一个类可以创建多个对象，每一个对象对应的参数值都不一样，这个时候就可以用 '__init__'来设置多个实参

```
class 英雄(object):
    def __init__(self,name,hp,atk):
        self.name = name
        self.hp = hp
        self.atk = atk

    def info(self):
        print(self.name)
        print(self.hp)
        print(self.atk)

luban = 英雄("鲁班七号",2000,100)
luban.info()
houyi = 英雄("后羿",1000,500)
houyi.info()
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
鲁班七号
2000
100
后羿
1000
500

Process finished with exit code 0
```



**注意：**

1. 在类内部获取 属性 和 实例方法，通过self获取
2. 在类外部获取 属性 和 实例方法，通过对象名来获取  
3. 如果一个类有多个对象，每个对象的属性是各自保存的，都有各自独立的地址
4. 但是实例方法是所有对象共享的，只占用一份内存空间，类会通过self来判断是哪个对象调用了实例方法



### 其他魔法方法

#### str()方法 

输出打印的方法，配合return使用

```
class 英雄(object):
    def __init__(self,name,hp,atk):
        self.name = name
        self.hp = hp
        self.atk = atk

    def info(self):
        print(self.name)
        print(self.hp)
        print(self.atk)

    def __str__(self):
        return "英雄{}数据：生命值{}，攻击{}".format(self.name, self.hp, self.atk)

luban = 英雄("鲁班七号",2000,100)
# luban.info()
houyi = 英雄("后羿",1000,500)
# houyi.info()
print(luban)
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
英雄鲁班七号数据：生命值2000，攻击100

Process finished with exit code 0

```



#### del方法

当对象被销毁的时候就会被调用

```
class 英雄(object):
    def __init__(self,name,hp,atk):
        self.name = name
        self.hp = hp
        self.atk = atk

    def info(self):
        print(self.name)
        print(self.hp)
        print(self.atk)

    def __str__(self):
        return "英雄{}数据：生命值{}，攻击{}".format(self.name, self.hp, self.atk)
    def __del__(self):
        print(f"我被{self.name}打死了")


luban = 英雄("鲁班七号",2000,100)
luban.info()
print(luban)
del luban 
houyi = 英雄("后羿",1000,500)
houyi.info()
print(houyi)
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
鲁班七号
2000
100
英雄鲁班七号数据：生命值2000，攻击100
我被鲁班七号打死了
后羿
1000
500
英雄后羿数据：生命值1000，攻击500
我被后羿打死了

Process finished with exit code 0
```





## 继承

### 单继承

```
class Shifu():
    def __init__(self):
        self.fangfa = "配方"
    def zuodangao(self):
        print(f"使用了{self.fangfa}做了一份蛋糕")
    def __str__(self):
        return f"使用了{self.fangfa}做了一份蛋糕"
# a = Shifu()
# a.zuodangao()
# print(a)
class Tudi(Shifu):
    pass
b = Tudi()
b.zuodangao()
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
使用了配方做了一份蛋糕

Process finished with exit code 0

```



**子类在类名的括号内写上父类的名字，直接操作下一步，就可以使用父类的属性和方法**

 

### 多继承

```
class Shifu():
    def __init__(self):
        self.fangfa = "配方"
    def zuodangao(self):
        print(f"使用了{self.fangfa}做了一份蛋糕")
    def chouyan(self):
        print('学会了抽烟')
    def __str__(self):
        return f"使用了{self.fangfa}做了一份蛋糕"
# a = Shifu()
# a.zuodangao()
# print(a)
class Shifu1():
    def __init__(self):
        self.fangfa = "配方1"
    def zuodangao(self):
        print(f"使用{self.fangfa}做了一份蛋糕")
    def game(self):
        print("学会了打游戏")

class Tudi(Shifu,Shifu1):
    pass
b = Tudi()
b.zuodangao()
b.chouyan()
b.game()
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
使用了配方做了一份蛋糕
学会了抽烟
学会了打游戏

Process finished with exit code 0

```

**当多继承的方法和属同名时，默认继承第一个，方法和属性名字不同名时都会继承**





### 子类重写父类的同名属性和方法

```
class Shifu():
    def __init__(self):
        self.fangfa = "配方"
    def zuodangao(self):
        print(f"使用了{self.fangfa}做了一份蛋糕")
    def chouyan(self):
        print('学会了抽烟')
    def __str__(self):
        return f"使用了{self.fangfa}做了一份蛋糕"
# a = Shifu()
# a.zuodangao()
# print(a)
class Shifu1():
    def __init__(self):
        self.fangfa = "配方1"
    def zuodangao(self):
        print(f"使用{self.fangfa}做了一份蛋糕")
    def game(self):
        print("学会了打游戏")

class Tudi(Shifu,Shifu1):
    def __init__(self):
        self.fangfa = "配方2"
    def zuodangao(self):
        print(f"使用了{self.fangfa}做了一份蛋糕")
b = Tudi()
b.zuodangao()
# b.chouyan()
# b.game()
```

```py
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
使用了配方2做了一份蛋糕

Process finished with exit code 0

```

**当子类自己本身有同父类同名的属性和方法时，优先使用自己的内容**



### **子类调用父类同名属性和方法**



```
class Shifu():
    def __init__(self):
        self.fangfa = "配方"
    def zuodangao(self):
        print(f"使用了{self.fangfa}做了一份蛋糕")
    def chouyan(self):
        print('学会了抽烟')
    def __str__(self):
        return f"使用了{self.fangfa}做了一份蛋糕"
# a = Shifu()
# a.zuodangao()
# print(a)
class Shifu1():
    def __init__(self):
        self.fangfa = "配方1"
    def zuodangao(self):
        print(f"使用{self.fangfa}做了一份蛋糕")
    def game(self):
        print("学会了打游戏")

class Tudi(Shifu,Shifu1):
    def __init__(self):
        self.fangfa = "配方2"
    def zuodangao(self):
        print(f"使用了{self.fangfa}做了一份蛋糕")
    def old(self):
        Shifu.__init__(self)
        self.zuodangao()
    def new(self):
        Shifu1.__init__(self)
        self.zuodangao()

b = Tudi()
b.zuodangao()
b.old()
b.new()
```



```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
使用了配方2做了一份蛋糕
使用了配方做了一份蛋糕
使用了配方1做了一份蛋糕

Process finished with exit code 0

```



**无论何时何地，self都是i表示子类的对象。在调用父类方法时，通过传递self参数，来控制方法和属性的访问修改。**





### **多层继承**

```
class Shifu():
    def __init__(self):
        self.fangfa = "配方"
    def zuodangao(self):
        print(f"使用了{self.fangfa}做了一份蛋糕")
    def chouyan(self):
        print('学会了抽烟')
    def __str__(self):
        return f"使用了{self.fangfa}做了一份蛋糕"
# a = Shifu()
# a.zuodangao()
# print(a)
class Shifu1():
    def __init__(self):
        self.fangfa = "配方1"
    def zuodangao(self):
        print(f"使用{self.fangfa}做了一份蛋糕")
    def game(self):
        print("学会了打游戏")

class Tudi(Shifu,Shifu1):
    def __init__(self):
        self.fangfa = "配方2"
    def zuodangao(self):
        print(f"使用了{self.fangfa}做了一份蛋糕")
    def old(self):
        Shifu.__init__(self)
        Shifu.zuodangao(self)
    def new(self):
        Shifu1.__init__(self)
        Shifu1.zuodangao(self)

class Xtudi(Tudi):
    pass
c = Xtudi()
c.chouyan()
c.zuodangao()
c.new()
c.old()
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
学会了抽烟
使用了配方2做了一份蛋糕
使用配方1做了一份蛋糕
使用了配方做了一份蛋糕

Process finished with exit code 0

```

**在继承的基础上又进行了第二次继承**



### 通过super()来调用父类中的方法

```
class Shifu():
    def __init__(self):
        self.fangfa = "配方"
    def zuodangao(self):
        print(f"使用了{self.fangfa}做了一份蛋糕")
    def chouyan(self):
        print('学会了抽烟')
    def __str__(self):
        return f"使用了{self.fangfa}做了一份蛋糕"
# a = Shifu()
# a.zuodangao()
# print(a)
class Shifu1():
    def __init__(self):
        self.fangfa = "配方1"
    def zuodangao(self):
        print(f"使用{self.fangfa}做了一份蛋糕")
    def game(self):
        print("学会了打游戏")

class Tudi(Shifu,Shifu1):
    def __init__(self):
        self.fangfa = "配方2"
    def zuodangao(self):
        print(f"使用了{self.fangfa}做了一份蛋糕")
    def old(self):
        Shifu.__init__(self)
        super().zuodangao()
    def new(self):
        Shifu1.__init__(self)
        super().zuodangao()

class Xtudi(Tudi):
    pass
c = Xtudi()
c.chouyan()
c.zuodangao()
c.new()
c.old()
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
学会了抽烟
使用了配方2做了一份蛋糕
使用了配方1做了一份蛋糕
使用了配方做了一份蛋糕

Process finished with exit code 0

```

**通过super().zuodangao()来取代Shifu1.zuodangao(self)**

 



# 文件



### 打开文件访问模式

| 访问模式 | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| r        | 以只读的方式打开文件。文件的指针将会放在文件的开头，这是默认模式。 |
| w        | 打开一个文件只用于写入。如果该文件已存在则将其覆盖。如果该文件不存在，则创建新文件。 |
| a        | 打开一个文件用于追加。如果该文件已经存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。 |
| rb       | 以二进制格式打开一个文件用于只读。文件指针将会放在文件的开头。这是默认模式。 |
| wb       | 以二进制格式打开一个文件只用于写入。如果该文件已存在则将其覆盖。如果该文件不存在，则创建一个新文件。 |
| ab       | 以二进制格式打开一个新文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，则创建新文件进行写入。 |



### 读取文件

```
a = open("test.txt","r")
print(a.read())
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
nihao
nihao
nihao

Process finished with exit code 0

```

同文件夹下读取一个名为 test.txt 的文件

read() 读取的是整个文件，

read()括号内可以加参数，添加读取的数量

当文件足够大的时候不要一次加载完，要分为部分加载





```
a = open("test.txt","r")
print(a.readline())
```

readline() 读取一行数据



```
a = open("test.txt","r")
print(a.readlines())
```

readlines() 读取所有行的数据



```
a = open("test.txt","r",encoding="utf8")
print(a.readlines())
```

当编码格式不一样出现乱码的时候 就在打开后边假如统一的 编码  **encoding="utf8"**



### 写入文件

```
a = open("test.txt","w")
a.write("nihao")
```

写入数据会把之前的数据删掉，写入新的数据。



### 补充写入文件

```
a = open("test.txt","a")
a.write("nihao")
```

写入数据不会把之前的数据删掉，直接补充新的数据。

需要换行在需要换行的内容后边加 **\a**





### 应用：复制文件

```
# 获取源文件的名字（包含路径)
filename = input("请输入要备份的文件名称：")

# 打开源文件
oldFile = open(filename,"r")

# 获取备份文件名字（备份文件名字=源文件名字+_复件+后缀名)
fileFlagNum = filename.rfind(".")
fileFlag = filename[fileFlagNum:]
print(fileFlag)
newFileName = filename[0:fileFlagNum]+"_复件"+fileFlag
print(newFileName)

# 写入备份文件
newfile = open(newFileName,"w")
for linecontent in oldFile.readlines():
    newfile.write(linecontent)

# 关闭文件，释放资源
oldFile.close()
newfile.close()
```



### 文件相关的操作

#### 文件重命名

通过 os.rename 来给文件重命名，括号前边为旧名字，后边为新名字。

```
import os
os.rename("test.txt","新名字.txt")
```



#### 删除文件

通过 os.remove 来删除文件，括号内为要删除的文件名。

```
import os
os.remove("新名字.txt")
```



#### 新建文件夹

通过 os.mkdir 来新建文件夹，括号内为要新建的文件夹名。

```
import os
os.mkdir("文件夹")
```



#### 获取当前目录

```
import os

print(os.getcwd())
```



#### 改变默认目录

```
import os

os.chdir("./文件夹")

print(os.getcwd())
```



#### 获取目录列表

```
import os

print(os.listdir("./"))
```



#### 删除文件夹

```
import os

os.rmdir("文件夹")
```



#### 应用1：批量修改文件名

```
a = "./文件夹/"
import os


listname = os.listdir(a)

for b in listname:
    newname = "【熊猫出品】"+b
    os.rename(a+b,a+newname)
```

#### 应用2：通过 if 来选择添加还是删除

```
a = "./文件夹/"
import os


listname = os.listdir(a)

flag = 1

for b in listname:
    if flag == 1:
        newname = "【熊猫出品】" + b

    if flag == 2:
        num = len("【熊猫出品】")
        newname = b[num:]

    os.rename(a+b,a+newname)
```



# 异常

### 捕获异常

```
a = "test1.txt"
try:
    b = open(a,"r")
    print(b.read())
    b.close()
except:
    pass
print("hahha")
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
hahha

Process finished with exit code 0

```

- 把可能出现问题的代码，放在try中。（产生异常的代码）

- 把处理异常的代码，放在except中。（处理异常代码的方法）

- pass可以替换成print，输出相应的原因。

  

### except捕获多个异常

```
a = "test1.txt"
try:
    num = 1/0
    b = open(a,"r")
    print(b.read())
    b.close()
except (IndentationError,ZeroDivisionError):
    pass
print("hahha")
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
hahha

Process finished with exit code 0

```



### 获取异常的信息描述

```
a = "test1.txt"
try:
    # num = 1/0
    b = open(a,"r")
    print(b.read())
    b.close()
except FileNotFoundError as q:
    print("问题点",q)


print("hahha")
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
问题点 [Errno 2] No such file or directory: 'test1.txt'
hahha

Process finished with exit code 0
```



### else

如果没有捕获到异常则执行else里的内容

```
a = "test.txt"
try:
    # num = 1/0
    b = open(a,"r")
    print(b.read())
    b.close()
except FileNotFoundError as q:
    print("问题点",q)
else:
    print("没有问题点")


print("hahha")
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
nihaonihaonihaonihao
nihao
nihao

没有问题点
hahha

Process finished with exit code 0
```



### 注意

**close 没有异常在else后边，有异常在excep后边**



### finally

在程序中，如果一个段代码必须要执行，即无论异常是否产生都要执行，那么二此时就需要使用finally。（比如文件关闭，释放锁，把数据库连接返还给连接池等）

```
a = "test.txt"
try:

    b = open(a,"r")
    print(b.read())
    b.close()
    num = 1 / 0
except:
    print("有问题")

finally:
    b.close()
    print("关闭文件")

print("hahha")
```



### 异常传递

```
a = "test.txt"
try:
    try:

        b = open(a,"r")
        print(b.read())
        b.close()
        num = 1 / 0
    except fdgadb:
        print("有问题")

    finally:
        b.close()
        print("关闭文件")

    print("hahha")
except:
    print("没有这个文件")
```

```python
C:\Users\pc\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:/Users/pc/PycharmProjects/pythonProject1/123.py
nihaonihaonihaonihao
nihao
nihao

关闭文件
没有这个文件

Process finished with exit code 0

```



内层except没有找到对应的问题点时，会向外传递1111111

22222222
