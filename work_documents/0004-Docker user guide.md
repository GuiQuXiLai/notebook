# 0004-Docker user guide

1. 参考https://www.runoob.com/docker/ubuntu-docker-install.html  

   **ubuntu**

   ```bash
   sudo apt-get install curl
   sudo apt-get install curl
   ```

2. `sudo vi /etc/docker/daemon.json`然后写入下面并保存  

   ```json
   {  "registry-mirrors": ["http://hub-mirror.c.163.com"],  "insecure-registries": ["172.21.100.63:5000"]}
   
   ```

        注意`{`顶格，不要随便换行，不然可能不能用 

3. `service docker restart`，如果失败删除`/etc/docker/daemon.json`看看，如果确认是`/etc/docker/daemon.json`的问题重新写一个  

4. 找张平要docker做好的包  

   ```bash
   docker pull  172.21.100.63:5000/9x05
   ```

5. 运行 

   ```bash
   docker run -it -v /home/sim-zp/workspace:/home/workspace 172.21.100.63:5000/9x05 /bin/bash
   ```

   其中外部代码在`/home/sim-zp/workspace`，docker里面在`/home/workspace` 
   如果涉及到License，需要改mac地址，增加`--mac-address 02:42:ac:11:00:03`  

   ```bash
   sudo docker run -it -v /home/hujie/hj/code:/home/workspace 172.21.100.63:5000/9x05 /bin/bash
   ```

6. 运行后用su权限  

   ```bash
    su root
    cd /home/workspace
   ```

   编译`./simcom/build/sim7000C.sh`  

7. 运行完了后好像不太会退出来，简单的输入exit即可，但是这个时候CONTAINER ID视乎还存在  

   ```bash
   CONTAINER ID   IMAGE                     COMMAND       CREATED              STATUS                            PORTS     NAMES9389831b163a   172.21.100.63:5000/9x05   "/bin/bash"   About a minute ago   Exited (127) About a minute ago             nervous_hellman7cf82ce3a897   172.21.100.63:5000/9x05   "/bin/bash"   2 days ago           Exited (1) 2 days ago                       peaceful_khorana
   ```

   可能是用docker stop $(docker ps -a -q)  

8. 一旦运行后想删除或者docker更新了，需要先定制并删除之前的再重新pull，不然会有一个不同的interface  
   参考如下：  
   https://www.cnblogs.com/zouhong/p/11761889.html  

   ```bash
   docker stop $(docker ps -a -q)
   ```

   如果想要删除所有container的话再加一个指令：  

   ```bash
   docker rm $(docker ps -a -q)
   ```

        狠心把容器都删除掉了，因为光停止还是不能删除镜像。  

        删除镜像  

`docker rmi ID`

再去pull  

```bash
sudo docker run -it -v /home/hujie/hj/code:/home/workspace --mac-address 02:42:ac:11:00:03 172.21.100.63:5000/9x05 /bin/bash
```

