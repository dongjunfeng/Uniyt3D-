# Uniyt3D-

## MySQL数据库简介

  MySQL 是瑞典的MySQL AB公司开发的一个可用于各种流行操作系统平台的关系数据库系统，它具有客户机/服务器体系结构的分布式数据库管理系统。MySQL 完全适用于网络，用其建造的数据库可在因特网上的任何地方访问，因此，可以和网络上任何地方的任何人共享数据库。MySQL具有功能强、使用简单、管理方 便、运行速度快、可靠性高、安全保密性强等优点。MySQL用C和C++编写，它可以工作在许多平台（Unix，Linux，Windows）上，提供了 针对不同编程语言(C,C++,JAVA等)的API函数；使用核心线程实现多线程，能够很好的支持多CPU；提供事务和非事务的存储机制；快速的基于线 程的内存分配系统；MySQL采用双重许可，用户可以在GNU许可条款下以免费软件或开放源码软件的方式使用MySQL软件，也可以从MySQL AB公司获得正式的商业许可。
除了以上特点，MySQL 还有一个最大的特点，那就是在诸如 UNIX 这样的操作系统上，它是免费的，可从因特网上下载其服务器和客户机软件。并且还能从因特网上得到许多与其相配的第三方软件或工具。而在 Windows 系统上，其客户机程序和服务器程序库是免费的。

## MySQL的优点

在将 MySQL 与其他数据库系统进行比较时，所要考虑的最重要的因素是性能、支持、特性（与 SQL 的一致性、扩展等等）、认证条件和约束条件、价格等。相比之下，MySQL 具有许多吸引人之处：

* 1.简单易用
MySQL 是一个高性能且相对简单的数据库系统，与一些更大系统的设置和管理相比，其复杂程度较低。

* 2.价格
MySQL 对多数个人用户来说是免费的。

* 3.小巧
4.1.1的数据库发行版仅仅只有21M，安装完成也仅仅51M。（只是在刚开发的时候）

* 4.支持查询语言
MySQL 可以利用 SQL（结构化查询语言），SQL 是一种所有现代数据库系统都选用的语言。也可以利用支持 ODBC（开放式数据库连接）的应用程序，ODBC 是 Microsoft 开发的一种数据库通信协议。

* 5.性能
许多客户机可同时连接到服务器。MySQL数据库没有用户数的限制，多个客户机可同时使用同一个数据库。可利用几个输入查询并查看结果的界面来交互 式地访问 MySQL。这些界面为：命令行客户机程序、Web 浏览器或 X Window System 客户机程序。此外，还有由各种语言（如C, C++, Eiffel, Java, Perl, PHP, Python, Ruby, and Tcl）编写的界面。因此，可以选择使用已编好的客户机程序或编写自己的客户机应用程序。

* 6.连接性和安全性
MySQL 是完全网络化的，其数据库可在因特网上的任何地方访问，因此，可以和任何地方的任何人共享数据库。而且 MySQL 还能进行访问控制，可以控制哪些人不能看到您的数据。

* 7.可移植性
MySQL 可运行在各种版本的 UNIX 以及其他非 UNIX 的系统（如 Windows 和 OS/2）上。MySQL 可运行在从家用 PC 到高级的服务器上。

* 8.开放式的分发
MySQL 容易获得；只要使用 Web 浏览器即可。如果不能理解某样东西是如何起作用的，或者对某个算法感到好奇，可以将其源代码取来，对源代码进行分析。如果不喜欢某些东西，则可以更改它。

* 9.速度
MySQL 运行速度很快。开发者声称 MySQL 可能是目前能得到的最快的数据库。可访问 http://www.mysql.com/benchmark.html （MySQL Web 站点上的性能比较页），调查一下这个性能。

## MySQL数据库下载

从下面的地址中，点击右侧的 Download按钮，下载MySQL Install Community 5.7.17.0.msi文件.
```
http://dev.mysql.com/downloads/installer/
```

## MySQL的安装

1.双击后，弹出如下窗口：（如果系统有提示，选择允许）

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081354540705559.png)

2.安装开始界面

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081424329614055.png)

3.勾选 I accept the license terms，如下图：

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081424416495575.png)

4.选择下一步，弹出如下窗口：

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081424531496554.png)

5.选择第二项：Server only，如下图：（这一步选择非常重要）

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081425046331764.png)

6.点击下一步，示意图如下：

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081425161332744.png)

7.可以修改路径，也可以不修改，修改路径示意图如下：（可选）

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081425259921722.png)

8.点击下一步，进入准备安装界面

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081425373993673.png)

9.点击执行，安装

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081425485395311.png)

10.安装进度

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081426225865179.png)

11.安装完成

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081426415864450.png)

12.准备配置

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081427154613033.png)

13.配置服务器类型及端口号，默认即可

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081427351023433.png)

14.填写Root用户密码，__请牢记该密码__

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081428315866389.png)

15.设置用户和服务开机启动，默认即可

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081428509616475.png)

16.确认配置,点击Excecute,如果有弹出窗口，__一定要允许__.

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081429423673612.png)

17.配置完成，点击Finish

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081430507743378.png)

18.点击 Next继续。

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081431081027105.png)

19.完成安装

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081431327744609.png)


## MySQL安装验证

1.打开命令行窗口,找到MySQL控制台

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081434261807452.png)

2.输入root账户的密码(也就是在安装过程中输入的密码)

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081435176808319.png)

3.如果输入正确，则会显示MySQL>输入标记

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081435412429150.png)

4.输入显示所有数据库命令：show databases; 一定要有分号，并按回车

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081435583527578.png)

5.如果能够显示系统默认的4个数据库，则认为我们数据库完成安装正确。

![](https://nts.newbieol.com/static/k25/03_%E5%BC%95%E6%93%8E%E9%AB%98%E7%BA%A7%E8%BF%9B%E9%98%B6/%E5%8D%8F%E5%90%8C%E5%BC%80%E5%8F%91%E4%B8%8E%E6%95%B0%E6%8D%AE%E5%BA%93%E5%9F%BA%E7%A1%80/%E6%95%B0%E6%8D%AE%E5%BA%93/%E6%95%B0%E6%8D%AE%E5%BA%933MYSQL%E5%AE%89%E8%A3%85/images/081436440245697.png)


       
