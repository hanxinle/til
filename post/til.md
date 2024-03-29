# 每日打卡

>从明天起，做一个幸福的

>喂马、劈柴，周游世界

>从明天起，关心粮食和蔬菜

>我有一所房子，面朝大海，春暖花开

除了每天写写日记，也应该对每天做了什么有个记录

* 2019-11-26

1、夏曹俊老师课程关提供了项目建立的模板、VS2017 项目配置的解释（[在文件夹vs2017_setting](../img/VS2017_Project_Setting/))

2、VMware 桥接模式不能上网如何解决

答：编辑-虚拟网络编辑-更改设置-选桥接模式的那个网络-"桥街"，选择本机在用的物理网卡（去windows的网络适配器查看）

3、Ubuntu上一些命令（以前没有用过或者用过不晓得区别

```bash

sudo passwd       #装好系统设置root密码
su -              #切换到root

# 网络设置通过设置/etc/netplan/下文件，提示did not find expected key的原因是缩进问题

# ps:我设置后出错了，记得本周提问如何设置,暂时不弄了，不影响接下来的学

touch xxx   #更新文件最后的访问时间

ln -s #软连接，源文件被修改此文件会失效
ln    #硬连
```
内联函数inline、常量const相关总结，在windows-dev这个repo

* 2019-11-27

