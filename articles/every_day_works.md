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

* 2019-11-28

1、编译与连接程序

```bash
#预处理,将头文件拷到源文件，宏定义替换
g++ -E hello.cpp -o hello.i
#编译，预处理的文件转变为汇编代码hello.s
g++ -S hello.i 
#汇编，将编译的结果生成二进制 hello.o
g++ -c hello.s
#链接，将上述过程的文件组合为可执行文件a.out（未用 -o指定输出文件的情形）
g++ hello.o
#执行，不可执行先运行 chmod +x a.out
./a.out
```
2、makefile书写的模板

```
[变量]
目标($@)：依赖($+)
[TAP]执行语句$(变量)    
```
2、socket编程入门（自己打程序体会socket工作的方式，同时补充相关网络知识）

3、深度工作

含义：认知能力最大化的工作状态

有助于深度工作的做法：（1）仪式感；（2）远离社交媒体等干扰；（3）独立的空间；（4）刻意练习，即每日拿出固定的时间来专门进行某一技能、知识、领域的针对性学习，训练。

4、emacs -nw 终端模式

* 2019-11-29

1、大事件：整理王老师代码留下来的编码规范，个人见过的最好的 <Personal C++ Coding Rules> 

2、详细了解了socket编程中，IP、port含义，结构体socketaddr_in的内部结构、含义，inet_addr等函数的使用及其含义。

3、程序员只要关注链路层、IP层、传输层、应用层（可以有下层无上层，决不能有上层无下层），IP层传输只关注一个数据包的传输过程，传输多个数据包的时候顺序及传输过程并不可靠，TCP和UDP作用于IP层之上，确定对方收到数据，并且将丢失的数据重传。

4、客户端程序中客户端套接字是由操作系统内核创建，IP用计算机IP，port随机。

5.回声客户端，及解决read、write函数调用次数不定，并且TCP不限制传输字节长度时通过多次调用read、write函数得到正确传输结果的方法。

* 2019-11-30 

1、寄存器的64bit表示与32bit、16bit的寄存器的关系。

2、CPU表示数据大多小端模式，低位低字节，读取的时候从高位向低位读取，一个变量的地址指的是它的低地址所在的内存地址。

