









### 学习准备

功能测试经验 需求、测试用例、测试工具、测试方法

熟悉接口测试 接口的概念、接口测试

练习网址：http://ihrm-test.itheima.net/#/login

### 目标

能够用charles 来分析前后端的问题

能够用charles 模拟弱网环境

能使用charles的断点构建异常的测试场景

### charles 是什么

它是一款基于http协议的代理服务器，通过成为电脑或者浏览器的代理，然后截取请求和请求结果达到分析抓包的目的。

### 原理

前置步骤

1. 需要运行charles并配置代理
2. 在客户端上面需要配置代理

步骤

1. 由客户端发出请求
2. charles 接收再发送到服务端
3. 服务端返回请求结果给charles
4. 由chailes转发给客户端

### charles 的功能

- 支持http 及 https 的代理
- 支持流量控制（弱网测试）
- 支持接口并发请求（性能测试、压力测试）
- 支持重发网络测试
- 支持断点调试（构建异常测试场景）

设置代理proxy

白名单黑名单重定向 tools

###  访问控制和代理设置

#### 访问控制

![](C:\Users\pc\Desktop\软件测试\charles相关截图\访问控制.jpg)



#### charles代理设置

![](C:\Users\pc\Desktop\软件测试\charles相关截图\代理设置.jpg)



#### windows代理设置

![](C:\Users\pc\Desktop\软件测试\charles相关截图\windows代理设置1.jpg)



![](C:\Users\pc\Desktop\软件测试\charles相关截图\windows代理设置2.jpg)



#### mac代理设置

![](C:\Users\pc\Desktop\软件测试\charles相关截图\mac代理设置1.jpg)



#### ios代理设置

![](C:\Users\pc\Desktop\软件测试\charles相关截图\ios代理设置.jpg)



#### 安卓代理设置

![](C:\Users\pc\Desktop\软件测试\charles相关截图\安卓代理设置.jpg)



### 证书配置

#### windows证书配置

![](C:\Users\pc\Desktop\软件测试\charles相关截图\windows证书设置.jpg)



#### mac证书配置

![](C:\Users\pc\Desktop\软件测试\charles相关截图\mac证书设置.jpg)



#### ios证书配置

![](C:\Users\pc\Desktop\软件测试\charles相关截图\ios证书配置1.jpg)

![](C:\Users\pc\Desktop\软件测试\charles相关截图\ios证书配置2.jpg)



### 流量配置（弱网）

![](C:\Users\pc\Desktop\软件测试\charles相关截图\流量配置（弱网）.jpg)



### 断点配置

![](C:\Users\pc\Desktop\软件测试\charles相关截图\断点配置.jpg)



![](C:\Users\pc\Desktop\软件测试\charles相关截图\断点配置2.jpg)