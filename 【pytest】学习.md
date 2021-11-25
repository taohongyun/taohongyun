## pytest

pytest时python的一种单元测试框架，同自带的unittest框架类似，相比unittest框架使用起来更简洁，效率更高。



### 特点

非常容易上手，入门简单，文档丰富，文档中有很多实例可以参考

支持简单的单元测试和复杂的功能测试

支持参数化

执行测试过程中可以将某些测试跳过，或者对某些预期失败的case标记成失败

支持重复执行失败的case

支持运行由Nose.Unittest编写的测试case

具有很多第三方插件，并且可以自定义拓展

方便的和持续继承工具集成





### 入门案例

打印如果需要带入内容则在括号内加"-s"，需要只需要一个打印一个文件，则在括号内加入文件名

```
import pytest

def test1():
    print("testa")
    return 1 * 0


def test2():
    print("testb")
    return 1 / 0


if __name__ == "__main__":
    pytest.main("-s","test1")
```



### 自动识别规则

#### 默认规则

直接执行pytest

从模块、类、函数及方法、其他依次迭代寻找test识别

#### 自定义规则 

可以通过配置文件进行指定识别



### 配置文件

需要在同一个文件夹中新建一个ini文件

```
[pytest]

addopts = -s ; 选项 通常为-或者--开头内容

testpaths = ./scripts ; 测试模块所在目录

python_files = test_*.py *test.py ; 测试模块文件名称规则，多个内容用空格分隔

python_classes = Test_* ; 测试类名称规则

python_functions = test_* ; 测试函数或者方法的文件名称
```

注意

windows系统 可能运行会报错，在配置文件中有中文的情况，需要调整配置文件的编码为GBK而不使用UTF-8

配置文件中的路径、文件名、类名、函数名、规则是不区分大小写的





### 断言、标记、跳过

```
import pytest

@pytest.mark.skip("我想跳过")
def test1():
    print("testc")
    assert 1 == 2


def test2():
    print("testd")
    assert 1 == 1


@pytest.mark.xfail()
def test3():
    print("testd")
    assert 1 == 3

if __name__ == "__main__":
    pytest.main("-s")
```

断言：assert 后边加入自己的断言

标记：在需要标记的内容上边加入 @pytest.mark.xfail()  

跳过：在需要跳过的内容上边加入 @pytest.mark.skip() 





### 参数化

对于相似的过程，但数据不一样的时候，可以使用参数化



argnames 参数名称 列表或元祖

argvalues 参数值 列表套元祖

ids 测试id



```
mport pytest

@pytest.mark.parametrize(["a","b"],[(1,2),(9,2),(1,2),(1,2),(1,2),(1,2),])
def test1(a,b):
    print("testc")
    assert a+b < 10


if __name__ == "__main__":
    pytest.main("-s")

```



### 夹具



#### setup  teardown

在测试之前或者之后执行，用于固定测试环境，及清理回收测试资源。



##### 模块级别

```
import pytest
def setup_module(args):
    print("set_module",args)
def teardown_module(args):
    print("teardown_module",args)

def test1():
    print("---","test1")

def test2():
    print("---","test2")


class Testone():
    def testa(self):
        print("testa")
    def testb(self):
        print("testb")


if __name__ == '__main__':
    pytest.main("-s")
```



##### 函数级别

```
import pytest
def setup_function(args):
    print("set_function",args)
def teardown_function(args):
    print("teardown_function",args)

def test1():
    print("---","test1")

def test2():
    print("---","test2")


class Testone():
    def testa(self):
        print("testa")
    def testb(self):
        print("testb")


if __name__ == '__main__':
    pytest.main("-s")
```



##### 类级别

```
import pytest
def setup_function(args):
    print("set_function",args)
def teardown_function(args):
    print("teardown_function",args)

def test1():
    print("---","test1")

def test2():
    print("---","test2")


class Testone():
    def setup_class(args):
        print("set_class", args)

    def teardown_class(args):
        print("teardown_class",args)
    def testa(self):
        print("testa")
    def testb(self):
        print("testb")


if __name__ == '__main__':
    pytest.main("-s")
```





#### fixture装饰器

除了setup和teardown，pytest提供fixture进行更为强大的夹具使用

我们可以把夹具看为一个过程

它也可以是具备返回值的，（该过程创建某种资源），正是我们测试中所需要的。
