# ubuntu添加新用户并且为其赋sudo权限

##  添加用户

```bash
sudo adduser username
```

![image-20221207092646258](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221207092646258.png)



## 添加sudo权限

```bash
sudo usermod -G sudo username
```

![image-20221207093159165](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221207093159165.png)



## 添加root权限

如果需要让此用户有root权限，执行命令：

```bash
sudo vim /etc/sudoers
```

修改文件如下：

```
# User privilege specification
root ALL=(ALL) ALL
username ALL=(ALL) ALL
```

保存退出，username用户就拥有了root权限

## 修改用户密码

修改root密码（默认root无密码，第一次执行时创建密码）：

```bash
sudo passwd root
```

修改开机登录密码（用户名为username）：

```bash
sudo passwd username
```