1、C++中引用的知识点(在windows-dev/Cpp_Assembly中reference.md中查看）

2、进程。windows中进程往往对应一个执行文件，Linux中，一个程序可以通过fork对应多个进程，进程有守护进程、前台进程（Cril+C终止）、后台进程（kill终止），进程查看用ps -ef命令，可以显示进程进程名、进程标识、父进程标识、时间等信息。终止进程，可以发送以数字表示的信号给进程，通知其结束，默认15，等待所占用资源释放后再结束，直接发送kill -9 进程编号，可以直接杀死进程，pkill则是根据进程名字结束进程。PS：nginx常常用作前端，客户端基于线程，满足高并发需求

3、nohup可以将前台进程设置在后台执行
```bash
# /dev/null/为删除输出信息，默认nohup.out中，也可以指定其他文
# &1标注输出&2错误输出
nohup tail -f /var/log/syslog > /dev/null/ &1 (标注输出) or &2(错误输出)
```
4、用户管理

```
# 添加用户(test)，设置密码，用户目录，添加组及该用户所属于的组

useradd test
passswd test
su test # 切换到用户test
pwd     # 当前路径 output:

useradd -m test -d /home/test -s /bin/bash
groupadd cpp
gpasswd -a test cpp
```

5、GitHub 解决冲突

假设用户1修改 xxx文件，并且push了，我这边再修改后push会提示拒绝，有冲突，查看冲突

```git diff master origin/master```

建议将该文件备份，然后执行以下操(备份，先拉取再合并）

```bash
git pull
vim xxx  #对其进行更改
git add xxx
git commit "my work"
git push
```
6、GitHub创建本地仓库缓存，在本地构建GitHub云端方法

在机器a上执

```git init --bare /home/hanxinle/xdisk.git```

则在该机建立了一个暂存区

在机器b执行

```git clone hanxinle@xx.mm.yy.zz:/home/hanxinle/xdisk.git```

则将repo拉取到本地，在本地创建文件等更改后，执行add,commit,push操作，其它机器执

```git clone hanxinle@xx.mm.yy.zz:/home/hanxinle/xdisk.git```

则可以在得到与机器b一致的repo，PS，把两个操作存在 github_commands.md 中。

* 2019-11-28

1、编译与连接程序

```bash
#预处,将头文件拷到源文件，宏定义替
g++ -E hello.cpp -o hello.i
#编译，预处理的文件转变为汇编代码hello.s
g++ -S hello.i 
#汇编，将编译的结果生成二进制 hello.o
g++ -c hello.s
#链接，将上述过程的文件组合为可执行文件a.out（未 -o指定输出文件的情形）
g++ hello.o
#执行，不可执行先运行 chmod +x a.out
./a.out
```
2、makefile书写的模

```
[变量]
目标($@)：依($+)
[TAP]执行语句$(变量)    
```
2、socket编程入门（自己打程序体会socket工作的方式，同时补充相关网络知识

3、深度工

含义：认知能力最大化的工作状

有助于深度工作的做法：（1）仪式感；（2）远离社交媒体等干扰；（3）独立的空间；（4）刻意练习，即每日拿出固定的时间来专门进行某一技能、知识、领域的针对性学习，训练

4、emacs -nw 终端模式

* 2019-11-29

1、大事件：整理王老师代码留下来的编码规范，个人见过的最好的 <Personal C++ Coding Rules> 

2、详细了解了socket编程中，IP、port含义，结构体socketaddr_in的内部结构、含义，inet_addr等函数的使用及其含义

3、程序员只要关注链路层、IP层、传输层、应用层（可以有下层无上层，决不能有上层无下层），IP层传输只关注一个数据包的传输过程，传输多个数据包的时候顺序及传输过程并不可靠，TCP和UDP作用于IP层之上，确定对方收到数据，并且将丢失的数据重传

4、客户端程序中客户端套接字是由操作系统内核创建，IP用计算机IP，port随机

5.回声客户端，及解决read、write函数调用次数不定，并且TCP不限制传输字节长度时通过多次调用read、write函数得到正确传输结果的方法

* 2019-11-30 

1、寄存器 64bit 表示 32bit 16bit 的寄存器的关系

2、CPU 表示数据大多小端模式，低位低字节，读取的时候从高位向低位读取，一个变量的地址指的是它的低地址所在的内存地址

3、网络学习关注如何设计稳定、可靠地协议，传输方案，系统学习关注内存、I/O管理，语言学习关心正确使用库，不要过度学习，频繁造轮子忽略学习目的

4、关于常量引用，可以指向常量、表达式、函数、不同数据类型，注意，const 引用指向不同类型产生临时变量

5、数 a[3] = {1,2,3},常引用可以如下声明，int * const & rArray = a，或 int (&rArray)[3] = a，前者不需要指定数组大小，增加灵活

* 2019-12-1

1、汇编中 lea eax,[xxxh] 是把地址值赋给寄存器，反汇编看到 
```
mov eax, dowrd ptr [ebp-20h],
mov [eax],O3H 
```

这样的代码，要想到指针初始化及改变指向的值。如 
```
int *p = a; 
*p =3;
```
2、每个程序运行时都会开辟内存空间（不能视作所有程序共享一块儿极大的内存），该内存空间可分为四块，栈空间、堆空间、代码区、全局区。其中，代码区存放程序中的函数；函数中的局部变量（包括main函数）、函数的参数等信息会在栈中分配空间，程序结束，系统自动回收栈空间。堆空间由用户分配的空间，程序结束后，堆空间不释放，所以程序中需要程序员手动释放申请的内存，否则成为内存泄漏

3、this指针是独享初始化时隐藏初始化的，指向的是对象的地址，即函数调用者的地址值。this位于栈区

4、对象可以存在于栈、堆、全局区中，如对class A而言

```c++
A a1; //全局

int main ()  {
    A  a2;  //栈区

    A * pA = new A;   //堆区

    return 0
}

```
* 2019-12-4

1、一旦定义了构造函数，必须使用其中一个初始化对象

2、使用 new 堆空间为对象分配空间会调用初始化构造函数，malloc不会调用构造函数

3
```c++
Person {
    int a;
};

Person p;    //不会调用构造函
p.a = 0;   

Person1 {
    int a= 0;
};

Person1 p1;  //调用构造函

Person2 {
    int a;
    Person2() {} //无这句，Person p2() 则是调用函数
};

Person2 p2(); //构造函
```

4、全局区声明变量调用构造函
```c++
Person {
    int a;
};

Person p1;  //全局区调用构造函

//在声明了构造函数Person() {}后，无论全局区还是main函数中，*p = new Person 或 *p = new Person()都会初始化构造函数，malloc不会调用构造函数。不确定的话，写程序查看，不同的编译器或许会有不同的处理

```
5、查看堆、栈
```c++
Person * p  = new Person;  

cout << p  << endl; //
cout << &p << endl; //
```
* 2019-12-5

1、继承方式默认是private，对于父类成员，其访问类型取基类、继承方式的“最小值”

2、初始化成员列表的初始化顺序是按照变量定义顺序初始化

3、初始化成员列表等价于构造函数

4、构造函数调用其它构造函数的写法 写在初始化成员列表中

5、要想使用父类指针，要求继承类型是public

6、C++默认无多态这种情形，只根据指针类型调用函数

* 2019-12-6

1、C++根据虚函数机制实现多态，借助基类指针（创建不同子类、基类类型），运行时决定执行函数

2、基类声明为虚函数，子类重新实现该函数，该函数还是虚函数，子类虚函数关键字“virtual”可以不接

```c++
class Base {
    virtual void run() {cout<<"Base::run()"<<endl;}
};

class A : public Base {
    void run() {cout<<"A::run()"<<endl;}
};

class B : public Base {
    void run() {cout<<"B::run()"<<endl;}
};

void testrun(Base * base)  {
    base->run();
}

main {

    //以下几种方法都可
    testrun(new A);
    testrun(new B);

    base * bA = new A;
    bA -> run();

    base * bB = new B;
    bB -> run();

}

```
* 2019-12-8

1、菱形继承会导致最下面的子类成员变量冗余、重复，有歧义导致无法访问基类成员

2、虚继承可以解决菱形继承的问题，对基类虚继承，共享基类的变量

3、虚继承有虚表指针，虚表第一项是虚表指针相对于对象地址的偏移，第二项是基类成员相较于子类成员的偏移地址

4、多继承：如果子类继承的多个父类都有虚函数，那么子类对象会产生多张虚表

5、static 成员变量

和程序周期同样的生命周期，相较于全局变量，限制了访问方式，防止被修改

static变量访问、static函数设计，要考虑线程安全问题

* 2019-12-9

1、const成员函数要是非静态成员函数（static全局生命周期，const可能会涉及已经析构的对象），函数声明包含const，实现时也要加上const关键字

2、const函数与同名非const函数构成重载

3、拷贝构造函数，对象创建的时候创建，用已经声明并初始化的对象初始化新的对象

4、固定的参数调用  (const 类名& 对象)

5、编译器默认的拷贝构造函数会用已有对象的地址的内容，覆盖新对象地址的内容

6、在类继承的时候，子类的拷贝构造函数可以调用父类的拷贝构造函数，参数就是子类对象名（理解为父类拷贝构造函数需要父类指针类型的参数，此时填入了子类对象作为实参）

7、类的成员变量都是栈区分配空间，可以用默认拷贝构造函数，此时是浅拷贝。如果存在堆上分配内存的情况（指针类型成员变量），一定要用深拷贝，即新的对象初始化需要在堆上独立分配空间，避免多个对象指向同一块堆内存，在修改、销毁堆内存的时候发生错误

* 2019-12-10

1、对象类型作为参数或者返回值，这个过程会产生临时的中间对象，调用拷贝构造函数，为了防止作为参数时产生临时对象，可以传递引用类型参数

2、匿名对象，格式：类名（），匿名对象也具有访问类成员的权限，在需要临时访问类成员而不想创建对象时可以使用这种方法，如用C++做leetcode题目时写测试代码的时候

3、隐式构造函数，采用单变量赋值给对象类型（单变量作为对象类型函数的参数）时候，等价于单参数的调用构造函数（多参数情况说明其它参数有默认值），这种写法可能造成迷惑，可以用explicit关键字加在构造函数前，禁止这样初始化对象

4、编译器在特殊情况会为类生成无参构造函数，这些特殊情况包括：（1）成员变量声明时初始化；2）存在虚函数，创建对象时要为虚函数表生成虚表地址；（3）虚继承，此时生成虚表，内容是两个指针（一个是该虚表地址相对与对象地址的偏移，另一个是基类成员相对于子类成员的偏移地址）；4）含有对象类型的成员，并且该成员显式定义了构造函数；5）父类有显式构造函数的子类对象   总结：当对象创建时需要进行一些额外工作的时候，编译器就会为对象创建无参的构造函数并且调用

5、友元，只能是友元类或者友元函数，非不能声明非友元类中某个函数是友元函数，然后赋予这个函数对私有成员访问权限

6、内部类。可以访问外部类的私有成员，但是反之不行；可以直接方位该类的静态成员，内部类不影响外部类的内存布局，它不属于外部类，只是为了访问外部类的成员提供的一种机制

7、局部类，函数内部定义的类。不能访问函数的局部成员（函数局部成员只有调用函数才会生成，故在不调用函数时不能访问不存在的变量），不能有static类型成员（因为static必须在类外初始化，而内部类的生命周期在函数调用后就消失了，不能外部初始化，这一机制与局部类生命周期矛盾）

* 2019-12-11

1、运算符重载是给原来的运算符增加或者定制功能，一般而言，重载后的参数、返回值都可以定制为类等原运算符不支持的类型

2、有些运算符只能重载为成员函数， = ,[],(),->，有些函 <<,>>则需要在类外重载+=返回对象的引用，return *this 【PS1,2设计的原则并不是唯一的，而是根据函数调用情况来重载，有些函数是通过对象调用（第一个参数是类的实例类型），所以写作成员函数，有些调用重载后的函数的返回值需要被赋值或者连续调用（返回类型const，函数也要加const，因为const类型只能调用const函数），或者禁用对返回值赋值（返回const类型或者将=”重载{什么都不做即可}，设置为私有）

3、子类有重载，涉及父类的成员，可以在父类设置相应的重载函数，子类传子类对象调用父类重载函数

* 2019-12-12

1、模板：类型参数化的代码复用技术，模板定义的函数是调用时实例化，编译器根据参数类型生成不同的函数并且调用，因此，模板实现不能分别放置在不同.h.cpp文件，可以将其实现放.hpp文件中，即有实现的头文件

2、VC++编译过程分别编译不同.cpp文件.obj文件，通过链接将main.obj函数调用地址等信息根据与其它obj文件信息进行修改，模板函数如果放在独立的cpp文件中，不调用没有实例化，无函数调用地址提供给main.obj，链接过程会出错，故采用1的做法

3、类型转换的4个函数，const_cast ,将const转为非const；dynamic_cast多类型转换（支持继承体系类型转换），提供运行时安全检查，不安全赋值为0；static_cast，缺乏运行时安全检测，不能交叉转换（不是同一继承体系的，无法转换）， 常用于基本数据类型的转换、非 const 转成 const，适用最广；reinterpret_cast用于底层强制转换，没有类型检查和格式转换，直接拷贝二进制数据，可以交叉转换，可以将指针和证书互相转换

4、C++11中NULL就是0，以此作为函数参数有二义性，空指针用nullptr代替

5、lambda表达式，\[ \]中捕获变量分为值捕获或者地址捕获，默认值捕获，可以认为捕获到的是常量，mutable关键字可视为临时声明个变量等于捕获到的常量值，可以对该变量表征的常量进行自增运算，\[=\]表示值捕获。\[&a\]表示按地址捕获a，可以修改a的值，\[&\]代表地址捕获所有函数体中需要用到的变量

* 2019-12-13

1、异

throw抛出异常，在本函数中寻找异常处理代码（catch),如果没有则会在上一层函数中寻找异常处理程序，直到main函数中，如果还没有异常处理程序，则程序终歀

下面例子中，try捕获throw抛出的异常，cath根据捕获的异常类型对异常进行处理。devide（）抛出异常后，无异常处理代码，test（）捕获异常并且处理，main函数调用test(),如果产生异常，异常在test()中处理，不影响main中程序的执行

```c++
int divide(int v1, int v2) throw(int) {  //声明时表征异常类型给接口调用
	if (v2 == 0) {
		// 抛出异常
		throw 666;
        //throw "除数不能0";
	}
	return v1 / v2;
}

void test() {
	try {
		int a = 10;
		int b = 0;
		int c =  divide(a, b) 
        //产生异常后，thow后的代码不会被执
        c++;
        cout <<"c = " << c << endl;
        
	} catch (int exception) {   //catch(...)则是捕获任意类型异常
		cout << "产生异常(int):" << exception << endl;
	} catch (const char *exception) {
		cout << "产生异常(const char *):" << exception << endl;
	}
}

int main ()  {
    test();
    return 0;
}
```
2、智能指针，智能指针是指向堆空间，不是指向栈空间堆空间，不是指向栈空间的对象。auto_ptr是c++03标准，现在不使用，因为其有缺陷，如不支持指向数组;shared_ptr使用最广，多个指针可以指向同一块内存，当最后一个指针回收时释放堆空间，shared_ptr使用时，其包含对共有空间的引用计数use_count(),这是一种强引用，在两个类包含互相包含的类指针时，main中对指针对象赋值，会发生内存泄漏，解决的方式是其中一个类内指针声明为weak_ptr，弱引用不会产生引用计数，对shared_ptr使用，各指针变量应该处于同一个作用域中，否则可能导致堆空间释放

* 2019-12-14

Ever tried, ever failed. No matter, try again, fail again, fail better. The world is yours.

* 2019-12-15 

1、Cheat Engine0day的基本用法

* 2019-12-16/17 

很多工作时间用来炉石，打断了自己的计划

* 2019-12-18

卸载炉石，读了自己曾经的微博，有感如下，发了微博

今年转了超级多的微博，差不多所发的微博是过去几年的和。这是从那个鬼地方走出来后放飞自我了，我看着当年的自己写给自己的话，如今只记得当年并没有100%拼命，是过去4年糟糕的经历干扰了对纯纯本科时光的记忆，我读着那些文字，看到了当年的朝气、进取、偶尔幻想的自己，读着浪淘沙的小懿的微博，不知不觉离开故乡，和浪淘沙，和他们相识近十年，而我似乎在这时间之河中慢慢迷失了自己，这两个月不断地找回自己内心深处的自己，今夜又归乡几步路，久违了，那个叫我常讲的“我”

我要战斗，不知疲倦，不知恐惧，不怕困难的战斗，不要让自己对自己再失望了

* 2019-12-19

1、CPP_RULES，自己从Wangxm老师的编码中总结了一些编码规范

2、把《程序设计实践》中第一章风格相关内容二次读一遍，接下来是数据结构部分

3、大飞码字上看到技术人员的好的品质：激情、进取、自学、乐观，深有同感

* 2019-12-20

1、今天学习了UML的相关知识，以前困惑于写代码不能有像写文章那般规划提纲的工具，想不到工具是有的，只是自己没有利用到，visio就是UML工具，我早前一直将其作为论文画图工具

2、UML的知识概

1）类的表示，类名为首字母大写，类成员第一个单词首字母小写，其余单词首字母大写，操作命名同成员，需要在末尾加上()，表征为类的操作,最后可以添加类的职责（功能描述）。对象作为类的实例，也是位于矩形矿种，冒号左边为实例名，冒号右边为类(实例:类名），无实例名只有类名表示（：类名）匿名对象
<center>
|      |

| 类名 |
| 成员 |
| 操作 |

|类的描述|

</center>


2 <<构造型>>可以作为部分属性的标题，实质是创建新的模型元素解决实际问题

3）关于UML如何组织的，请看

![](../img/uml_conventions.png)

其中最主要的是图中“关联”到“实现”的一些横线，这些线能够帮助梳理类间关系，是 OOD 的说明工具

* 2019-12-21

1、OOD 中较常用的关系有调用、继承、实现（使得...生效）、是...的一部分（无法独存）

2、TCP 传递文件中，可以通过结构体定制协议，但是更加好的做法是，通过 protobuf，这样能杜绝多语言通信结构体的对齐等问题，使用 json、xml 也是可以的，只是速度上会有妥协;

3、TCPserver 封装为类，这个还不太了解，需要去参考代码、实现。暂时想法，数据部分就是要传递的内容，每个server对象就是打开一个端口，等待客户端的输入信息

* 2019-12-22

1、第一次直播，确定了两个星期后的任务，定制TCP协议

2、STL 中最重要的是容器和算法，从这两个开始学习

3、这两天休息时间过度，应该调整一下自己的作息规律

* 2019-12-29

1、TCP/IP 发送、接收文件的 c，cpp 版本

* 2019-12-30

1、解决了文件传输过程中的粘包问题（文件内容包含莫名其妙的字符）

2、解决了文件名字传输、接收问题，传输文件名字只传输与文件名相同大小的buff内容，接收数组大小由1024改做100，文件名字不再包含乱码等问题

* 2019-12-31

1、项1的文档

* 2020-1-5

1、代码评审存在的问题。（1）构造函数中不做业务相关的内容，因为出错不可控；2）C++11中，成员声明的时候要初始化；3）ip_用char ip_[16]，port用int，便于验证：4）字符串无修改，记得 const

* 2020-1-6

1、libevent在Linux epoll（同步非阻塞)，在 Windows 下是 Select模式

2、阻塞 IO:BIO,同步非阻塞 IO：NIO，异步非阻塞IO：AIO

3、阻塞（blocking) 结果返回前，当前线程被挂   — socket；非阻塞（nonblocking) 结果返回前，线程不阻 — epoll select;同步（Sync) 功能调用无结果不返回，事情一件件做；异步（Async):功能调用后无结果立即返回，等待通知，一件事情没完成就可以做下一件

