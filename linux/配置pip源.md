由于写python代码随时需要用到下载轮子，但是由于下载的轮子是国外源，下载网速非常慢。常常限制在10~30Kb，因此往往需要下载一整夜，或者下载超时导致下载失败。

通过在往上搜索，查到到了两种使用国内镜像源完成pip下载的任务。

ps：使用国内镜像源下载very very的爽！！！

共两种方案：

> 一、方案一——随用随改型 
>
> 二、方案二——永久修改型

## 一、方案一——随用随改型

1.按下“win+r”键进入运行界面，输入“cmd”。

![img](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/v2-ed0f5d03ff6125c1094a7507de228b4b_720w.png)

2.”enter“键回车，进入命令提示符界面。

![img](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/v2-440a0df2e2ecc3817c5f8724bad104de_720w.png)



3.接下来在输入“pip install xxx”时插入国内镜像源地址，变为“pip install -i 地址 xxx”并回车。

几个常用镜像源： 

- 阿里云：http://mirrors.aliyun.com/pypi/simple/
- 清华大学：https://pypi.tuna.tsinghua.edu.cn/simple/
- 中国科学技术大学：http://pypi.mirrors.ustc.edu.cn/simple/

**举一个例子，**

在命令提示符界面输入：

pip install -i https://pypi.tuna.tsinghua.edu.cn/simple/ opencv-python

![img](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/v2-d60db5819e1061577efa8a27351ed6fd_720w.png)

由于随用随改型需要牢记国内几个镜像源的地址，强烈建议这篇文章进行收藏，淦！

当然如果你不想频繁的复制粘贴镜像源地址，你当然可以采用下面的永久修改型进行一次设定。

## 二、方案二——永久修改型

### Windows系统

1.在磁盘c下的用户（当前登录用户即可）下新建pip文件夹.

![img](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/v2-ae78130f6b8573b7ce8f68871c38e2c7_720w.png)

2.进入pip文件夹，新建一个文本文档，并将其名称及扩展改为“pip.ini”

![img](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/v2-7fbde9a6f2929019eeaae92976d690ed_720w.png)

3.以记事本的方式打开,输入下面内容，并保存

> [global]
>
> index-url = https://pypi.tuna.tsinghua.edu.cn/simple/
>
> [install]
>
> trusted-host = [https://pypi.tuna.tsinghua.edu.cn](https://pypi.tuna.tsinghua.edu.cn/)

4.此时重新进入cmd，直接“pip install xxx”，可以看到此处还是清华大学的镜像源

![img](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/v2-8ebbaa52beb95ad675d386325f8ca9f2_720w.png)

### Linux or Mac系统

1. 使用软件包的安装用户，执行如下命令：

   ```bash
   cd ~/.pip
   ```

   如果提示目录不存在，则执行如下命令创建：

   ```bash
   mkdir ~/.pip 
   cd ~/.pip
   ```

2. 编辑pip.conf文件。

   使用**vi pip.conf**命令打开pip.conf文件，写入如下内容：

   ```bash
   [global]
   #以华为源为例，请根据实际情况进行替换。
   index-url = https://mirrors.huaweicloud.com/repository/pypi/simple
   trusted-host = mirrors.huaweicloud.com
   timeout = 120
   ```

3. 执行**:wq!**命令保存文件。

如果觉得本文对你有所用处，点个赞吧,你的鼓励是我创作的动力。