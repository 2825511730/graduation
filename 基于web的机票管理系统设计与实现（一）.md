

@[toc]

<font color=red>**获取源码请关注公众号：C you again，回复“基于web的机票管理系统”或者“机票管理系统”**</font>

## 1 摘 要

近年来，我国发展迅速，对交通工具的需求量大幅度增加。飞机作为出行工具之一，花费时间短、用户体验度好，价格实惠、安全性高等优点自然成为人们的首选，这也导致等待时间长、购票效率低等一系列问题的出现，给用户和航空公司造成严重困扰。面对这些问题，在线机票预订系统显得格外重要。

本系统使用Eclipse开发工具，使用Redis、MySQL数据库，采用MVC三层架构的方式，结合当前最流行的SSM框架以及支付宝沙箱支付环境来实现各个功能。系统分为用户端和管理员端。用户端实现了用户注册与登录、用户评论、机票查询，机票预订，订单查询、广告展示等功能。管理员端包括航班信息管理模块、订单信息管理模块、用户信息管理模块、留言评论管理模块、广告信息管理模块、个人信息管理模块等六大模块，具有开放体系结构的、易扩充的、易维护的、具有良好人机界面的优点。

经过充分的测试，测试数据均正确无误，各个模块运行良好。机票预订系统的推出，为乘客出行提供方便，便于机场工作人员对机票信息进行管理，提高了机场工作人员对机票管理的工作效率。

**关键词：机票预订系统； 数据库； MVC； SSM； 面向对象**

## 2 系统相关技术概述

#### 2.1 Java web

Java Web，是用Java技术来解决相关web互联网领域的技术总和。随着Web互联网技术的出现和推广，基于Java技术的Java Web技术应运而生，并为解决互联网相关问题提出解决方案。我们知道，Web是由服务器和客户端两方面组成。基于Java语言的Web框架有很多种，用以适用不同的技术需求，但是都遵循最基本的原则和技术路线，即采用了MVC的架构设计思想，并通过Servlet或者Filter进行请求拦截，同时使用约定，XML或Annotation来实现必备的相关配置，充分利用其面向对象的特质，实现前台用户请求和后台程序响应的工作流程。

#### 2.2 三大框架SSM

SSM框架，是Spring + Spring MVC + MyBatis的缩写，这个是继SSH之后，目前比较主流的Java EE企业级框架，适用于搭建各种大型的企业级应用系统。
Spring是一个开源框架，Spring是于2003年兴起的一个轻量级的Java开发框架，由Rod Johnson在其著作Expert One-On-One J2EE Development and Design中阐述的部分理念和原型衍生而来。它是为了解决企业应用开发的复杂性而创建的。Spring使用基本的JavaBean来完成以前只可能由EJB完成的事情。然而，Spring的用途不仅限于服务器端的开发。从简单性、可测试性和松耦合的角度而言，任何Java应用都可以从Spring中受益。 简单来说，Spring是一个轻量级的控制反转（IoC）和面向切面（AOP）的容器框架。
Spring MVC属于Spring Framework的后续产品，已经融合在Spring Web Flow里面，它原生支持的Spring特性，让开发变得非常简单规范。Spring MVC 分离了控制器、模型对象、分派器以及处理程序对象的角色，这种分离让它们更容易进行定制。

MyBatis本是apache的一个开源项目iBatis, 2010年这个项目由apache software foundation 迁移到了google code，并且改名为MyBatis 。MyBatis是一个基于Java的持久层框架。iBATIS提供的持久层框架包括SQL Maps和Data Access Objects（DAO）MyBatis消除了几乎所有的JDBC代码和参数的手工设置以及结果集的检索。MyBatis使用简单的XML或注解用于配置和原始映射，将接口和Java的POJOs（Plain Old Java Objects，普通的 Java对象）映射成数据库中的记录。

#### 2.3 前端框架AngularJS

AngularJS是一个开发动态Web应用的框架。它让你可以使用HTML作为模板语言并且可以通过扩展的HTML语法来使应用组件更加清晰和简洁。它的创新之处在于，通过数据绑定和依赖注入减少了大量代码，而这些都在浏览器端通过JavaScript实现。

