# VSCode配置远程ssh免密登录

## 引言

经历过远程开发的人都知道VSCode的**VS Code Remote**是一个非常好用的插件，这个插件使得开发者可以在容器，物理或虚拟机，以及 Windows Subsystem for Linux (WSL) 中实现无缝的远程开发。

而在此之前的远程开发呢，比如我的导师，一个资历较老的开发人员了。他进行远程开发的方式是通过在本地Source Insight阅读和修改代码，然后通过samba管理服务器的文件，再通过将修改的文件与远程服务器上的文件进行替换的方式，实现远程代码编写。这个方式相较来说效率已经颇低了。

下面我引用一篇别人写的安装设置remote-ssh的博客（以分割线来进行划分），来略过重复的这一部分讲解，本篇只着重对免密这一部分进行探讨。

这是原博客：[vscode设置remote-ssh并免密登录](https://blog.csdn.net/weixin_42397613/article/details/114983147)

## 设置remote博客引用

------

1. **在vscode中安装remote-ssh插件**
  直接在vscode中搜索remote-ssh即可安装

  ![在这里插入图片描述](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/20210318162150567.png)

​		安装完成以后是这样：

![在这里插入图片描述](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/20210318162305788.png)


2. **使用remote-ssh远程登录ssh**
  按照下图标记依次点击1、2、3，就会出现remote-ssh编辑界面，用来输出要远程登录的ssh

  ![在这里插入图片描述](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/20210318162526139.png)

这就是远程ssh信息的编辑界面：

![在这里插入图片描述](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/20210318162606137.png)

- **Host**是这个ssh信息在你本地的显示内容（这个可以修改自己能够区分的信息，因为后面往往并不是只有一台服务器）
- **HostName**是你的远程ssh的ip信息
- **User**是你的远程ssh的用户名，如果远程是Linux系统的话，这个就是你登录Linux的用户名

输入完成保存以后，左侧就会出现你的刚才设置的信息：

![在这里插入图片描述](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/20210318162919317.png)

然后点击下图圈起来的按钮，用来登录你的远程ssh

![在这里插入图片描述](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/20210318163014725.png)

点击完成，就会弹出新的vscode界面，需要你进一步输入远程ssh的信息：

![在这里插入图片描述](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/20210318163115796.png)

点击continue，之后会出：

![在这里插入图片描述](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/20210318163246472.png)

输入你的远程ssh主机的密码，之后：

![在这里插入图片描述](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/20210318163326266.png)

左下角出现如图字样，你就已经连接上了。

3. **设置免密登录**
当可以连接上ssh以后，打开命令行，输入：

```bash
ssh-keygen
```

回车，一直回车，不要输入任何内容，直到命令行就会输出一下信息：

![在这里插入图片描述](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/20210318163549952.png)

表示生成的公钥和秘钥，注意圈起来的路径文件，需要将其拷贝到你的远程ssh主机中，我远程主机时虚拟机，所以仅将其上上传到/home文件夹下即可，也就是吧id_rsa.pub文件拷贝（PS：刚才圈起来的按个目录一定有这个文件）。
之后操作远程ssh主机：

```
mkdir .ssh
mv id_rsa.pub .ssh
cd .ssh
cat id_rsa.pub >> authorized_keys
sudo chmod 600 authorized_keys
service sshd restart
```

可能在最后一条命令要输出你的账号登录密码。
这样远程ssh主机配置免密码登录就完成了。
然后你可以在vscode重复打开远程ssh的步骤，看看是否还需要输入密码了。

------

## 免密配置探讨

之所以想要对这部分免密部分进行探讨是因为，在这个过程中使用到了id_rsa（私钥）和id_rsa.pub（公钥）这两个文件。

而生成这两个文件是需要在命令行界面执行`ssh-keygen` 才能生成的。

而之所以通过使用这种方式可以实现远程登录免密，其实还是利用了ssh用户认证的两种最基本的方式，密码认证和密钥认证。

**密码认证**就是将自己的用户名和密码发给服务器进行认证，因此在每次打开远程ssh时需要输入你的密码。

**密钥认证**就是通过使用公钥和私钥进行身份验证，实现安全的免密登录。

**ssh密钥认证登录流程：**

- 在进行SSH连接之前，SSH客户端需要先生成自己的公钥私钥对，并将自己的公钥存放在SSH服务器上。
- SSH客户端发送登录请求，SSH服务器就会根据请求中的用户名等信息在本地搜索客户端的公钥，并用这个公钥加密一个随机数发送给客户端。
- 客户端使用自己的私钥对返回信息进行解密，并发送给服务器。
- 服务器验证客户端解密的信息是否正确，如果正确则认证通过。

![SSH密钥认证登录流程](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/download)



因此在配置VSCode的ssh远程登陆时，你只需要生成一份公钥私钥密钥对即可。如果你在远程服务器生成，则可以把公钥私钥复制到本地用户名下.ssh文件夹。如果你在本地生成，则需要复制到服务器的用户名下.ssh文件夹。

如果你是本地和服务器的ssh都有专门的用途，那就只能舍弃使用密钥登录的方式了。

## 结尾

在开发的工作中，起初我是使用wsl在本地进行开发。但是由于项目十分的庞大，导致在程序编译时，我的主机几乎无法使用，极其卡顿。因此我还是拿出了公司配的性能不太好的一个服务器，卡顿就让它在服务器上慢慢卡吧。

而在这个迁移的过程中，由于我的账户信息都在wsl上，Gerrit管理员为我开通拉取代码的权限是wsl用户下生成的公钥。如果在服务器上重新生成公钥私钥对，就需要重新找管理员。但是你可以将wsl的公钥私钥信息直接复制到你服务器上的同名文件内，然后保持相同的权限。这样你的服务器和wsl共用一套公钥私钥，就无需重新配置Gerrit上的信息了，主要还是找人办事麻烦的原因。

本文的分享记录就到这里，如果您觉得文章写的不错，欢迎您能留个赞再划过，让我继续保持持续创作的动力！