* 2020-1-7

1、libevent线程池（非阻塞多路复用机制，默认有锁，此项目要查代码

2、QT（信号槽机制，MVD，不使用MVC

* 2020-1-8

1、云盘实战课程原型搭建，在多线程、libevent这里，自己有些迷惑，需要从这里开始补充

2、算法方面，滑动窗口法

* 2020-1-9,10

1、上述两种算法的细节总结,easy部分题有18页，嘿嘿

* 2020-1-13,14

1、http协议工作流程，TCP/IP、网卡的工作原理

* 2020-1-15

1、网络设备：集线器、交换机和路由器

* 2020-1-16

1、网络之服务

* 2020-1-17~18

回家过年遇上肺炎疫情

* 2020-2-19

1、异或运算，为不进位加法，满足交换律，结合律，与0异或值不变，可用于找连续数字的缺失值，及元素出现两次的数组中存在的唯一一个出现一次的元素，参看黑一本笔记

2、堆的作用，最小堆求最大的K的元素，最大堆求第K小的元素

* 2020-2-21

1、stl 初步，template、regex、memory、string、exception。项目：bitcion.cpp（未消化）

* 2020-2-22

1、stl之容器，完成了array、list、deque、map、vector，明天完成unordered_map和项目

* 2020-2-23

1、multimap