#### 2.4 数据库MySQL

MySQL是一种开放源代码的关系型数据库管理系统（RDBMS），使用最常用的数据库管理语言--结构化查询语言（SQL）进行数据库管理。MySQL是开放源代码的，因此任何人都可以在General Public License的许可下下载并根据个性化的需要对其进行修改。MySQL因为其速度、可靠性和适应性而备受关注。大多数人都认为在不需要事务化处理的情况下，MySQL是管理内容最好的选择。

#### 2.5 数据库Redis 

Redis（Remote Dictionary Server )，即远程字典服务，是一个开源的使用ANSI C语言编写、支持网络、可基于内存亦可持久化的日志型、Key-Value数据库，并提供多种语言的API。redis是一个key-value存储系统。和Memcached类似，它支持存储的value类型相对更多，包括string(字符串)、list(链表)、set(集合)、zset(sorted set --有序集合)和hash（哈希类型）。这些数据类型都支持push/pop、add/remove及取交集并集和差集及更丰富的操作，而且这些操作都是原子性的。在此基础上，redis支持各种不同方式的排序。与memcached一样，为了保证效率，数据都是缓存在内存中。区别的是redis会周期性的把更新的数据写入磁盘或者把修改操作写入追加的记录文件，并且在此基础上实现了master-slave(主从)同步。

#### 2.6 开发工具Eclipse

Eclipse 是一个开放源代码的、基于Java的可扩展开发平台。就其本身而言，它只是一个框架和一组服务，用于通过插件组件构建开发环境。幸运的是，Eclipse 附带了一个标准的插件集，包括Java开发工具（Java Development Kit，JDK）。

## 3 需求分析

#### 3.1 系统实现目标

如今，互联网遍布于生活的每个角落，不断改变着人们的生产生活，基于Web的机票预订系统就是借助互联网发展的热潮，方便大众，服务大众。具体实现以下两个目标：

 （1）	方便用户购票
 
用户可以访问前台系统浏览、查询航班信息，足不出户，预订机票，免去了以往寻找购票网点，排队购票的麻烦。

（2）	航空公司实现办公自动化

后台系统能使航空公司办事效率大幅度提高，它将所有的工作流程按照一系列流程进行规范化，从而减少工作时间，提高了人员的办事效率。

#### 3.2 系统功能分析

 - 后台航班信息管理：主要是指添加航班信息，删除航班信息，查询航班信息和航班信息详细情况查看等。
 - 
   后台订单信息管理：后台订单信息管理主要包括订单列表，查询订单信息，订单信息的删除等。
 
 - 后台用户信息管理：主要指注册用户的展示与按条件查询注册用户。

 - 后台留言评论管理：主要指展示用户的留言信息和按留言日期、留言用户查找留言信息等。

 - 后台广告信息管理：主要指添加广告信息，删除广告信息，设置广告的有效性等。

 - 后台个人信息管理：主要指查看个人信息，修改个人信息。

 - 前台登录与注册管理：包括前台系统用户的注册于登录。

 - 前台首页信息展示：主要是指航班信息展示、航班信息查询、航班信息详情、登录用户信息展示、留言板和个人信息详情与修改等。

 - 前台订单页面：主要是订单内容的填写和订单详情。 前台订单支付：是指使用支付宝沙箱环境支付订单。

#### 3.3 系统用列图

**系统前台功能用列图**

![](https://img-blog.csdnimg.cn/2020062913054442.png)

**系统后台功能用列图**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629130651305.png)

## 4 系统总体设计

#### 4.1 软件架构设计

此项目使用经典的三层架构模式[8]，分别是表现层，业务逻辑层和数据持久层。如下图所示。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629161925742.png)

表现层：表现层也称为表示层，位于最外层（最上层），离用户最近。用于显示数据和接收用户输入的数据，为用户提供一种交互式操作的界面。

业务逻辑层：业务逻辑层（Business Logic Layer）无疑是系统架构中体现核心价值的部分。它的关注点主要集中在业务规则的制定、业务流程的实现等与业务需求有关的系统设计，也即是说它是与系统所应对的领域（Domain）逻辑有关，很多时候，也将业务逻辑层称为领域层。

