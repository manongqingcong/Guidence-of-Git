﻿### Git的使用流程

参考地址：https://www.cnblogs.com/best/p/7474442.html（包括视频）

参考地址：https://www.cnblogs.com/chenwolong/p/GIT.html

##### 一、Git的安装

```Git
1、 官网下载安装包： https://git-scm.com/（下载git对应操作系统的版本）

2、 Windows系统使用执行程序默认安装或者Linux系统解压进行命令安装
    
    Windows安装：双击执行程序‘下一步’，执行安装

    Linux安装Git：sudo apt-get install git 命令行就可以安装了。

    Mac OS安装Git： https://git-scm.com/download/mac，下载双击.pkg安装
3、 Bash基本操作命令
    1）、cd : 改变目录。
    2）、cd . . 回退到上一个目录，直接cd进入默认目录
    3）、pwd : 显示当前所在的目录路径。
    4）、ls(ll): 都是列出当前目录中的所有文件，只不过ll(两个ll)列出的内容更为详            细。
    5）、touch : 新建一个文件 如 touch index.js 就会在当前目录下新建一个                index.js文件。
    6）、rm: 删除一个文件, rm index.js 就会把index.js文件删除。
    7）、mkdir: 新建一个目录,就是新建一个文件夹。
    8）、rm -r : 删除一个文件夹, rm -r src 删除src目录， 好像不能用通配符。
    9）、mv 移动文件, mv index.html src index.html 是我们要移动的文件, src 是          目标文件夹,当然, 这样写,必须保证文件和目标文件夹在同一目录下。
    10）、reset 重新初始化终端/清屏。
    11）、clear 清屏。
    12）、history 查看命令历史。
    13）、help 帮助。
    14）、exit 退出。
    15）、#表示注释
    16）、echo文件内写入内容：echo hello > index.html
```

##### 二、Git配置查看

```Git
1、 使用git config -l 可以查看现在的git环境详细配置

2、 查看不同级别的配置文件：
    
    #查看系统config
    git config --system --list

    #查看当前用户（global）配置
    git config --global  --list

    #查看当前仓库配置信息
    git config --local  --list
```

##### 三、设置用户名与邮箱（用户标识，必要）

```Git
1、 当你安装Git后首先要做的事情是设置你的用户名称和e-mail地址。这是非常重要的，因为每次Git提交都会使用该信息。它被永远的嵌入到了你的提交中：

 　　$ git config --global user.name "zhangguo"  #名称
 　　$ git config --global user.email zhangguo@qq.com   #邮箱
 　　
2、只需要做一次这个设置，如果你传递了--global 选项，因为Git将总是会使用该信息来处理你在系统中所做的一切操作。如果你希望在一个特定的项目中使用不同的名称或e-mail地址，你可以在该项目中运行该命令而不要--global选项。 总之--global为全局配置，不加为某个项目的特定配置。
```

##### 四、创建本地仓库的方法有两种：一种是创建全新的仓库，另一种是克隆远程仓库。

```Git
1、创建全新仓库
需要用GIT管理的项目的根目录执行：
# 在当前目录新建一个Git代码库
$ git init

当然如果使用如下命令，可以把创建目录与仓库一起完成：
# 新建一个目录，将其初始化为Git代码库
$ git init [project-name]

2、克隆远程仓库
 另一种方式是克隆远程目录，由于是将远程服务器上的仓库完全镜像一份至本地，而不是取某一个特定版本，所以用clone而不是checkout，语法格式如下：

# 克隆一个项目和它的整个代码历史(版本信息)
$ git clone [url]
```

##### 五、查看文件状态

```Git
1、文件4种状态
Untracked: 未跟踪, 此文件在文件夹中, 但并没有加入到git库, 不参与版本控制. 通过git add 状态变为Staged.

Unmodify: 文件已经入库, 未修改, 即版本库中的文件快照内容与文件夹中完全一致. 这种类型的文件有两种去处, 如果它被修改, 而变为Modified. 如果使用git rm移出版本库, 则成为Untracked文件

Modified: 文件已修改, 仅仅是修改, 并没有进行其他的操作. 这个文件也有两个去处, 通过git add可进入暂存staged状态, 使用git checkout 则丢弃修改过, 返回到unmodify状态, 这个git checkout即从库中取出文件, 覆盖当前修改

Staged: 暂存状态. 执行git commit则将修改同步到库中, 这时库中的文件和本地文件又变为一致, 文件为Unmodify状态. 执行git reset HEAD filename取消暂存, 文件状态为Modified

2、查看文件状态
#查看指定文件状态
$ git status [filename]

#查看所有文件状态
$ git status

#创建文件测试
$ git touch index.html
$ git echo hello > index.html
```