2、调整自己的学习计划

* 2020-2-24

1、项目：circular_buffer

* 2020-3-11

1、stl：algorithm 完成 1/3；design_pattern 中template method、strategy

* 2020-3-20

1、OS 中的 process，及其在 Linux 下应用

* 2020-3-21

处理器管理（进程）及存储管理初步

* 2020-3-22

1、存储管理、文件管理、设备管理及各自系统构成  

* 2020-3-23

1、线程同步（线程锁方法：互斥锁、旋转锁、读写锁、条件锁）

* 2020-3-24

1、进程同步：共享内存、Unix 域套接字

* 2020-3-25

1、Python线程池

* 2020-3-26

1、异步处理

* 2020-3-28

1、工程编码实践项,命令行菜单小程序

* 2020-3-29

1、总结命令行菜单小程序项目的得失

* 2020-3-30~4-2

1、计算机网络学习2、买了一本关于如何提升学习效率的书籍3、整理自己的资料4、学习了 pdf 文件添加书签以及做笔记的新方法，提升学习效率

* 2020-4-3~4-7

1、网络层

* 2020-4-8

1、传输层

* 2020-4-9

1、提前练习会儿书法，在记笔记的时候，写字比较顺利甚至有点享受；2、有思考地读书，能够提升自己信息吸收得速度及信息提取的质量；3、对所做事情有个认真的态度的话，对事情的推进、进度、质量才有相当力度（认真是一种纪律，像运动一样天天进行）；4、自己以前唯一能做到的事情——入迷，现在就是缺少入迷，对现实世界不能入戏；5、抓其他工作的前提是要抓思想建设，这是毛主席影视作品学到的。

