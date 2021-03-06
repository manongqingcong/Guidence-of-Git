﻿### Linux系统下Git使用教程

##### 一、初始化

1、首先安装git软件，安装环境是centos 7.x下的云服务器。使用命令:

```
#yum install git
```

2、设置用户名和邮箱（必须）：

```
# git config --global user.name "Your Name"
# git config --global user.email "email@example.com"
```

3、创建一个版本库,选择一个合适的地方，创建一个空目录：

```
# mkdir learngit    #在服务器中创建learngit文件夹
# cd learngit     #进入learngit 文件夹
# pwd     #显示当前工作路径
```

结果：（使用root用户权限）

```
/root/learngit
```

4、初始化这个目录为git可以管理的仓库，使用命令：

```
# git init

Initialized empty Git repository in /root/learngit/.git/
```

已经成功初始化git仓库，并且是空的，路径在/root/learngit/,这个目录就是git可以管理的仓库。

5、把文件添加到git仓库

```
#vi  read.txt  #创建一个文本文件
# i  "hello ,world"    # 编辑文件内容
# :x        #保存并退出
```

第一步   使用命令 `git add `告诉git，把文件添加到仓库：

```
# git add read.txt
```

第二步  用命令`git commit`告诉git，把文件提交到仓库：

```
# git commit -m "wrote a read file"
```

说明： `git commit`命令，`-m `后面是本次提交的说明，是对提交更改的内容的说明，方便以后很快的查找版本更新的内容。

`git commit `命令执行成功后，会告诉你，1个文件被改动，插入了1行内容（read.txt有1行内容）。

为什么Git添加文件需要`add`，`commit`一共两步呢？因为`commit`可以一次提交很多文件，所以你可以多次`add`不同的文件，比如：

```
# git add file1.txt
# git add file2.txt file3.txt
# git commit -m "add 3 files."
```

#####  二、更新文件内容

1、继续更新文件内容

```
#vi read.txt
#hello world #第二行添加hello ，world
#：x  
```

2、查看文件现在状态

```
#git status
```

![l1](F:\Git使用\Git附件图片\l1.png)

可以看到，文件已经修改，但是还没有提交。

3、查看更改的内容，使用命令：

```
#git diff read.txt
```

![l2](\Git使用\Git附件图片\l2.png)

可以看见更改的内容，增加了一行内容。

4、再次提交版本

```
#git add read.txt
```

此时的状态 ：git status

![l3](\Git使用\Git附件图片\l3.png)

提交：

```
#git commit -m "add hello world"
```

![l4](\Git使用\Git附件图片\l4.png)

