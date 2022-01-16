## end=""

```

为末尾[end](https://www.baidu.com/s?wd=end&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)传递一个空字符串，这样print函数不会在字符串末尾添加一个换行符，而是添加一个空字符串，其实这也是一个语法要求，表示这个语句没结束。 
```

### isalpha

```
str.isalpha() 方法检测字符串是否只由字母组成。 
```

##  isspace

```
Python isspace() 方法检测字符串是否只由空格组成。
```

## isdigit

```
Python isdigit() 方法检测字符串是否只由数字组成。
```



## from sys import stdout

```
sys.stdout.write("") 等于 print("",end="")
```



## sep = ‘’

```
调用多个字符之间使用字符隔开（space）
```



## lambda常见用法

  由于lambda语法是固定的，其本质上只有一种用法，那就是定义一个lambda函数。
    在实际中，根据这个lambda函数应用场景的不同，可以将lambda函数的用法扩展为以下几种：

1、将lambda函数赋值给一个变量，通过这个变量间接调用该lambda函数。
示例：
add = lambda x, y: x+y
相当于定义了加法函数lambda x, y: x+y，并将其赋值给变量add，这样变量add就指向了具有加法功能的函数。
这时我们如果执行add(1, 2)，其输出结果就为 3。

2、将lambda函数赋值给其他函数，从而将其他函数用该lambda函数替换。
示例：

```
#为了把标准库tinme中的函数sleep的功能屏蔽（mock),我们可以在程序初始化时调用：
time.sleep=lambda x:None
#这样，在后续代码中调用time库的sleep函数将不会执行原有的功能
例如time.sleep(3)	# 程序不会休眠 3 秒钟，而是因为lambda输出为None，所以这里结果是什么都不做
1
2
3
4
5
3、将lambda函数作为参数传递给其他函数

```



## 倒序输出

  ### reverse()反转

```
a = [1,2,3,4,5,6]
a.reverse()  
print(a)
```

### 切片用法：创建一个与原字符串顺序相反的字符串

```
a = [1,2,3,4,5,6]
a = a[::-1]    
print(a)
```