* 2020-4-10

1、传输层 FIN2、个人图腾：写作

* 2020-4-11

1、网络结束

* 2020-4-12 ~ 16

1、blog2、common lisp env

* 2020-4-17 ~ 20

1 some blog

* 2020-4-21

1、stl-Algorithm, stl-io

* 2020-4-22 

1、memory

* 2020-4-23

1、thread.

* 2020-4-29,30

1、Quantlib、boost 1_730

* 2020-5-3,4

1、基础过了一遍；

* 2020-5-5

1、Linux、net 程序设计框架。

* 2020-5-7

>cd  source_dir
> ctags -R

(in vim)
>:set tags= source_dir/tags

C+] jump

C+t back

* 2020-5-8

1. 封装了tcp，Linux 下.so 的生成与配置。

* 2020-5-9

1、http\php 服务器初步编码。（尚需要代码重构，技术点消化）

* 2020-5-10

1、mysql windows

* 2020-5-11~17

1、计划、谋划的重要性；

* 2020-5-18

1. quantlib 提供编码规范

* 2020-5-19

1. apue-src learn

* 2020-5-20

1. 游双 Linux 网络编程


* 2020-5-26

1. 一些电视剧：《生活大爆炸》，《小谢尔顿》,《天蝎》，《福尔摩斯》，《这里的黎明静悄悄》

