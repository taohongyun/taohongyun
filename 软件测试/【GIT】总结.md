## 版本控制

### 作用

> 实现跨区域多人协同合作
>
> 追踪一个或多个文件的历史纪录
>
> 组织和保护你的源代码和文档
>
> 统计工作量
>
> 并行开发 提高开发效率
>
> 跟踪记录整个软件的开发过程
>
> 减轻开发人员的负担 节省时间 同时降低人为错误

（简单来说就是用于管理多人协同开发项目的技术）

### 主流版本控制器

Git、Svn、Cvs、Vss、Tfs



### 版本控制分类

本地版本控制

集中版本服务器svn

分布式版本控制git



### Git和Svn的区别

**Svn**是集中式的版本控制系统，版本库是集中放在中央服务器的，而工作，用的都是自己的电脑，所以首先要从中央服务器得到最新版本，然后工作，完成工作后，需要把自己做完的活推送到中央服务器，集中式版本控制系统时必须要联网才能工作，对网络带宽要求比较高。

**Git**是分布式的版本控制系统，没有中央服务器，每个人电脑就是一个完整的版本库，工作的时候不需要联网了因为版本都在自己的电脑上。可以直接看到已更新的代码和文件。

 

http://npm.taobao.org?mirrors?git-for-windows/ 镜像下载



### 基本命令

**Cd** 改变目录

**Cd ..** 回退到上一目录，直接cd进入牧人目录

**Pwd** 显示当前所在的目录路径

**Ls****（ll****）**都是列举当前目录的所有文件，ll列举的更为详细。

**Touch** 新建一个文件

**Rm** 删除一个文件

**Mkdir** 新建一个文件夹

**Rm-r** 删除一文件夹 rm-r src 删除src目录

**Mv** 移动文件

**Reset** 重新初始化清屏

**Clear** 清屏

**History** 查看命令历史

**Help** 帮助

**Exit** 退出

**#** 注释



### Git配置

查看配置 git config –l  查看系统配置 git config—system –list

设置用户名

Git config –global user.name taohongyun

Git config –global user.email taohongyun0609.com



### GIt的一般工作流程

在工作目录里添加修改文件

将需要版本管理的文件放入暂存区域 git add.

将暂存区域的文件提交到git仓库 git commit

 

### Git项目搭建

Git Init 初始化项目

Git clone 克隆

Git status 查看全部命令

Git status [filename]

Git add . 添加到暂存区里边

Git commit –m “new file hello.txt”

 

git clone https://github.com/taohongyun/-

从github往本地克隆



### Git分支中常用信令

列出所有本地分支 git branch

列出所有远程分支 git branch –r

新建一个分支 git branch [branch-name]

新建一个分支，并切换到该分支 git checkout –b [branch]

合并指定分支到当前分支 $ git branch –d [branch-name]

删除分支 $ git branch –d [branch-name] 

删除远程分支 $ git puch origin –delete [branch-name] $ git branch –dr [remote/branch]

 

###  一般工作流程

git remote add origin  网址     先做连接

git pull --rebase origin master     把远程已有的下载下来

git push -u origin master     工作结束把本地的一起上传上去

 





git checkout -b 新建的分支名字

git clone 克隆

git add 文件名

git commit -m "属性"

git push origin 上传到远程

git merge 文件名  （当前分支必须要是被合并到的分支）

git checkout 分支名  切换到那个分支

git diff 文件名 另一个文件名 查看两个文件的不同

git branch 查看所有本地分支

git branch -r 查看所有远程分支

git branch -d 分支名 删除本地分支

git push origin --delete 分支名 删除远程分支
