# 每日打卡

>从明天起，做一个幸福的人

>喂马、劈柴，周游世界

>从明天起，关心粮食和蔬菜

>我有一所房子，面朝大海，春暖花开

除了每天写写日记，也应该对每天做了什么有个记录。

* 2019-11-26

1、夏曹俊老师课程关提供了项目建立的模板、S2017项目配置的解释（[在文件夹vs2017_setting](../img/VS2017_Project_Setting/))。

2、wmware 桥接模式不能上网如何解决？

答：编辑-虚拟网络编辑器-更改设置-选桥接模式的那个网络-将"桥街到"，选择本机在用的物理网卡（去windows的网络适配器查看）

3、Ubuntu上一些命令（以前没有用过或者用过不晓得区别）

```bash

sudo passwd       #装好系统设置root密码
su -              #切换到root

# 网络设置通过设置/etc/netplan/下文件，提示did not find expected key的原因是缩进问题

# ps:我设置后出错了，记得本周提问如何设置,暂时不弄了，不影响接下来的学习

touch xxx   #更新文件最后的访问时间

ln -s #软连接，源文件被修改此文件会失效
ln    #硬连接
```
内联函数inline、常量const相关总结，在windows-dev这个repo中

* 2019-11-27

1、C++中引用的知识点。(在windows-dev/Cpp_Assembly中reference.md中查看）

2、进程。windows中进程往往对应一个执行文件，Linux中，一个程序可以通过fork对应多个进程，进程有守护进程、前台进程（Cril+C终止）、后台进程（kill终止），进程查看用ps -ef命令，可以显示进程进程名、进程标识、父进程标识、时间等信息。终止进程，可以发送以数字表示的信号给进程，通知其结束，默认是15，等待所占用资源释放后再结束，直接发送kill -9 进程编号，可以直接杀死进程，pkill则是根据进程名字结束进程。PS：nginx常常用作前端，客户端基于线程，满足高并发需求。

3、nohup可以将前台进程设置在后台执行，
```bash
# /dev/null/为删除输出信息，默认nohup.out中，也可以指定其他文件
# &1标注输出，&2错误输出
nohup tail -f /var/log/syslog > /dev/null/ &1 (标注输出) or &2(错误输出)
```
4、用户管理

```
# 添加用户(test)，设置密码，用户目录，添加组及该用户所属于的组

useradd test
passswd test
su test # 切换到用户test
pwd     # 当前路径 output:空

useradd -m test -d /home/test -s /bin/bash
groupadd cpp
gpasswd -a test cpp
```

5、GitHub解决冲突

假设用户1修改了 xxx文件，并且push了，我这边再修改后push会提示拒绝，有冲突，查看冲突：

    git diff master origin/master

建议将该文件备份，然后执行以下操作(备份，先拉取再合并）：

```bash
git pull
vim xxx  #对其进行更改
git add xxx
git commit "my work"
git push
```
6、GitHub创建本地仓库缓存，在本地构建GitHub云端方法

在机器a上执行

    git init --bare /home/hanxinle/xdisk.git

则在该机建立了一个暂存区。

在机器b执行

    git clone hanxinle@xx.mm.yy.zz:/home/hanxinle/xdisk.git

则将repo拉取到本地，在本地创建文件等更改后，执行add,commit,push操作，其它机器执行

    git clone hanxinle@xx.mm.yy.zz:/home/hanxinle/xdisk.git

则可以在得到与机器b一致的repo，PS，把两个操作存在[github_commands.md](github_commands.md)中。    