* 2020-5-31

1. compiler

* 2020-6-1,2,3,4

1. compile

* 2020-6-9

1. Java

* 2020-6-10

1. 递归、树

* 2020-6-11

1. 树遍历、递归与非递归深入、C 接口与实现

* 2020-6-12

1. bst template.

* 2020-6-27

前段时间眼睛有些小问题，暂时认为是疲劳引起的，以后要注意休息，注意保护眼睛。

* 2020-6-28

费曼学习法：

1. 拿一张白纸在顶部写下要学的内容的名称；
2. 用最直白的语言解释这个概念；
3. 找出自己不是很明白或是在解释过程中卡壳的地方回看概念出处直至完全理解。

* 2020-6-29~7.9

整理一些资料，最近几天发现了网上的总结和自己之前看的STL资料互相映射弥补，所以需要把这些东西都尽量自己总结在一起，形成文档，更重要的是在文档中添加可索引的代码。

* 2020-7-10 ~ 16

基本排序算法和 linux 系统学习。

* 2020-7-17 ~ 31

从内蒙古顺利返深，并且将路上需要处理的事情都处理好，保护了眼睛，路上吹空调感冒了，吃了3天药自己好了。搬了家，整理好了自己的物品，接下来的日子明确自己的技术方向，并且建立自己的技术护城河。

给自己配了一台电脑，老电脑不适合长时间、频繁跑大程序了，但是还是需要带出去使用，所以得保护好老电脑，Fighting。

* 2020-8-1 ~ 10

组成了新电脑，安装软件，因为系统不稳定，将其调整到次新版本。反思，要回归平静状态，补充做计划的重要性认知，不仅仅重视执行，而是从一开始就重视执行情况，思考要从源头抓起，从源头就开始发挥力量。

* 2020-8-11，12

调整了 Linux-cpp-notes 中 cpp 文件夹的内容，记录了开发环境配置的文档，整理了汇编部分发现，自己上个阶段把知识点总结到了这个打卡的地方，有时间要把这部分内容集中到 Linux-cpp-notes 中 cpp 文件夹。

把自己最近时间的工作，总结了，并且归类到三个项目文件，便于对自己的生活进行管理。

* 2020-8-13

早起把 cpp 资料汇总到 linux_cpp_notes 中，删掉了原本的 cpp-concepts (cpp-newbie,cpp-begin)。以 Projects 的形式注明自己最近在忙的事情，一共三个，开发及考试。

* 2020-8-17


一些 cpp\系统编程\网络编程相关项目：

1. 金山卫士 https://share.weiyun.com/5hxVWP7 
密码：WbUK

1. flamingo IM 
https://github.com/balloonwj/flamingo 

1. 电驴源码
链接：https://pan.baidu.com/s/11IceO8vO2e16wsJyPJfM3g  
密码:omev 

