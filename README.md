# Interview_yc
自己整理的面试题与解析
[TOC]



 

Python中如何使用线程池和进程池？

threading.local的作用？

进程之间如何进行通信？

什么是并发和并行？

进程锁和线程锁的作用？

### 解释什么是异步非阻塞？

“阻塞”与"非阻塞"与"同步"与“异步"不能简单的从字面理解，提供一个从分布式系统角度的回答。

1. **同步与异步**

   同步和异步关注的是消息通信机制 (synchronous communication/ asynchronous communication)

   所谓同步，就是在发出一个*调用*时，在没有得到结果之前，该*调用*就不返回。但是一旦调用返回，就得到返回值了。换句话说，就是由*调用者*主动等待这个*调用*的结果。

   而异步则是相反，*调用*在发出之后，这个调用就直接返回了，所以没有返回结果。换句话说，当一个异步过程调用发出后，调用者不会立刻得到结果。而是在*调用*发出后，*被调用者*通过状态、通知来通知调用者，或通过回调函数处理这个调用。

   典型的异步编程模型比如Node.js

   举个通俗的例子：你打电话问书店老板有没有《分布式系统》这本书，如果是同步通信机制，书店老板会说，你稍等，”我查一下"，然后开始查啊查，等查好了（可能是5秒，也可能是一天）告诉你结果（返回结果）。

   而异步通信机制，书店老板直接告诉你我查一下啊，查好了打电话给你，然后直接挂电话了（不返回结果）。然后查好了，他会主动打电话给你。在这里老板通过“回电”这种方式来回调。

2. **阻塞与非阻塞**

   阻塞和非阻塞关注的是程序在等待调用结果（消息，返回值）时的状态.

   阻塞调用是指调用结果返回之前，当前线程会被挂起。调用线程只有在得到结果之后才会返回。

   非阻塞调用指在不能立刻得到结果之前，该调用不会阻塞当前线程。

   还是上面的例子，你打电话问书店老板有没有《分布式系统》这本书，你如果是阻塞式调用，你会一直把自己“挂起”，直到得到这本书有没有的结果。

   如果是非阻塞式调用，你不管老板有没有告诉你，你自己先一边去玩了， 当然你也要偶尔过几分钟check一下老板有没有返回结果。在这里阻塞与非阻塞与是否同步异步无关。跟老板通过什么方式回答你结果无关。





### 路由器和交换机的区别？

什么是域名解析？

如何修改本地hosts文件？

生产者消费者模型应用场景及优势？

什么是cdn？

LVS是什么及作用？

Nginx是什么及作用？

keepalived是什么及作用?

haproxy是什么以及作用？

什么是负载均衡？

什么是rpc及应用场景？

简述 asynio模块的作用和应用场景。

简述 gevent模块的作用和应用场景。

twisted框架的使用和应用？

——————————————————————
redis和memcached比较？

redis中数据库默认是多少个db 及作用？

python操作redis的模块？

如果redis中的某个列表中的数据量非常大，如果实现循环显示每一个值？

redis如何实现主从复制？以及数据同步机制？

redis中的sentinel的作用？

如何实现redis集群？

redis中默认有多少个哈希槽？

简述redis的有哪几种持久化策略及比较？

列举redis支持的过期策略。

MySQL 里有 2000w 数据，redis 中只存 20w 的数据，如何保证 redis 中都是热点数据？ 

写代码，基于redis的列表实现 先进先出、后进先出队列、优先级队列。

如何基于redis实现消息队列？

如何基于redis实现发布和订阅？以及发布订阅和消息队列的区别？

什么是codis及作用？

什么是twemproxy及作用？

写代码实现redis事务操作。

redis中的watch的命令的作用？

基于redis如何实现商城商品数量计数器？

简述redis分布式锁和redlock的实现机制。

什么是一致性哈希？Python中是否有相应模块？

如何高效的找到redis中所有以oldboy开头的key？

### 第四部分 前端、框架和其他（155题）

### 谈谈你对http协议的认识。

HTTP是应用层协议。它把联网的细节都交给了通用、可靠的因特网传输协议TCP\IP协议。

