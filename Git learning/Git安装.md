## 一.Git安装

windows安装：进入网站http://git-scm.com/下载安装，然后再cmd命令行配置

```shell
git config --global user.name "xxxxx"
git config --global user.email "xxxxx@xxx.com"
git config --list  
```

linux安装：

```shell
[root@centos ~]# yum -y install git
[root@centos ~]# git --version            //初始化版本库
[root@centos ~]# git init /var/git --bare
```

## 二.理论基础

![](D:\Gitproject\Git学习\Git.assets\image-20220125211818304.png)

如果每个版本中有文件发生变动，Git 会将整个文件复制并保存起来。这种设计看似会多消耗更多的空间，但在分支管理时却是带来了很多的益处和利。

你的本地仓库有 Git 维护的三棵“树”组成，这是 Git 的核心框架。这三棵树分别是：**工作区域、暂存区域和 Git 仓库**

![image-20220125211853932](D:\Gitproject\Git学习\Git.assets\image-20220125211853932.png)

工作区域（Working Directory）就是你平时存放项目代码的地方

暂存区域（Stage）用于临时存放你的改动，事实上它只是一个文件，保存即将提交的文件列表信息

Git 仓库（Repository）就是安全存放数据的位置，这里边有你提交的所有版本的数据。其中，HEAD 指向最新放入仓库的版本（这第三棵树，确切的说，应该是 Git 仓库中 HEAD 指向的版本）

Git的工作流程一般是：

1.在工作目录中添加，修改文件

2.将需要进行版本管理的文件放入暂存区域

3.将暂存区域的文件提交到 Git 仓库

Git 管理的文件有三种状态：已修改（modified）、已暂存（staged）和已提交（committed），依次对应上边的每一个流程

## 三.Git使用实战

### 1.初始化Git

在自己电脑盘中新建一个文件夹，使用Gitproject为例，在windows的Terminal进行操作：

```shell
C:\Users\xxx> cd D:              //进入文件夹所在的盘符
D:\> cd .\Gitproject\
D:\Gitproject> git init            //初始化Git项目
Initialized empty Git repository in D:/Gitproject/.git/
//在文件夹MyProject中添加一个文本文件README.md
D:\Gitproject>  git add README.md  //将文件加入暂存区
D:\Gitproject> git commit -m "add a test file"
//将文件提交到git仓库（-m表示添加本次提交的说明）
[master 08d772c] add a test file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
```

将GItHub上别人的代码作用到本地：

```shell
D:\>Gitproject>git clone 目标
```

