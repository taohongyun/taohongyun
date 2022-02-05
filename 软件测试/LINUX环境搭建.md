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

