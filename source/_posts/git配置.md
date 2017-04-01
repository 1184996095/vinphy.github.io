title: git配置
date: 2016-06-28 18:44:12
updated	: 2016-06-28 18:44:12
permalink: 技术铛
tags:
- git
- github
- 版本管理
categories:
- 技术档

---


跟着笔者魔鬼般的步伐，我们一起来瞅瞅一个团队协作的任务如何进行版本管理吧~

要跟上哦~

===============================================

首先我们先来看下git进行版本管理的大概流程：



好啦，心里大概有个底了吧，现在开始正式操作了哟~

（一）前期准备

1.申请一个github账号：

　　访问https://github.com/，进入如图页面：



注册一个属于自己的github账号。

2.安装git：

　　安装指南：http://note.youdao.com/share/?id=f0b3422cf19db7c0dcc31de16f2653cc&type=note

3.安装开发工具IntelliJ IDEA（当然啦，可以根据自己的喜好安装不同的开发工具）:

　　安装指南：http://note.youdao.com/share/?id=89349b4e4f6f57ae603c2c43bad1bb62&type=note

4.github与本地电脑的关联 && 本地gitbash配置全局用户名等信息：

　-在安装好之后，电脑桌面会生成gitbash的快捷方式，我们将其打开，会进入到如下界面：

  

　　-现在我们先在GitBash上将一些前期的准备工作做好。

　　--首先，开启快速编辑模式（这样才可以右击鼠标粘贴，不开启的话粘贴功能不能用的哟）：在Git Bash任务栏右击，点击下拉菜单中“属性”按钮，出现如下界面，勾选 “快速编辑模式”：

  

　设置好了，现在我们可以开始愉快的进行git操作了。

　--先建立本地电脑与github的联系(为github账号加入SSH Key)：

　　->创建SSH Key：

　　首先到用户主目录（一般是C:\Users\admin）下，看看有没有.ssh文件夹。

　　如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件；

　　有的话，可直接跳到下一步；

　　如果没有，打开Git Bash，在命令行输入以下命令，然后回车。

$ ssh-keygen -t rsa -C "你注册github的邮箱"
　这时用户主目录下就会生成.ssh的文件夹，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人：
　　->给github账号配置SSH秘钥：

　　登陆GitHub，打开“Account settings”，点击左侧“SSH Keys”按钮，再点击右侧“Add SSH Key”，在输入框中填一个自己中意的Title，在Key文本框里粘贴id_rsa.pub文件的内容：

github-addkey-1    github-addkey-2

　　--然后我们在本地配置全局的用户名等信息，这样进行git操作时，你的身份才是可以识别的：

　　　->在Git Bash命令行中键入如下命令：

1.git config user.name "用户名"
2.git config user.email "邮箱"
3.git config color.ui true //可选，设置Git Bash字体有颜色差异
　　

（二）操作

　　1.本地已有代码

　　->在Git Bash命令行用“cd”命令进入你存放代码的文件夹;

　　->git init 命令初始化本地仓库。你的代码存放文件夹下会出现如图所示的".git"文件夹。



　　2.本地无代码，直接去远程库上克隆项目

　　-访问团队项目远程仓库地址（此演示为当地址需访问别人项目得到的情况，如果有地址时，只需在登陆自己github账号的同时打开该地址）

　　->登录你的github账号,在搜索框中输入你要查找的项目名或用户名。在跳转后的页面点击Code或Users，出现要搜索的结果后，点击进入。

   

　　->在所访问用户的主页中找到你想要的项目。

     

　　将项目fork一份到自己的github仓库中。如下图所示,fork之前，地址栏访问的是别人的github仓库;fork之后地址栏跳转到自己的github仓库地址，fork后面的数字会+1.这时就将项目文件拷贝了一份到自己的远程仓库。复制自己的远程仓库地址（如果github上没有绑定SSH秘钥，请复制https路径，不要复制SSH路径）。

    

　　-将远程仓库的项目迁到本地仓库中（下面演示的是图形化界面，git命令见开头流程图）

　　打开IDEA，在菜单栏找到“VCS”，下拉菜单中悬停“Chenckout from Version Control”,点击“GitHub”。如下图所示：

  

　　会出现如下界面，输入你的github账号密码。



　　然后在接下来的页面设置你的操作密码；在如下页面的Git Repository URL输入刚刚复制的项目地址（自己的远程仓库），点击clone。就可以将远程仓库的项目迁下来。



-对项目进行修改
-将本地仓库修改后的代码迁移到远程仓库中
首先，为了方便团队协作，我们在本地checkout一个本地分支。
如图，在IDEA的右下角，我们选择新建一个分支。我新建了一个名为“develop”的分支，如下图所示：
   

　接下来我们就在改分支编写代码啦。

　修改完之后，我们就要将本地仓库的代码提交到远程服务器上面了。

　如下图所示，在IDEA左侧项目名上面，我们点击万能的右键，选择“Git”子菜单中的“Commit Directory”；在弹出窗口中填写提交信息，然后点击“Commit and Push”；在接下来的弹出框中“Commit”“Push”。这是代码就提交到远程仓库的“develop”分支了。

   

（三）远程

　-在远程仓库中贡献代码

　　进入你的github页面，会显示如下的提交信息。点击“Compare & pull request”进行合并，切换到develop分支可以看到刚刚提交的代码了。

  

　　-现在我们找到亮眼的“New pull request”按钮进行点击。会跳转如右下所示页面。左边选择你自己的分支，右边选你要与之对比合并的团队项目远程分支，确认就可以了。

  

 