1. filezilla
链接:
https://pan.baidu.com/s/1e4IMWobw2OFMmJbHyYAiXA  
密码: 8vci 

1. 12306
链接:
https://pan.baidu.com/s/1qQref2HZVXwBiXOQDo_SoA  
密码: 6tnm 

* 2020-8-18

1、完成事业单位备考第1部分考点学习；2、Linux C 语言从源文件到可执行文件的每个过程，以及 gcc 指令，用 gdb 调试可执行文件的初步教程。

* 2020-8-19

1、完成事业单位备考第2部分的1/2; 2、编译系统各个阶段的作用整理完毕发布在博客上了。3、略清苦的备考过程中就没有乱七八糟的想法和浪费时间的杂事了，想起了2009年的时候，夫不争则天下难以与之争，当集中精力做事的时候就是竞争力最强的时候，平时别想这些有的没的。

* 2020-8-20
  

1、完成事业单位备考第3部分1/3；

* 2020-8-21~25

rest

* 2020-8-26

1、备考第3部分

* 2020-8-27~30

1、备考资料完毕；2、Linux 反汇编重温数据存储

* 2020-8-31
  

1、事业单位1无面试资格，停止做题目，继续搞技术

* 2020-9-1~2
  

1、Windows 进程

* 2020-9-3~8

1、线程，2、Be Black.

* 2020-9-9~12
  

1、卖了 4 批书籍；2、VC++ multithread(推及C++11、Linux)

* 2020-9-13、14

1、multi_thread 十亿数据处理一个示例；2、multi_thread 动态链接库及测试；3、QT 图片处理单线程及多线程版本。

* 2020-9-15、16

1、文档整理，接下来 网盘项目和编译原理这部分。

* 2020-9-17~21

Clean the room

* 2020-9-22~24

win32 代码生成控件并且使用

* 2020-9-25

Linux网络编程初步，多种并发模型初步，还需要自己做笔记夯实。

* 2020-9-26 ~ 10-5
  

完成了 Linux 下的网络编程基本 socket 函数的使用与网络连接状态的转变，封装了 tcp 并用 多线程、epoll 等实现了服务端并发接收多个客户端，最后实现了一个 http 服务器，对 http 掌握程度加深。

* 2020-10-6~8

备考事业单位，接下来学习高性能服务器设计，包括 nginx，同时要推进云盘项目向前进发。

* 2020-10-11
  

事业单位考试结束，回来卖了几本书，开始新阶段的学习。

* 2020-10-12~17

游双，高性能服务器编程及其它相关资料

* 2020-10-18~27
  

买了新键盘又退货，有钱才有动力；外部条件对自身的提升是有限的。

* 2020-11-1
  

Windows is shit.Stop learn deep about it.

* 2020-11~12

完成一些大略上的思考，完成早年笔记的电子化过程。

* 2020-12-19

设计模式（简单工厂）

* 2020-12-20~2021-1-3
  

修炼小成，弄好了简历。接下来要下大力气才能变成“超级赛亚人”。

* 2021-1-4~10

系统，开始做一些算法题目

* 2021-1-14

已投简历，并且算法题开始稳步搞起，接下来补足其它技术及经营 GitHub、博客。

* 2021-1-15~22
  

面试，已经拿到几个 offer，发现如下问题，并提出改进：

1. 分清主次。有些公司的招聘流程特别繁琐，准备这一家可以准备其它 3 家以上都够了。要有所权衡，要不要放弃优势去在面试间隙宝贵时间填补这类空白。算法套路一些公司不太深究，因为做了背过答案

就差不多能写出来，没做过就吭吭吃吃要写半天，可能两个小时就写两个题目，面试效率有待商榷。我的面试策略是熟悉基本数据结构和算法，面试时很多不需要白板编程而是说下思路、实现过程中有哪些需

要注意的地方，我觉得这个比较好，也是我该用心准备的地方。但是 leetcode 上一些题目的解法确实在思维上给我启发，是个宝库。

改进：算法也好，其它方面也罢，基础要打好，不要别人一问起来，熟悉的概念就是说不出什么来。

2. 项目展示，我的简历上只有一个项目，因此将这一个项目讲清楚十分必要。求职前期以为求职不忙，可以先放上一个项目，再重构及加上第二个项目。现在看来时间紧张，根本来不及，因此更有必要将这个

唯一的项目讲清楚。我给自己提出的改进是做些辅助的资料带过去，包含信息有设计文档、开发迭代的记录、编码规范等，不要有那种不如公司规范我就觉得没有必要做，把这个当成是个不写在简历但是表现

优势在面试阶段的第二个项目。

3. 一些题目的解答为了强调自己的理解，说法不够“官方”，下次应该先简短引述教材上的说明，再3句话内概括说下自己的理解和技术体验；

改进：翻阅教材，上网搜集一下常见问题的答案，往往自己会说印象最深的 1 点，网上可能给你补充到 5 点。

