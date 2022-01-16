### find查找文件/目录

```
find + 文件/目录名
```

### cd （change directory） 切换目录

```
cd  # 切换到root根目录
cd /   # 切换到系统根目录
cd ,,/  # 切换到上一层目录
```

### ls/dir  （list） 列出目录下文件

``` 
ls -a (all) #列出所有文件
ls -d (directory) #列出目录
ls -i (inode)  #显示每个文件的inode号（索引节点号，可以理解文件的储存地址）
ls -l (long)  # 较长格式列出
ls -lh (human-readable) 与-l# 人性化阅读输出
```

### clear 清屏

```
clear  #清除屏幕内容
```

### pwd 显示路径

```
pwd (print work directory) #显示当前所在路径
```

## mv(move) 移动或者更改现有文件或者目录

```
mv -b (backup)+ 目标文件或者路径 #移动到目标目录，若覆盖文件则先备份
mv -f (force) + 目标文件或者路径 #强制覆盖，没有文件时相当于备份
mv -i (interactive) + 目标文件或者路径 #覆盖前进行询问
mv -u (update) + 目标文件或者路径 #在移动或者更改文件名时，若目标文件已经存在，且其文件日期比源文件新，则不覆盖目标文件
```

### rm(remove) 删除文件或者目录

```
rm -d (directory) # 直接把想要删除的目录的硬连接数据删成0，删除该目录
rm -f (froce)  # 强制删除文件或者目录
rm -i (interactive)  #删除既有文件或者目录之前先询问用户
rm -r/-R (recursive)  #递归删除，防止目录里有文件不能删除
```

### mkdir (make directories)  建立目录(文件夹)

```
mkdir + 文件名 #创建文件夹
mkdir -p 文件夹1/文件夹2/文件夹3 #批量创建多层文件夹
mkdir -p {文件夹1，文件夹2，文件夹3}/文件夹4  #批量创建多个多层文件夹
mkdir -v  #创建目录并显示详细信息
```

### rmdir 删除空文件夹/目录

```
rmdir + 目录名   #删除目录，注意必须时空目录
rmdir + -p 目录名/目录名/目录名  #删除指定目录及其上级文件夹

```

###  echo 显示一行文本，可使用通配符，正则表达式

```
echo + 文本内容  #显示文本
echo + -n + 文本信息  #显示不带尾部回车符的文本
echo + -e “文本信息”  #允许使用转义字符输出文本
echo + 新文本内容>文件名  #重定向，清除源文件所有内容，并插入单行
echo + 新文本内容>>文件名  #追加重定向，在原有的基础上末尾插入一行文本
```

### ifconfig/ip addr(centOS) 显示或者设置网络设备（查看ip）

```
ifconfig  #处于激活状态的网络接口
ifconfig -a  #所有配置的网络接口，不论其是否激活
```

### ping检测主机，（127.0.0.1为主机，可以检验网卡，用于检测内网）

```
ping （-c 次数）  127.0.0.1  # ping主机，不设置次数则为ping无限次，按p或者ctrl c 停止
ping （-c 次数） ip    #ping ip
```

### date 显示系统时间

```
date   #显示打印的时间
date -s 时间   #设置时间 例如 date -s '12:01:01'
date %m%d%H%M%S  #按照格式输出时间
```

### su 切换用户

```
su 用户名   #切换到用户名
sudo 命令   #在root用户下执行一条命令
sudo su    #下面的命令都由su用户执行
su root    #CentOS下切换root用户的一种方式
```



```
cp -i 文件名 位置   #交互式复制，在覆盖目标文件之前将给出提示要求用户确认
cp -f 文件名 位置   #覆盖已存在的目标文件而不提示
cp -r 文件名 位置   #复制的是一个文件夹，包括文件夹下的素有文件夹和文件
cp -v 文件名 位置   #显示拷贝进度
```

###  cat 查看文件内容

```
cat 目标文件  #普通输出
cat -n 目标文件  #开头显示行号
cat -E 目标文件  #以$结束
cat -ns 目标文件  #去空行，夹行号
tac  目标文件   #反向查看文件内容
```

### touch 创建文件

```
touch 文件名    #将文件改成当前时间，文件不存在则新建
touch -c -t 时间 文件名   #将档案时间改为特定时间  例：touch -c -t 05061803 123.txt（将档案时间改为,5月6日18点3分）
touch -r 参考文件名 目标文件名  #将目标文件档案改成跟参考文件一样 例： touch -r abc.txt 123.txt（将123.txt档案改成跟abc.txt一样）
touch -d 时间 文件名 #将文件日期改为特定天数时间  例：touch -d "2 days ago" 123.txt   将123.txt日期修改为2天以前 

```

### man查看帮助文档

```
man 命令  # 查看命令的帮助文档
```

### history 查看用户历史操作

```
history    #查看所有执行过的命令
history n   # 查看n条历史记录
!n       #执行编号为n的命令，注意是感叹号，例：!3  执行编号为3的命令
history -c    #清除历史记录
```

### id /who 查看用户

```
id/who   #显示当前用户信息
id 用户名  #显示用户名的信息
who -a   #显示目前登入系统的用户详细信息
who -b   #上次系统启动时间
```

### sleep 休眠

```
sleep n;命令   #n秒后，执行某命令,注意分号
```

### shutdown/poweroff/halt 关机/重启命令

```
shutdown -h now或/poweroff或halt    #立刻关机
shutdown -h 时间                    #在指定的时间关机
shutdown -H now                    #立即停机
shutdown -r now 或者reboot          #重启
```

### diff 比较两个文件/文件夹之间的差异

```
diff 文件1 文件2       #比较文件1和文件2之间的差异
diff 文件夹1/文件夹2/   #比较文件夹1和文件夹2的差异
diff -r 文件夹1/文件夹2/  #利用递归的方式比较两个文件夹之间的差异
```

### apt-get 对软件包的操作命令

```
apt-get install 软件/包   #安装包
apt-get update 软件/包    #更新软件
apt-get remove 软件/包    #卸载软件
apt-get upgarde 软件/包   #更新已安装的包
apt-get clean 软件/包     #清除无用的包
```

### SSH

```
ssh 用户@ip地址  #远程ssh连接某主机 
```

### useradd添加用户

```
useradd 用户名   #添加某用户
用户名 passwd    #添加密码
useradd -r 用户名           #添加系统用户
useradd -d 路径 用户名       #添加用户，并且指定，home目录 
```

### tail -f 滚动查看日志

```
tail -f tet 滚动查看名字为tet的文档内容，不进入编辑界面
tail -f 1000 tet 滚动查看最后1000行文档内容
```

