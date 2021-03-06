﻿第一部分安装

**1. 下载地址:**  

https://git-scm.com/download/win

如果速度慢, 使用 迅雷下载;

**2. 点击安装, 然后下一步, 直到下面这个页面:**

![1](\Git使用\Git附件图片\1.jpg)

建议: 按照上面所示方式选中复选框 ;

**3.  点击下一步, 直到出现这个页面:**

![2](\Git使用\Git附件图片\2.jpg)

建议: 这个页面是选择git使用的命令行, 建议使用第一个git自带的;

**4. 点击下一步, 直到出现下面这个页面:**

![3](\Git使用\Git附件图片\3.jpg)

建议: 这个是选择行结束符, windows与linux行结束符不一致; 建议选择第一个, 这样git会自动转换;

**5. 点击下一步, 直到出现下面这个页面:**

![4](\Git使用\Git附件图片\4.jpg)

建议: 选择命名行窗口, 建议第一个;

**6. 点击下一步, 直到出现下面这个页面:**

![5](\Git使用\Git附件图片\5.jpg)

建议: 是否开启文件缓存, 选第一个; 点击install;

**7. 安装成功后: 击桌面上的git快捷方式打开命名行, 运行git命名, 出现如下界面则成功:**

![6](\Git使用\Git附件图片\6.jpg)

### 第二部分: windows配置git SSH服务

**1. 生成SSH秘钥对:**

命名行运行 : ssh-keygen -t rsa -C "你的邮箱地址";

![7](\Git使用\Git附件图片\7.jpg)

**2. 输入你的秘钥密码:**

![7-1](\Git使用\Git附件图片\7-1.jpg)

**3. 找到这个文件:用记事本打开, 然后复制内容**

![8](\Git使用\Git附件图片\8.jpg)

**4. 进入git, 从这里打开信息设置页面: 在这里添加生成的秘钥;**

![9](\Git使用\Git附件图片\9.jpg)

![10](\Git使用\Git附件图片\10.jpg)

![11](\Git使用\Git附件图片\11.jpg)

![12](\Git使用\Git附件图片\12.png)

### 第三部分: 配置全局用户名和邮箱

**1.命令行运行以下指令:**

git config --global user.name  "你的用户名"

git config --global user.email "你的邮箱"

![13](\Git使用\Git附件图片\13.jpg)

### 第四部分: IDEA配置

**1. 配置git路径**

![14](\Git使用\Git附件图片\14.jpg)

**2.新建一个项目: TestGit,   src下创建一个HelloWorld.java文件,**  

项目路径:C:\Users\Administrator\Desktop\code\TestGit

![15](\Git使用\Git附件图片\15.jpg)

**3. 打开github, 新建仓库TestGit;**

![16](\Git使用\Git附件图片\16.jpg)

**2. 打开项目所在文件夹, 在文件夹上右键运行: git bash here**

![17](\Git使用\Git附件图片\17.jpg)

**3. 命名行依次运行以下命名:**

```
git init

git add src

git commit -m  "first commit"

git remote add origin https://github.com/mw138/TestGit.git

git push  -u origin master
```

**4. 如果不出错误提示输入用户名, 密码:**

![18](\Git使用\Git附件图片\18.png)

**5. 输入用户名密码后,开始提交,出现下面提示则成功**

![19](\Git使用\Git附件图片\19.jpg)

**6. 打开github验证: 可以看出确实提交上去了**

![20](\Git使用\Git附件图片\20.jpg)

**7. 至此, 该项目已经加入到了github的版本控制,  在idea上可以进行提交和更新了;**

**新建一个Test文件, 然后提交到版本库,  步骤如下:**

 

![21](\Git使用\Git附件图片\21.jpg)

 

![22](\Git使用\Git附件图片\22.jpg)

![23](\Git使用\Git附件图片\23.jpg)

**idea上: vcs --> git --> push**

![24](\Git使用\Git附件图片\24.jpg)

![25](\Git使用\Git附件图片\25.jpg)

![26](\Git使用\Git附件图片\26.jpg)

![27](\Git使用\Git附件图片\27.jpg)

**注意事项:**

1.如果第一次使用git, idea会提示输入github用户名, 密码;

2.如果出现提示 提示没有本地分支, 运行以下命名:

git branch --set-upstream master origin/master