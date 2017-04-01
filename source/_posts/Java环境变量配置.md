title: java 环境配置
date: 2016-06-28 18:44:12
updated	: 2016-06-28 18:44:12
permalink: 技术铛
tags:
- java 环境配置
- Java
- 环境配置
categories:
- 技术档

---
不管是编程还是用一些软件，都可能需要配置Java环境变量，今天我们一起来配置一下这个名为Java的环境变量吧。  
## 安装Java
进入[Java主页](http://www.java.com/zh_CN/)，点击`免费Java下载`，并安装到C盘根目录下；  
## 配置
进入到`系统属性`界面，点击左侧边栏的`高级系统设置`，出现系统属性的弹出窗口。  
![系统属性界面](http://i.imgur.com/89KiIFG.png)  
![系统属性弹出窗口](http://i.imgur.com/WOSmGSY.png)
选择`环境变量`，在环境变量弹出窗口下边`系统变量`下拉框中,    
![环境变量弹出窗口](http://i.imgur.com/6xAdlWD.png)
- 点击`新建`，变量名为“JAVA_HOME”，变量值复制安装的java路径，本人此次安装路几个为`C:\java\bin`;
- 选择Path，双击，在弹出框口中输入`%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;`
- 新建一个名为`CLASSPATH`的系统变量，变量值为`.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;`  
## 验证
现在Java配置配好了，如何验证Java是否配置成功呢？  
- 到`开始`菜单中输入`cmd`命令，将会出来dos命令窗口；
- 输入`JAVAC`或者	`java -version`，出现帮助信息或者版本系你想则证明Java配置成功。