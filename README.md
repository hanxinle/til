# 博客、Github 内容索引

我的旧博客在[博客园](https://www.cnblogs.com/hanxinle/)，这个博客记录的内容是零碎的，不便于查找资料。因此，我在2019-11-25 update: 基于 Github 建立了[新博客](https://hanxinle.github.io/)，我会把自己旧博客的精华及最新的学习成果更新在新博客。另，因为 GitHub 托管博客访问受限制，在 gitee 上布置了新的[博客](http://hanxinle.gitee.io/blog)。

这个repo (til) 用于每日打卡，以及汇集学习资源。
## 个人知识总结

* [http 服务器(C++)](https://github.com/hanxinle/http-server)
* [windows 程序设计(C++)](https://github.com/hanxinle/windows-programming)
* [自然语言处理](https://github.com/hanxinle/nlp)
* [MySql](https://github.com/hanxinle/mysql)
* [数字图像处理(matlab版)](https://github.com/hanxinle/matlab_image_processing)
* [机器学习实践](https://github.com/hanxinle/practical_machine_learning)
* [GitHub 命令行](https://github.com/hanxinle/til/blob/master/post/github_commands.md))



[每日打卡处](./post/til.md)

# 以下为资源汇集 

# [书籍源码地址](https://github.com/hanxinle/books-src)

>PS:以下链接打不开的话去[这里](https://github.com/hanxinle/books-src)寻找，内容都是从刚刚 books-src 链接复制的，这里就做个目录，不改了。

* [tlpi-book](./tlpi-book)

    《Unix 系统编程手册》

    对 sockets/ 下的一些文件进行修改，使得可以通过编译。

    编译步骤，先进入 lib/ 执行 make，然后进入主目录执行 make

* [unpv13e](./unpv13e)

    《Unix 网络编程卷1-套接字联网 API》

    注意看 README 文件，不支持 BSD4 的编译选项要跳过。


    1. 提示没有 if_dl.h 文件，请去网上复制文件内容，创建并放到 /usr/include/net/ 中；
    2. 提示缺少某个宏 MAX_RA，请去定义其为 1024（#define MAX_RA 1024）；
    3. 提示 size 类型错误，将其类型由 ssize_t 改为 socklen_t 。

* [孟宁-命令行工具（C语言版）-软件工程实践](./software_practice_in_c_by_mengning)

* [深入理解 Linux 程序设计源码](https://github.com/hanxinle/understanding-unix-linux-programming)

* [大话计算机随书附赠的资料](https://github.com/hanxinle/bigtalk_about_computer)

* [编译原理之美 - 手把手教你实现一个编译器(宫文学) - src](https://github.com/RichardGong/PlayWithCompiler)

* [Head First Java](./Head-First-Java)

* [慢雾安全提供的资料](https://github.com/slowmist)

* [Antlr4 语法](https://github.com/antlr/grammars-v4)

* [红色警戒1 代码](https://github.com/electronicarts/CnC_Remastered_Collection)

* [深入理解计算机系统的导读（关注博客）](https://www.cnblogs.com/figure9/archive/2010/04/10/1708942.html)

* [clasp](https://github.com/clasp-developers/clasp)

* [I hate regex](https://ihateregex.io/)-[GitHub](https://github.com/geongeorge/i-hate-regex) 

* 公众号：高性能服务器开发 上面有些很好的资料

* [milo yip 的 json 库教程](https://github.com/miloyip/json-tutorial)

* [cpp template 2nd 翻译](https://github.com/Walton1128/CPP-Templates-2nd--)

* [深度学习21天-随书资料](https://github.com/zhaoyongke/Caffe21Days)

* [caffe windows](https://github.com/HolidayXue/CaffeMerge)

* [boost_cook_book-src](./boost_cookbook_2013)
* [自制编程语言（Japan）-src](./make_your_own_language)
* [自制编程语言-基于C语言（郑钢）](./stepByStep)

《操作系统真象还原》（郑钢）代码的 3 个版本，代码应该一致，上传者直接上传了自己运行程序的版本，包括运行不通过时自己的调试。运行不通过去 Github 上找其它 repo 学习。

* [操作系统真象还原-src-1/3](./os_truth_src)
* [操作系统真象还原-src-2/3](./OS_lab-master)
* [操作系统真象还原-src-3/3](./tiny-os-master)
* 
* [Windows 程序设计（第5版）](./Windows-programming-5th)
* [30天自制操作系统-src](./30天自制操作系统)
* [多核和 GPU 编程课程资料（源码、课后答案、勘误） ](./multi_cores_gpu_programming)

## 2019.9
* [(转)GitHub教程-引子: pull request 是什么含义?](post/what_is_pull_request.md)
* [GitHub 命令行](post/github_commands.md)
* [(转).md 文件教学](https://blog.csdn.net/kaitiren/article/details/38513715)及其 [GitHub 地址](https://github.com/guodongxiaren/README)
* [数字图像处理( matlab )](https://github.com/hanxinle/matlab_image_processing)
* [实用机器学习](https://github.com/hanxinle/practical_machine_learning)
  * [Python 开发环境配置](https://github.com/hanxinle/practical_machine_learning/blob/master/0_Get_Start/start_with_python.md)
* [MPICH 在集群上配置(并行计算工具)](https://www.cnblogs.com/hanxinle/p/7688753.html)
* [给 CV 初学者的学习建议](post/live_record_advice_for_cv_beginner.md)


## 2019.10

* [实用机器学习](https://github.com/hanxinle/practical_machine_learning)
  * [Python 开发环境配置](https://github.com/hanxinle/practical_machine_learning/blob/master/0_Get_Start/start_with_python.md)
  * [数据预处理](https://github.com/hanxinle/practical_machine_learning/tree/master/1_Data_Processing)
  * [回归](https://gihub.com/hanxinle/practical_machine_learning/tree/master/2_Regression)
  * [分类](https://github.com/hanxinle/practical_machine_learning/tree/master/3_Classification)
  * [聚类](https://github.com/hanxinle/practical_machine_learning/tree/master/4_Clustering)
  * [关联规则](https://github.com/hanxinle/practical_machine_learning/tree/master/5_Apriori)
  * [强化学习](https://github.com/hanxinle/practical_machine_learning/tree/master/6_Reinforcement%20Learning)
  * [降维](https://github.com/hanxinle/practical_machine_learning/tree/master/7_Dimensionality%20Reduction)
* [mysql 从小工到进阶](https://github.com/hanxinle/sql)
* [(转) git commands by one file ](https://github.com/hanxinle/blog/blob/master/articles/git_examples.sh)


## 2019.11

* [BEYOND Machine Learning with Scikit-Learn and TensorFlow](https://github.com/ageron/handson-ml)
   
   PS: 不仅是随书代码,而是一套教程.
* [自然语言处理 知识体系(博客)](https://www.cnblogs.com/hanxinle/p/11864806.html) [GitHub](https://github.com/hanxinle/nlp/blob/master/nlp_start.md)
* [Spacy、NLTK 教程](https://github.com/hanxinle/nlp/tree/master/Spacy_NLTK)
* [对话机器人](https://github.com/hanxinle/nlp/tree/master/chatbot_)
  
  运用TF-IDF实现问答机器人，以及应用LSTM的推理机器人，能够根据事件的描述，推理出对该事件提问的正确答案。
* [剑指 offer 第一版 C++ 代码](https://github.com/hanxinle/job_interview_logs/tree/master/InterviewQuestions)

  GitHub 上有这些代码的Java版本作为参考，这些代码基于C++98&03，可以在学习过程中尝试更改这些代码，使其支持C++11或更高版本。
* [系统设计大宝箱](https://github.com/donnemartin/system-design-primer#system-design-interview-questions-with-solutions)

  关于系统设计，如何学习，面试准备，应有尽有的资料整理。

* [日常学习打卡](post/every_day_works.md)

## 2019.12 
* [第二届 TVM 与深度学习编译器会议总结](https://sampl.cs.washington.edu/tvmconf/)
[视频链接](https://www.youtube.com/watch?v=npqO0hVXZwU&feature=youtu.be&list=PLTPQEx-31JXjA2ZmvYT5s0RqDXFXTSjyL&t=3542)（ PS：课件见会议链接）

* [C++ 匠心之作](https://github.com/hanxinle/Cpp-0-1-Resource)

## 2020.1

* 网盘（网络、系统）

* 算法

* [2016 C++ 技术大会](http://boolan.com/lecture/cpp2016)
   * [吴咏 wei 演讲资料](https://github.com/adah1972/cpp_conf_china_2016)

* [Vscode 视频、文档](https://code.visualstudio.com/docs/getstarted/introvideos)

* [深入理解 Linux 程序设计源码](https://github.com/hanxinle/understanding-unix-linux-programming)

* [大话计算机随书附赠的资料](https://github.com/hanxinle/bigtalk_about_computer)

## 2020.4

* [手撕 leetcode 算法题目](https://github.com/labuladong/fucking-algorithm)

  语言比较朴素，可以看到是用自己的话总结的，理论部分还不够犀利、扎实，可以作为一个参考。

* [一个哥们儿总结的关于人的发展、成长的感悟（认同的标记[x]）](post/life_rules_from_other_guy.md)

## 2020.5

* [慢雾安全提供的资料](https://github.com/slowmist)
* [编译原理之美 - 手把手教你实现一个编译器(宫文学) - src](https://github.com/RichardGong/PlayWithCompiler)

## 2020.6

* [Antlr4 语法](https://github.com/antlr/grammars-v4)
* [红色警戒1 代码](https://github.com/electronicarts/CnC_Remastered_Collection)
* [深入理解计算机系统的导读（关注博客）](https://www.cnblogs.com/figure9/archive/2010/04/10/1708942.html)

* [clasp](https://github.com/clasp-developers/clasp)

* [I hate regex](https://ihateregex.io/)-[GitHub](https://github.com/geongeorge/i-hate-regex) 

* 公众号：高性能服务器开发 上面有些很好的资料

## 2020.7
* [milo yip 的 json 库教程](https://github.com/miloyip/json-tutorial)

* [cpp template 2nd 翻译](https://github.com/Walton1128/CPP-Templates-2nd--)

* [深度学习21天 随书资料](https://github.com/zhaoyongke/Caffe21Days)

* [caffe windows](https://github.com/HolidayXue/CaffeMerge)

* [陈硕 TCP/IP notes](https://chenshuo.github.io/tcpip-study/)

## 2020.8

* [Let Over Lambda - src](https://github.com/hanxinle/let-over-lambda)
* [on lisp](https://github.com/hanxinle/on-lisp)
* [practical common lisp](https://github.com/hanxinle/practical-common-lisp)
 
* [技术书籍源码汇总repo](https://github.com/hanxinle/books-src)
  
* [xv6-mit](https://pdos.csail.mit.edu/6.828/2012/xv6.html)
* [xv6-中文文档](https://th0ar.gitbooks.io/xv6-chinese/content/)
* [xv6 explained](https://github.com/YehudaShapira/xv6-explained)
* [xv6 github](https://github.com/mit-pdos/xv6-public)
* [xv6-with-doc](https://github.com/mit-pdos/xv6-riscv)
  
  PS：另有两本 xv6 的 pdf 文件位于仓库 books 中。

* [lynar moon engine-Youtube](https://www.youtube.com/watch?v=PzrJmXz6W7U&list=PLmvHLkJs7MrXB9tCf79HLtXggOyO9lUe1&index=3&t=0s)
* [lynar moon engine-Youtube-github](https://github.com/LynarStudios/LEMoon)
* [lynar moon engine-Udemy-Clion-src](https://bitbucket.org/officiallynarstudios/lynarmoonengine/downloads/)
  
## 2020.9

* [CppCon2016 资料](https://github.com/CppCon/CppCon2016)
* [elastos - 一个物联网（IOT）系统](https://github.com/elastos)
* [书籍：leanpub Linux C programming](https://leanpub.com/linuxsystemprogrammingwithc) 及 [源码](https://github.com/madmax440/gists)
* [30天自制操作系统源码](https://github.com/yourtion/30dayMakeOS)
* [quicklisp 文档](https://www.quicklisp.org/beta/UNOFFICIAL/docs/)

## 2020.10

* [doxygen 语法](./post/doxygen语法.md)
