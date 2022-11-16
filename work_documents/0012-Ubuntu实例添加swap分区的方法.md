# Ubuntu实例中添加swap分区的方法

本文来源于[Ubuntu实例中添加swap分区的方法](https://help.aliyun.com/document_detail/157171.html)

## 概述

本文主要讲述在Ubuntu实例中添加swap分区的方法。

## 详细信息

> 阿里云提醒您：
>
> - 如果您对实例或数据有修改、变更等风险操作，务必注意实例的容灾、容错能力，确保数据安全。
> - 如果您对实例（包括但不限于ECS、RDS）等进行配置与数据修改，建议提前创建快照或开启RDS日志备份等功能。
> - 如果您在阿里云平台授权或者提交过登录账号、密码等安全信息，建议您及时修改。

请您参考以下步骤进行操作：

1. 依次执行以下命令，创建一个空文件，锁定文件的大小。

   ```
   sudo mkdir -v /var/cache/swap 
   cd /var/cache/swap 
   sudo dd if=/dev/zero of=swapfile bs=1K count=4M
   ```

   > **说明***：文件的具体大小建议设定为内存的两倍。此处的1K×4M＝4GiB。*

2. 执行以下命令，将新建的文件转换为swap文件。

   ```
   sudo mkswap swapfile
   ```

3. 执行以下命令，给文件授权。

   ```
   sudo chmod 600 swapfile
   ```

4. 执行以下命令，启用swap分区。

   ```
   sudo swapon swapfile
   ```

5. 执行以下命令，进行验证。

   ```
   swapon -s
   top -bn1 | grep -i swap
   ```

   系统显示类似如下。

   ```
   KiB Swap: 4194300 total, 4194300 free
   ```

6. 执行以下命令，将该分区设置成开机自启。

   ```
   echo "/var/cache/swap/swapfile none swap sw 0 0" | sudo tee -a /etc/fstab
   ```

7. 执行以下命令，测试开机是否加载swap分区。

   ```
   sudo swapoff swapfile 
   sudo swapon -va
   ```

8. 如果您需要修改swap使用率，编辑

   ```
   /etc/sysctl.conf
   ```

   文件，修改vm.swappiness值。

   ```
   vm.swappiness=[$NUM]
   ```

   > **说明**：[$NUM]值为swap使用率，取值为0~100。swappiness等于0的时候表示最大限度使用物理内存，然后才使用swap分区；swappiness等于100的时候表示积极的使用swap分区，并且把内存上的数据及时的搬运到swap分区中。

## 适用于

- 云服务器ECS