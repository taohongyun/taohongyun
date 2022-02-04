### linux优势

- 跨平台的硬件支持（对于一些硬件windows需要一些驱动）
- 丰富的软件支持  （linux下只区分32位，64位。一般的软件在linux系统下兼容性要比windows下少很多）
- 多用户多任务 （多终端操作，提高效率）
- 可靠的安全性
- 良好的稳定性
- 完善的网络功能
- 

### 软件运行环境

从操作系统方面来看，linux服务器



### 搭建测试环境

测试环境，预发布环境，线上（生产）环境

软件包（部署文档），测试服务器ip，用户名，密码

#### finalshell远程连接服务器

新建连接

名称随便写

主机填写测试服务器的ip (ifconfig)

#### 安装依赖环境

```
yum = Yellow dog Updater, Modified 主要功能是更方便的添加/删除/更新RPM包. 它能自动解决包的倚赖性问题. 它能便于管理大量系统的更新问题 
```

yum list | grep java  

yum install java-1.8.0-openjdk.x86_64

#### 上传tomcat包

工具 lrzsz  安装 ：yum install lrzsz  卸载 yum -y remove lrzsz

rz  上传文件

sz  保存文件

#### 解压tomcat

unzip apache-tomcat-8.5.73.zip

#### 配置权限 

cd apache-tomcat-8.5.73

cd bin 

chomd +x  执行权限

chomd +x *.sh 给予所有.sh文件可执行权限

 注意：文件默认只有可读权限的

#### 运行tomcat

./startup.sh

#### 关闭防火墙

service firewalld stop  关闭防火墙

service firewalld start  打开防火墙

service firewalld restart  重启防火墙

#### 上传war包

之前装过lrzsz工具，这里可以直接上传

- rz + 回车  
- 选择war包
- mv + war包名 + webapps ：将war包移动到webapps文件夹中

#### 修改tomcat端口

cd ./apache-tomcat-8.5.73/conf    切换到conf文件夹

vi server.xml  

光标下键向下继续显示未显示出来的内容

命令输入输入i ,进入可编辑模式，按住光标进行修改，

修改完成后按esc退出修改

命令输入输入：wq  退出并保存

### 查看日志

查看日志： tail -f xxx.log    # -f 从尾部开始看，为实时监听查看

管道查看（关键字）：tail -f xxx.log | grep "tomcat"



### 结束进程

netstat -anp|grep 8080  查看占用8080端口的pid







## 

## 萤火小程序商场所需要的运行环境（LNMP）

码云项目环境链接：https://gitee.com/xany/bestshop-php

建议使用环境：Linux + Nginx1.14 + PHP7.1 + MySQL5.6    LNMP

​	Nginx：是一款轻量级的web服务器/反向代理服务器以及电子邮件（imap/pop3）代理服务器，优点是占用内存小，开发能力强

​	Mysql：开源免费支持多平台，是互联网公司应用最为广泛的关系型数据库

​	PHP：是目前最流行的编程语言

### 工作原理

用户访问web服务器的ip地址(URL)，nginx提供一个网站供给用户访问，php语言编写的php软件放在nbinx中运行，软件中的数据存放在mysql数据库中

浏览器 --》应用服务器 --》mysql数据库 --》应用服务器  --》浏览器



### 工具

libiconv-1.14.tar.gz

mysql-5.6.35-linux-glibc2.5-x86_64.tar.gz

navicat112_mysql_cs_x64.tar.gz

nginx-1.10.2.tar.gz

php-5.3.29.tar.gz

项目包





### 搭建第一个中间件Nginx

#### Nginx安装

nginx降权

niginx给予root权限有风险所以要降权  (nginx有风险会导致整个系统都有风险)，添加一个降权用户

```
useradd www -s /sbin/nologin -M

#-s：表示指定用户所用的shell 
#nologin：不能访问linux系统  /sbin/nologin：表示不登录
#-M：表示不能创建主目录

 cat /etc/passwd
 降权之后查看是否创建成功
```



编译安装Nginx

```
解压：
tar -xzf nginx-1.10.2.tar.gz
-x:从tar包把文件提取出来(解压)  -z:压缩方式是gzip，所以解压也是用gzip(通过gzip压缩来进行解压)  -f:表示gz文件路径（代表是一个文件）

配置：切换到解压后的nginx包中
./configure --prefix=/data/server/nginx
--prefix：指定配置地址

编译：
make

安装：
make install

修改配置文件：
vim /data/server/nginx/conf/nginx.conf
1.进入文件编辑文件
2.找到#user nobody;
3.在下边添加 uesr www; 注意下边添加的没有# 注意user www后一定要加分号，不然报错

```