##### 六、将untracked状态的文件添加到暂存区

```
语法格式如下：
# 添加指定文件到暂存区
$ git add [file1] [file2] ...

# 添加指定目录到暂存区，包括子目录
$ git add [dir]

# 添加当前目录的所有文件到暂存区
$ git add .
```

##### 七、移除文件与目录（撤销add）

```
#直接从暂存区删除文件，工作区则不做出改变
git rm --cached <file>

#如果已经用add 命令把文件加入stage了，就先需要从stage中撤销
git reset HEAD <file>...

#移除所有未跟踪文件
#一般会加上参数-df，-d表示包含目录，-f表示强制清除。
git clean [options] 

#只从stage中删除，保留物理文件
git rm --cached readme.txt 

#不但从stage中删除，同时删除物理文件
git rm readme.txt 

#把a.txt改名为b.txt
git mv a.txt b.txt 
```

##### 八、查看文件修改后的差异

```
git diff用于显示WorkSpace中的文件和暂存区文件的差异

用"git status"只能查看对哪些文件做了改动，如果要看改动了什么，可以用：

#查看文件修改后的差异
git diff [files]

#比较暂存区的文件与之前已经提交过的文件
git diff --cached

也可以把WorkSpace中的状态和repo中的状态进行diff，命令如下:
#比较repo与工作空间中的文件差异
git diff HEAD~n
```

##### 九、提交

```Git
通过add只是将文件或目录添加到了index暂存区，使用commit可以实现将暂存区的文件提交到本地仓库。
# 提交暂存区到仓库区
$ git commit -m [message]

# 提交暂存区的指定文件到仓库区
$ git commit [file1] [file2] ... -m [message]

# 提交工作区自上次commit之后的变化，直接到仓库区，跳过了add,对新文件无效
$ git commit -a

# 提交时显示所有diff信息
$ git commit -v

# 使用一次新的commit，替代上一次提交
# 如果代码没有任何新变化，则用来改写上一次commit的提交信息
$ git commit --amend -m [message]

# 重做上一次commit，并包括指定文件的新变化
$ git commit --amend [file1] [file2] ...


修订提交

如果我们提交过后发现有个文件改错了，或者只是想修改提交说明，这时可以对相应文件做出修改，将修改过的文件通过"git add"添加到暂存区，然后执行以下命令：

#修订提交
git commit --amend
撤销提交（commit）

原理就是放弃工作区和index的改动，同时HEAD指针指向前一个commit对象

#撤销上一次的提交
git reset --hard HEAD~1

撤销提交
git revert <commit-id>
这条命令会把指定的提交的所有修改回滚，并同时生成一个新的提交。
```

##### 十、提交到远程仓库

```Git
#添加远程主机，主机名为origin 地址为https://git.coding.net/zhangguoGit/project7.git

git remote add origin https://git.coding.net/zhangguoGit/project7.git

#本地的master分支推送到origin主机，同时指定origin为默认主机，后面就可以不加任何参数使用git push了，-u 参数指定一个默认主机

git push -u origin master

#远程git仓库缓存 -推(更新/提交)
git push --all

# 上传本地指定分支到远程仓库
$ git push [remote] [branch]

# 强行推送当前分支到远程仓库，即使有冲突
$ git push [remote] --force

# 推送所有分支到远程仓库
$ git push [remote] --all

#上传数据，如git push origin master
git push [remote-name] [branch]
```

##### 十一、远程仓库操作

```Git
# 下载远程仓库的所有变动
$ git fetch [remote]

# 显示所有远程仓库
$ git remote -v

# 显示某个远程仓库的信息
$ git remote show [remote]

# 增加一个新的远程仓库，并命名
$ git remote add [shortname] [url]

#简单查看远程---所有仓库
git remote  （只能查看远程仓库的名字）
#查看单个仓库
git  remote show [remote-branch-name]

#新建远程仓库
git remote add [branchname]  [url]

#修改远程仓库
git remote rename [oldname] [newname]

#删除远程仓库
git remote rm [remote-name]

#获取远程仓库数据
git fetch [remote-name] (获取仓库所有更新，但不自动合并当前分支)
git pull (获取仓库所有更新，并自动合并到当前分支)
```