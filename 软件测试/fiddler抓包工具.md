### 简介

位于客户端与服务器端的一个代理

### 应用场景

接口调试和接口测试，没有接口文档的时候

线上调试，发现bug

判断前后端bug

mock测试（模拟测试）：没有前端的情况下进行后端的接口测试

弱网测试

### 安装与介绍

fiddlersetup 

证书生成器（主要是用于生成fiddler的证书，作用是使fiddler抓取到https协议的报文）

### 原理

打开fiddler之后就会自动监听端口8888（本机）客户端的请求

fiddler将请求发送给服务器端

服务器端处理请求，将响应发送给fiddler

fiddler将响应转发给客户端



### 软件界面

#### 菜单栏

File 

- capture traffic  是否fiddler注册为代理
- new viewer   打开一个新的fiddler窗口
- load archive  重新夹杂i之前的文件
- save  保存   保存所有包  保存选中的包  保存请求  保存响应
- import sessions  导入
- export sessions   导出

edit 

- 复制
- 删除
- 选中所有
- 恢复删除
- 粘贴
- 标记
- 解锁会话

Rules

- Hide CONNECTs
- Hide 304s

隐藏通道包、信息304的包

- Automatic Breakpoints   before request  请求之前   after responses  响应之后 设置断点
- Customize Rules  自定义脚本
- Require Proxy Authentication   客户端安装证书
- Performance  =》  simulate modem speeds 模拟弱网测试

Tool

- reset script  重置脚本

View 

用于展示一些窗口



#### 工具栏

备注

重新发送包

断点没有执行完成  点击执行完成



解码

保存的会话的数量

选择抓包或者监听的程序 所有的进程

查找包

保存包

打开浏览器

清空浏览器的缓存



#### 抓取的数据报文

编号/状态码/协议/主机的ip地址/路径/包的大小/ /内容的格式/来自哪个进程/备注/自定义



#### 功能页签

/ /统计/**检查**（请求和响应）/**自动响应**（线上调试）/**接口测试**/ /fiddler自身原生脚本（弱网测试需要修改这里的脚本）/日志/**过滤器**/时间戳





shift + F5  去缓存刷新 （有缓存直接访问缓存 不会访问服务器）