```
常见问题：
#在初次安装Nginx过程中，经常会出现这样的错误： make： *** 没有规则可以创建“default”需要的目标“build”。
需要安装依赖包：
yum install pcre-devel
yum install zlib zlib-devel
yum install openssl openssl-devel

```



#### 检查结果

关闭nginx

```
/data/server/nginx/sbin/nginx -s stop
```

启动nginx

```
/data/server/nginx/sbin/nginx
```

重启nginx

```
/data/server/nginx/sbin/nginx -s reload
```

启动后检查

```
netstat -tnulp|grep nginx
```

```
netstat后命令详解：

-a或--all 显示所有连线中的Socket。
-A<网络类型>或--<网络类型> 列出该网络类型连线中的相关地址。
-c或--continuous 持续列出网络状态。
-C或--cache 显示路由器配置的快取信息。
-e或--extend 显示网络其他相关信息。
-F或--fib 显示路由缓存。
-g或--groups 显示多重广播功能群组组员名单。
-h或--help 在线帮助。
-i或--interfaces 显示网络界面信息表单。
-l或--listening 显示监控中的服务器的Socket。
-M或--masquerade 显示伪装的网络连线。
-n或--numeric 直接使用IP地址，而不通过域名服务器。
-N或--netlink或--symbolic 显示网络硬件外围设备的符号连接名称。
-o或--timers 显示计时器。
-p或--programs 显示正在使用Socket的程序识别码和程序名称。
-r或--route 显示Routing Table。
-s或--statistics 显示网络工作信息统计表。
-t或--tcp 显示TCP传输协议的连线状况。
-u或--udp 显示UDP传输协议的连线状况。
-v或--verbose 显示指令执行过程。
-V或--version 显示版本信息。
-w或--raw 显示RAW传输协议的连线状况。
-x或--unix 此参数的效果和指定"-A unix"参数相同。
--ip或--inet 此参数的效果和指定"-A inet"参数相同。
```



### 搭建第二个中间件Mysql

#### mysql安装

创建专用用户（降权）

```
useradd mysql -s /sbin/nologin/ -M 
nologin ：表示不能访问linux 系统
/sbin/nologin/ 表示不登录
-M ：表示不能创建主目录

cat /etc/passwd :检查是否创建成功
userdel -r 用户名
```

```
解压：
tar -xzf mysql-5.6.35-linux-glibc2.5-x86_64.tar.gz -C /data/server
-x:表示解压
-z：表示通过gzip压缩来进行解压
-f:表示一个文件
-C：表示解压到指定目录中
软链接：
ln -s mysql-5.6.35-linux-glibc2.5-x86_64 mysql
-s：表示进行软链接
```

```
初始化mysql数据库
/data/server/mysql/scripts/mysql_install_db --basedir=/data/server/mysql --datadir=/data/server/mysql/data/ --user=mysql
 
basedir 安装软件的路径
datadir 安装数据的路径
user = mysql 指定用户名为mysql

```

```
数据库配置文件管理
mv /etc/my.cnf /etc/my.cnf-bak   #改名

cp /data/server/mysql/support-files/my-default.cnf /etc/my.cnf
```

```
数据库启动命令配置
cp /data/server/mysql/support-files/mysql.server /etc/init.d/mysqld 
chmod +x /etc/init.d/mysqld
```

```
修改启动命令
sed -i 's#nihao#hello#g' 1.txt  #将1.txt文件中的nihao替换成hell
s 代表替换 
g 代表全部

sed -i 's#/usr/local/mysql#/data/server/mysql#g' /data/server/mysql/bin/mysqld_safe /etc/init.d/mysqld

```

```
数据文件权限设置
chown -R mysql.mysql /data/server/mysql/
-R 递归修改目录
```

```
将MySQL服务设置会开机自启动选项
chkconfig --add mysqld
chkconfig mysqld on
```

```
netstat -tnulp | grep mysql  检查软件是否在运行
```



#### mysql服务端操作

启动数据库

```
service mysqld start
```

停止数据库

```
service mysqld stop
```

重启数据库

```
service mysqld restart
```

