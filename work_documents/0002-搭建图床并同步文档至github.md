# 0002-搭建图床并同步文档至github

搭建一个图床的想法由来已久了，之前作为学生时代，囊中羞涩，于是选择了使用`github/gitee`创建一个仓库作为自己的图床。

然而不好用就是不好用，`github`在国内的访问总是受限，上传到图床的一个图片总是刷新不出，极其搞人心态。而`gitee`呢，懂的都懂。简而言之，该付费还是要付费，付费以节省时间并享受到最优质的服务。

最近几天，折腾这一套的想法愈发浓烈，趁着今天上午没有着急的工作在阿里云购买了一个**对象存储OSS**作为自己的图床并把自己工作以来的经验总结为文档形式，上传至`github`的`work_documents`仓库。下面介绍整个过程的完整步骤：

## 1. 阿里云官网注册准备工作

这需要你有一个阿里云的账号，并且在阿里云的官网首页找到对象存储OSS进行购买，购买之后开通该服务。

<img src="https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221012190700102.png" alt="image-20221012190700102" style="zoom: 50%;" />

之后在阿里云官网还有三个步骤需要操作

第一：创建Bucket，Bucket是什么暂时不管，先创建

<img src="https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221012190907654.png" alt="image-20221012190907654" style="zoom: 50%;" />

图中我已经创建完毕，在创建是需要勾选读写权限为**公共读**

<img src="https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221012191002232.png" alt="image-20221012191002232"  />

第二：之后点击头像，找到`AccessKey`管理。

![image-20221012191137497](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221012191137497.png)

点击`创建AccessKey`

![image-20221012191320132](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221012191320132.png)

保存创建的`AccessKey ID`和`AccessKey Secret`

第三：在`Bucket列表`中找到文件管理，新建目录，我创建的是`images`

![image-20221012191619265](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221012191619265.png)

##  2. PicGo填写阿里云OSS相关信息

 ![image-20221012191512070](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221012191512070.png)

模仿就好，我就不详细叙述了。

##  3. Typora里进行如下设置

![image-20221012191848405](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221012191848405.png) 