4. 简历存在的问题：无六级，有人事反馈，即使是社招也会去看的，所以要放上去；学校教育经历的问题，有几次面试方会问是否是全日制教育经历，要将“全日制、统招、学术性研究生”这几个关键字加上；

改进：添加必要信息，已经完成。

5. 技能怎么搭配？我确实做过若干 Windows 应用，并且将 Windows 编程写进了技能栏里，但其实我求职的目标并不在 Windows 客户端编程，项目介绍也是跨平台的，因此既然不求这个岗位，就将这个删掉，如果有面试官看了 GitHub 首页，会看到我有Windows编程的技能，并且简历中也说明了服务端是 跨平台。

改进：删掉次要技能

6. 关于 Qt，我在简历中写了使用过 Qt，确实很多人联系我，我都如实告知，我只是简单用了下，虽然了解他的工作机制，designer 的使用，但是并没有深究其中模块。等于变相拒绝了这些 offer，因此自己应该花点时间把这一块儿补上，做些项目体验下 QT 实施项目与 MFC 的不同。

改进：面试间隙补足一下 QT 项目

7. 关于 MySQL。我在 Github 首页就放上了一个 sql 知识技能总结的仓库，现在一年多没看手生了就会去查，也通过 C++　编程实现过　CURD　等常见操作，之前没有在简历中西写　MySQL，我觉得又是完美思想在作怪，我又不是没学过，只是用的时候去查命令，查 API，查自己写过的代码，因此应该在简历中加上。

改进：简历加上 MySQL

* 2021-1-23~26
  

面试安排太多，人都有点崩溃了。编码要时刻熟练，不能临时抱佛脚，字符串处理要熟悉一下解法。按照自己笔记记录的内容再加把劲儿。

* 2020-1-27

昨天视频面代码的题目自己吸取了教训，不再那么磨磨蹭蹭，直接就速度敲出了题目的初级解法。今天搞 bpftrace，在 apt、snap 等软件管理工具下安装，竟然还是有坑的，收藏了几个网页，帮助跳出这些坑。

* 2021-1-31
  

整理心情，整理技术，扩展一下再出发。

* 2020-2-21

 自己感觉这20天自己做的东西太少了，围绕着书本搞起来是不行的，必须要围着项目搞起来。

 * 2021-2-25

昨天完成了网盘原型项目，这次重新实现了一次，能在4天内完成这个项目。

* 2021-4-5

最近完成了一个 qt 项目，目前在 stl 进阶。

* 2021-4-21

项目完成了三个，gitee博客开张。

* 2021-5-31

改变了思想，5月17日就入职了，这两三周一直在编译 WebRTC，自己转到音视频领域耕耘了。

* 2021-6-24

编译 webrtc，难说入门，还是要写点实际的应用才好说自己入门了。这个有资料，自己勇敢写就行了。自己现在做些 Janus 服务端的研究，webrtc 分为三块，音视频编解码、服务、还有（）(忘了叫啥。。。)，自己逐渐搞这两块儿，能搞出很多东西了。



* 2021-8-17

  刚刚看流媒体服务器的代码看魔怔了，突然感觉自己对C++ 有了新的感觉，最近恰好在学 FFmpeg，上班前觉得这门课比较贵，想不到后来的工作就是做这块儿，当时觉得贵的课程都买下来了，在单位慢慢看。

  上周转正了，对我而言是一个新的起点。加油。

* 2021-5 - 2022-7

  这段时间的工作内容是视频会议相关的技术，包括 SRS、webrtc、ffmpeg、AWS，AWS 浅浅地使用后随着项目的取消，不再深入研究，SRS 因为公司后续放弃了视频会议，也没有再继续跟进它的内部技术，后续的技术布局主要围绕着 ffmpeg 来进行。从我的判断来说，ffmpeg 和 SRS 更具有适用性，而 webrtc 相对复杂，并且只能完成 demo 级别的作品，需要后续继续研究。



* 2022.8- 2023.7

又空窗了一年，开始想学习汇编提升自己，后来女友借款的事情可以说摧毁了很多东西，虽然自己尽力帮助了，但还是埋下了一些隐患。这空窗的一年自己最大的收获是学会了写外挂，这些想来就是志和大学时候就会的东西，自己蹉跎了这么多年才真正的了解和掌握。

* 2023.7 - 2024.2

2023 年十月分手了，新的公司一切都好，特别幸运遇到殷凯这个好搭档，自己在方直的工作中学到了很多，殷凯 3 月就离职了，3 越后开始就是自己一个人在方直学习了，我要先消化方直所用到的技术，利用一切资源提升自己客户端开发的能力。最近自己对安全行业特别感兴趣，已经开始在慢慢看安全方面的资料了，如果有机会的话，也向这个方向慢慢转向。

