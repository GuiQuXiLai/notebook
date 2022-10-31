# 0008-git commit

1. 首先在需要添加代码的工程文件文件里只添加修改代码
2. `git status`查看变动的代码文件名
3. `git add .`提交所有变动的文件
4. `git commit `直接提交仓库

git commit 需要设置`git config -e --global`

![image-20221028100425867](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221028100425867.png)

其中[user]部分的name和email在由`git config --global user.name` 和 `git config --global user.email`设置过了

需要添加[commit]，对template文件位置进行设置，我将其放在`template=~/git-commit-template`

`git-commit-template`，是git commit 提交的模板

之后进行git commit 就会提示你填入以下内容

![image-20221028101048705](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221028101048705.png)

RequestType:问题类型_CaseID

- 问题类型取值：CR、PR和MR
  - CR：软件部自己提的case
  - PR：测试部/前端提出的case
  - MR：不止一个case
- CaseID：JIRA Case ID

> 若RequestType=PR，CaseID必须有。
>
> 若RequestType=CR，又没有CaseID,该项可省略。
>
> 若RequestType=MR，该项可省略。

如本次我填写PR_SIM7500-11072

TestType：测试类型

- 测试类型取值：NO、ST、HT、SH
  - NO：表示不需要测试
  - ST：表示需要软测测试
  - HT：表示需要硬测测试
  - SH：表示需要软测和硬测测试

Topic：功能模块

- 功能模块取值：SMS/Network/TCPIP/FTP/SSL/LBS/TTS

  ![image-20221028101918448](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221028101918448.png)

可根据JIRA Case上的模块类型填写

Title：用英文简要描述问题解决

Desrc：可与title相同内容

Rote：ADD_M/ADD_O/EN_M/EN_O中的一个

-  **[ADD_M]**自己认为是必须要写进release note 的，可以开放给所有客户的
- **[ADD_O]**自己认为是没有必要写release note 的，可能只是我们自己用用，客户用不到的
- **[EN_M]**自己认为是必须要写进 release note 的，修复了重要功能严重bug的
- **[EN_****O****]**修改了之前没发现的bug，如某些特别的情况不起作用，对客户程序没什么影响

**Projt：**The project of the case

**Owner**: The assignee of the case.
