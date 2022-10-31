# 0007-解决WSL2与虚拟机冲突问题

WSL依赖于hyper-v必须开启，而VMware不依赖这个，必须关闭

> CMD管理员模式启动，输入`bcdedit /set hypervisorlaunchtype auto`开启，则可以使用WSL
> CMD管理员模式启动，输入`bcdedit /set hypervisorlaunchtype off`关闭，则可以使用VMware

**注意**：不管是开还是关都需要重启电脑