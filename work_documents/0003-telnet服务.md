# 0003-telnet服务

OK，终于展开这一话题了。

没错前面做的这些工作都是为了在此服务，而之所以有这个话题的产生则源自于笔者在工作场景中遇到的一个麻烦。

![image-20221012193302767](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221012193302767.png)

客户直接发了一个操作，说在命令行输入这个可以使用`AT`指令，而平常笔者工作使用的AT指令都是在`SSCOM`这类软件里进行的。

![image-20221012193421187](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221012193421187.png)

最关键的是客户说`telnet`可以在控制台窗口输入，而根据笔者以往的工作经验，我立马想到了`adb和fastboot`。adb笔者暂时用的较少，但是`fastboot`经常被我用来对高通平台进行强制刷机。

![image-20221012193645119](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221012193645119.png)

而像`fastboot`和`adb`这样的程序怎样使用呢？一般都是将该文件解压，之后在环境变量里添加一个该文件夹即可直接在命令行调用该程序。

所以我一直想`telnet`是什么程序，but问了好几个人都没告诉我怎么搞。

突然灵机一动，百度了一下，原来`telnet`是一个`windows的服务`。可以先在控制台点击程序，进入界面。

![image-20221012193930299](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221012193930299.png)

点击启动或关闭Windows功能

![image-20221012194019265](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221012194019265.png)

选择Telnet客户端，即可在终端使用`telnet xxx.xxx.xxx.xxx`命令

![image-20221012194115499](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221012194115499.png)