数据持久层：数据持久层也称为是数据访问层，其功能主要是负责数据库的访问，可以访问数据库系统、二进制文件、文本文档或是XML文档。简单的说法就是实现对数据表的select、insert、update以及delete的操作。

#### 4.2 总体功能模块设计

本系统主要分为前台子系统和后台子系统，两个子系统包含的具体功能如下：

1.	前台功能包括：

A.	用户登录
B.	用户注册
C.	航班查询
D.	机票详情
E.	机票预订
F.	订单支付
G.	订单查看
H.	用户留言
I.	个人信息查看与修改

2.	后台功能包括：

A.	航班信息管理
B.	订单信息管理
C.	用户信息管理
D.	留言评论管理
E.	广告管理
F.	个人信息管理
	
前台子系统和后台子系统详细功能如下图所示。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629162123983.png)

（1）	前台系统功能设计

A.	用户登录功能，详细功能说明如表4.1所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629162203700.png)

B.	用户注册功能，详细功能说明如表4.2所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629162233245.png)

C.	航班查询功能，详细功能说明如表4.3所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/2020062916225818.png)

D.	机票详情功能，详细功能说明如表4.4所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629162329946.png)

E.	机票预订功能，详细功能说明如表4.5所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629162359190.png)

F.	订单支付功能，详细功能说明如表4.6所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629162434840.png)

G.	订单查看功能，详细功能说明如表4.7所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629162503226.png)

H.	用户留言功能，详细功能说明如表4.8所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629162541553.png)

I.	个人信息查看与修改功能，详细功能说明如表4.9所示
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629162642681.png)

（2）	后台系统功能设计

A.	航班信息管理模块功能，详细功能说明如表4.10所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629162734948.png)

B.	订单信息管理模块功能，详细功能说明如表4.11所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629162803297.png)

C.	用户信息管理模块功能，详细功能说明如表4.12所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629162830600.png)

D.	留言评论管理模块功能，详细功能说明如表4.13所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629162857199.png)


E.	广告管理模块功能，详细功能说明如表4.14所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629162923133.png)

F.	个人信息管理模块功能，详细功能说明如表4.15所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629163025889.png)

#### 4.3 数据库设计

##### 4.3.1 数据库结构设计

通过建立该系统各个模块的E-R图[9]，是整个模块之间的功能变得更加清晰，模块间所具有的耦合性边的越低。管理员实体（Admin），留言评论实体（Discuss），航班实体（Flight），订单（Order）实体，普通用户实体（User）和广告信息实体（content）E-R图分别如下图所示。

**管理员实体（Admin）E-R图**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629163219407.png)

**留言评论实体（Discuss）E-R图**

![](https://img-blog.csdnimg.cn/20200629163243659.png)

**航班实体（Flight）E-R图**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629163314340.png)

**订单实体（Order）E-R图**

![](https://img-blog.csdnimg.cn/20200629163338765.png)

**普通用户实体（User）E-R图**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629163406306.png)

**广告信息实体（Content）E-R图**

![](https://img-blog.csdnimg.cn/20200629163437515.png)

##### 4.3.2 数据库表设计

为实现数据库的设计，对数据进行分表处理，每一个表格代表不同的信息和功能，分别如下图所示。

1.	管理员信息表（admin），用于存放管理员信息，表结构如表4.16所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629163612350.png)

2.	留言评论信息表（discuss），用于存放留言评论信息，表结构如表4.17所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629163642277.png)

3.	航班信息表（flight），用于存放航班信息，表结构如表4.18所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629163711492.png)

4.	订单信息表（order），用于存放订单信息，表结构如表4.19所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629163742666.png)

5.	普通用户信息表（user），用于存放用户信息，表结构如表4.20所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/202006291638194.png)

## 源码下载

**下期继续分享[《基于web的机票管理系统设计与实现（二）》](https://blog.csdn.net/qq_40625778/article/details/107039441)

获取源码请关注公众号：C you again，回复“基于web的机票管理系统”或者“机票管理系统”**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200629140932725.jpg)