![](https://s1.ax1x.com/2018/11/20/F9M2Qg.png)



谈谈你对websocket协议的认识。



什么是magic string ？

如何创建响应式布局？

你曾经使用过哪些前端框架？

什么是ajax请求？并使用jQuery和XMLHttpRequest对象实现一个ajax请求。

如何在前端实现轮训？

如何在前端实现长轮训？

vuex的作用？

vue中的路由的拦截器的作用？

axios的作用？

列举vue的常见指令。

简述jsonp及实现原理？

是什么cors ？

列举Http请求中常见的请求方式？

列举Http请求中的状态码？

列举Http请求中常见的请求头？

看图写结果：
![img](https://images2018.cnblogs.com/blog/425762/201805/425762-20180523193331193-1780213562.png)

看图写结果：
![img](https://images2018.cnblogs.com/blog/425762/201805/425762-20180523193350024-1394121124.png)

看图写结果：
![img](https://images2018.cnblogs.com/blog/425762/201805/425762-20180523193402254-925709250.png)

看图写结果：
![img](https://images2018.cnblogs.com/blog/425762/201805/425762-20180523193412085-688600397.png) 

看图写结果：
![img](https://images2018.cnblogs.com/blog/425762/201805/425762-20180523193421487-536908496.png)

看图写结果：
![img](https://images2018.cnblogs.com/blog/425762/201805/425762-20180523193433388-1947519928.png)

django、flask、tornado框架的比较？

### 什么是wsgi？

**Web服务器网关接口**（**Python Web Server Gateway Interface**，缩写为WSGI）是为[Python](https://zh.wikipedia.org/wiki/Python)语言定义的[Web服务器](https://zh.wikipedia.org/wiki/%E7%B6%B2%E9%A0%81%E4%BC%BA%E6%9C%8D%E5%99%A8)和[Web应用程序](https://zh.wikipedia.org/wiki/%E7%BD%91%E7%BB%9C%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F)或[框架](https://zh.wikipedia.org/wiki/Web%E5%BA%94%E7%94%A8%E6%A1%86%E6%9E%B6)之间的一种简单而通用的[接口](https://zh.wikipedia.org/wiki/%E4%BB%8B%E9%9D%A2_(%E7%A8%8B%E5%BC%8F%E8%A8%AD%E8%A8%88))。自从WSGI被开发出来以后，许多其它语言中也出现了类似接口。

WSGI区分为两个部分：一为“[服务器](https://zh.wikipedia.org/wiki/%E4%BC%BA%E6%9C%8D%E5%99%A8)”或“网关”，另一为“应用程序”或“应用框架”。在处理一个WSGI请求时，服务器会为应用程序提供环境信息及一个回调函数（Callback Function）。当应用程序完成处理请求后，透过前述的回调函数，将结果回传给服务器。

所谓的 *WSGI 中间件*同时实现了API的两方，因此可以在WSGI服务器和WSGI应用之间起调解作用：从Web服务器的角度来说，中间件扮演应用程序，而从应用程序的角度来说，中间件扮演服务器。“中间件”组件可以执行以下功能：

- 重写[环境变量](https://zh.wikipedia.org/wiki/%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F)后，根据目标[URL](https://zh.wikipedia.org/wiki/%E7%BB%9F%E4%B8%80%E8%B5%84%E6%BA%90%E5%AE%9A%E4%BD%8D%E7%AC%A6)，将请求消息路由到不同的应用对象。
- 允许在一个[进程](https://zh.wikipedia.org/wiki/%E8%A1%8C%E7%A8%8B)中同时运行多个应用程序或应用框架。
- [负载均衡](https://zh.wikipedia.org/wiki/%E8%B4%9F%E8%BD%BD%E5%9D%87%E8%A1%A1)和远程处理，通过在[网络](https://zh.wikipedia.org/wiki/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C)上转发请求和响应消息。
- 进行内容后处理，例如应用[XSLT](https://zh.wikipedia.org/wiki/XSLT)样式表。

**实现该协议的模块：**

- wsgiref
- werkzurg
- uwsig

### django请求的生命周期？



列举django的内置组件？

列举django中间件的5个方法？以及django中间件的应用场景？

简述什么是FBV和CBV？

django的request对象是在什么时候创建的？

如何给CBV的程序添加装饰器？

列举django orm 中所有的方法（QuerySet对象的所有方法）

only和defer的区别？

select_related和prefetch_related的区别？

filter和exclude的区别？

### 列举django orm中三种能写sql语句的方法。



django orm 中如何设置读写分离？

F和Q的作用?

values和values_list的区别？



如何使用django orm批量创建数据？

### django的Form和ModeForm的作用？

用来做检验字段

更加便捷的实现设置



### django的Form组件中，如果字段中包含choices参数，请使用两种方式实现数据源实时更新。

django的Model中的ForeignKey字段中的on_delete参数有什么作用？

django中csrf的实现机制？

django如何实现websocket？

基于django使用ajax发送post请求时，都可以使用哪种方法携带csrf token？

django中如何实现orm表中添加数据时创建一条日志记录。

django缓存如何设置？

django的缓存能使用redis吗？如果可以的话，如何配置？

django路由系统中name的作用？

django的模板中filter和simple_tag的区别？

django-debug-toolbar的作用？



django中如何实现单元测试？

解释orm中 db first 和 code first的含义？

django中如何根据数据库表生成model中的类？

使用orm和原生sql的优缺点？

简述MVC和MTV

django的contenttype组件的作用？

### 谈谈你对restfull 规范的认识？



接口的幂等性是什么意思？

什么是RPC？

Http和Https的区别？

### 为什么要使用django rest framework框架？

- 在做项目期间用到的是前后端分离的架构，前端用Vue后端用Django
- 为了更好的和前端人员配合，我们采用rest协议来确保接口风格的一致性
- django rest framework可以帮助我快速的开发符合rest规范的接口



### django rest framework框架中都有那些组件？

**1. 路由**

- 可以通过as_view传参数，根据请求方式不同执行相应的方法
- 可以在url中设置一个结尾，类似于： .json

**2. 视图**

- 帮助开发者提供了一些类，并在类中提供了多个方法以供我们使用

**3. 版本**

- 在url中设置version参数，用户请求时候传入参数。在request.version中获取版本，根据版本不同做不同处理

**4. 认证**
写一个类并注册到认证类，在类的的authticate方法中编写认证逻辑。

- 认证成功（user,auth）
- raise AuthticateFaild(….)
- None

**5. 权限**
写一个类并注册到权限类，在类的的has_permission方法中编写认证逻辑。

- True
- False

**6. 频率限制**
写一个类并注册到频率类，在类的的 allow_request/wait 方法中编写认证逻辑。

```
allow_request
	 True 
	 False  如果返回False，那么就要执行wait
```



**7. 解析器**

- 根据ContentType请求头，选择不同解析器对 请求体中的数据进行解析。
- POST /index/ http1.1.\r\nhost:11.11.11.11\r\nContent-Type:url-formendo…. \r\n\r\nuser=alex&age=123
- POST /index/ http1.1.\r\nhost:11.11.11.11\r\nContent-Type:application/json\r\n\r\n{….}

**8. 分页**

- 对从数据库中获取到的数据进行分页处理: SQL -> limit offset
  - 根据页码：<http://www.luffycity.com/api/v1/student/?page=1&size=10>
  - 根据索引：<http://www.luffycity.com/api/v1/student/?offset=60&limit=10>
  - 根据加密：<http://www.luffycity.com/api/v1/student/?page=erd8>



### django rest framework框架中的视图都可以继承哪些类？

`APIview、ViewSets、Generic views

### 简述 django rest framework框架的认证流程。

https://www.cnblogs.com/renpingsheng/p/9534984.html

### django rest framework如何实现的用户访问频率控制？

Flask框架的优势？

Flask框架依赖组件？

Flask蓝图的作用？

列举使用过的Flask第三方组件？

简述Flask上下文管理流程?

Flask中的g的作用？

Flask中上下文管理主要涉及到了那些相关的类？并描述类主要作用？

为什么要Flask把Local对象中的的值stack 维护成一个列表？

Flask中多app应用是怎么完成？

在Flask中实现WebSocket需要什么组件？

wtforms组件的作用？

Flask框架默认session处理机制？

解释Flask框架中的Local对象和threading.local对象的区别？

Flask中 blinker 是什么？

SQLAlchemy中的 session和scoped_session 的区别？

SQLAlchemy如何执行原生SQL？

ORM的实现原理？

DBUtils模块的作用？

以下SQLAlchemy的字段是否正确？如果不正确请更正：

`from` `datetime ``import` `datetime`` ``from` `sqlalchemy.ext.declarative``import` `declarative_base`` ``from` `sqlalchemy ``import` `Column, Integer, String, DateTime``  ``Base ``=` `declarative_base()  ``class` `UserInfo(Base):    ``    ``__tablename__ ``=` `'userinfo'``    ``    ``id` `=` `Column(Integer, primary_key``=``True``, autoincrement``=``True``) ``    ``name ``=` `Column(String(``64``), unique``=``True``) ``    ``ctime ``=` `Column(DateTime, default``=``datetime.now())`

SQLAchemy中如何为表设置引擎和字符编码？

SQLAchemy中如何设置联合唯一索引？

简述Tornado框架的特点。

简述Tornado框架中Future对象的作用？

Tornado框架中如何编写WebSocket程序？

Tornado中静态文件是如何处理的？ 如： <link href="{{static_url("commons.css")}}" rel="stylesheet" />

Tornado操作MySQL使用的模块？

Tornado操作redis使用的模块？

简述Tornado框架的适用场景？

git常见命令作用：

简述以下git中stash命令作用以及相关其他命令。

git 中 merge 和 rebase命令 的区别。

公司如何基于git做的协同开发？

如何基于git实现代码review？

git如何实现v1.0 、v2.0 等版本的管理？

什么是gitlab？

github和gitlab的区别？

如何为github上牛逼的开源项目贡献代码？

git中 .gitignore文件的作用?

### 什么是敏捷开发？

> 请参考这篇博文：http://www.cnblogs.com/taven/archive/2010/10/17/1853386.html

简述 jenkins 工具的作用?

公司如何实现代码发布？

简述 RabbitMQ、Kafka、ZeroMQ的区别？

RabbitMQ如何在消费者获取任务后未处理完前就挂掉时，保证数据不丢失？

RabbitMQ如何对消息做持久化？

RabbitMQ如何控制消息被消费的顺序？

以下RabbitMQ的exchange type分别代表什么意思？如：fanout、direct、topic。

简述 celery 是什么以及应用场景？

简述celery运行机制。

celery如何实现定时任务？

简述 celery多任务结构目录？

celery中装饰器 @app.task 和 @shared_task的区别？

简述 requests模块的作用及基本使用？

简述 beautifulsoup模块的作用及基本使用？

简述 seleninu模块的作用及基本使用?

scrapy框架中各组件的工作流程？

在scrapy框架中如何设置代理（两种方法）？

scrapy框架中如何实现大文件的下载？

scrapy中如何实现限速？

scrapy中如何实现暂定爬虫？

scrapy中如何进行自定制命令？

scrapy中如何实现的记录爬虫的深度？

scrapy中的pipelines工作原理？

scrapy的pipelines如何丢弃一个item对象？

简述scrapy中爬虫中间件和下载中间件的作用？

scrapy-redis组件的作用？

scrapy-redis组件中如何实现的任务的去重？

scrapy-redis的调度器如何实现任务的深度优先和广度优先？

简述 vitualenv 及应用场景?

简述 pipreqs 及应用场景？

在Python中使用过什么代码检查工具？

简述 saltstack、ansible、fabric、puppet工具的作用？

B Tree和B+ Tree的区别？

请列举常见排序并通过代码实现任意三种。

请列举常见查找并通过代码实现任意三种。

请列举你熟悉的设计模式？

有没有刷过leetcode？

列举熟悉的的Linux命令。

公司线上服务器是什么系统？

解释 PV、UV 的含义？

解释 QPS的含义？

uwsgi和wsgi的区别？

supervisor的作用？

什么是反向代理？

简述SSH的整个过程。

有问题都去那些找解决方案？

是否有关注什么技术类的公众号？

最近在研究什么新技术？

是否了解过领域驱动模型？

 







