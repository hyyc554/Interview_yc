# 网络编程

## 1. 简述 OSI 七层协议。

- 为了实现计算机系统的互连，OSI参考模型把整个网络的通信功能划分为7个层次，同时也定义了层次之间的相互关系以及各层所包括的服务及每层的功能。
- OSI的七层由低到高依次为：物理层、数据链路层、网络层、传输层、会话层、表示层、应用层
- 下三层（物理层、数据链路层、网络层）面向数据通信
- 传输层则是七层中最为重要的一层，它位于上层和下层中间，起承上启下的作用。
- 上三层（会话层、表示层、应用层）则面向资源子网

![izUYSx.gif](https://s1.ax1x.com/2018/11/17/izUYSx.gif)

## 2. 什么是C/S和B/S架构？

C/S架构——客户端/服务器架构

B/S架构——浏览器/服务器架构

## 3. 简述三次握手、四次挥手的流程。
### 三次握手：
- 第一次握手：建立连接时，客户端发送syn包（syn=j）到服务器，并进入SYN_SENT状态，等待服务器确认；SYN：同步序列编号（Synchronize Sequence Numbers）。
- 第二次握手：服务器收到syn包，必须确认客户的SYN（ack=j+1），同时自己也发送一个SYN包（syn=k），即SYN+ACK包，此时服务器进入SYN_RECV状态；
- 第三次握手：客户端收到服务器的SYN+ACK包，向服务器发送确认包ACK(ack=k+1），此包发送完毕，客户端和服务器进入ESTABLISHED（TCP连接成功）状态，完成三次握手。
![VhLJ1J.gif](https://s2.ax1x.com/2019/06/13/VhLJ1J.gif)
### 四次挥手：

- 第一次挥手：客户端向服务器发送一个FIN报文段，将设置seq为160和ack为112，;此时，客户端进入 FIN_WAIT_1状态,这表示客户端没有数据要发送服务器了，请求关闭连接;

- 第二次挥手：服务器收到了客户端发送的FIN报文段，向客户端回一个ACK报文段，ack设置为1，seq设置为112;服务器进入了CLOSE_WAIT状态，客户端收到服务器返回的ACK报文后，进入FIN_WAIT_2状态; 
- 第三次挥手：服务器会观察自己是否还有数据没有发送给客户端，如果有，先把数据发送给客户端，再发送FIN报文；如果没有，那么服务器直接发送FIN报文给客户端。请求关闭连接，同时服务器进入LAST_ACK状态;
 
- 第四次挥手：客户端收到服务器发送的FIN报文段，向服务器发送ACK报文段，将seq设置为161，将ack设置为113，然后客户端进入TIME_WAIT状态;服务器收到客户端的ACK报文段以后，就关闭连接;此时，客户端等待2MSL后依然没有收到回复，则证明Server端已正常关闭，客户端也可以关闭连接了。
![VhLa0x.gif](https://s2.ax1x.com/2019/06/13/VhLa0x.gif)

## 4. 为什么TCP客户端最后还要发送一次确认呢？
一句话，主要防止已经失效的连接请求报文突然又传送到了服务器，从而产生错误。
如果使用的是两次握手建立连接，假设有这样一种场景，客户端发送了第一个请求连接并且没有丢失，只是因为在网络结点中滞留的时间太长了，由于TCP的客户端迟迟没有收到确认报文，以为服务器没有收到，此时重新向服务器发送这条报文，此后客户端和服务器经过两次握手完成连接，传输数据，然后关闭连接。此时此前滞留的那一次请求连接，网络通畅了到达了服务器，这个报文本该是失效的，但是，两次握手的机制将会让客户端和服务器再次建立连接，这将导致不必要的错误和资源的浪费。
如果采用的是三次握手，就算是那一次失效的报文传送过来了，服务端接受到了那条失效报文并且回复了确认报文，但是客户端不会再次发出确认。由于服务器收不到确认，就知道客户端并没有请求连接。

## 5. 什么是arp协议？

地址解析协议，即ARP（Address Resolution Protocol），是根据IP地址获取物理地址的一个TCP/IP协议。主机发送信息时将包含目标IP地址的ARP请求广播到网络上的所有主机，并接收返回消息，以此确定目标的物理地址；收到返回消息后将该IP地址和物理地址存入本机ARP缓存中并保留一定时间，下次请求时直接查询ARP缓存以节约资源。地址解析协议是建立在网络中各个主机互相信任的基础上的，网络上的主机可以自主发送ARP应答消息，其他主机收到应答报文时不会检测该报文的真实性就会将其记入本机ARP缓存；由此攻击者就可以向某一主机发送伪ARP应答报文，使其发送的信息无法到达预期的主机或到达错误的主机，这就构成了一个ARP欺骗。ARP命令可用于查询本机ARP缓存中IP地址和MAC地址的对应关系、添加或删除静态对应关系等。相关协议有RARP、代理ARP。NDP用于在IPv6中代替地址解析协议。

### TCP和UDP的区别？

UDP 是面向无连接的通讯协议，UDP 数据包括目的端口号和源端口号信息。
优点：UDP 速度快、操作简单、要求系统资源较少，由于通讯不需要连接，可以实现广播发送
缺点：UDP 传送数据前并不与对方建立连接，对接收到的数据也不发送确认信号，发送端不知道数
据是否会正确接收，也不重复发送，不可靠 。

TCP 是面向连接的通讯协议，通过三次握手建立连接，通讯完成时四次挥手
优点：TCP 在数据传递时，有确认、窗口、重传、阻塞等控制机制，能保证数据正确性，较为可靠。
缺点：TCP 相对于 UDP 速度慢一点，要求系统资源较多 

### 什么是局域网和广域网？

为何基于tcp协议的通信比基于udp协议的通信更可靠？

什么是socket？简述基于tcp协议的套接字通信流程。

什么是粘包？ socket 中造成粘包的原因是什么？ 哪些情况会发生粘包现象？

### IO多路复用的作用？



下面举一个例子，模拟一个tcp服务器处理30个客户socket。假设你是一个老师，让30个学生解答一道题目，然后检查学生做的是否正确，你有下面几个选择：

1. 第一种选择：按顺序逐个检查，先检查A，然后是B，之后是C、D。。。这中间如果有一个学生卡主，全班都会被耽误。这种模式就好比，你用循环挨个处理socket，根本不具有并发能力。

2. 第二种选择：你创建30个分身，每个分身检查一个学生的答案是否正确。 这种类似于为每一个用户创建一个进程或者线程处理连接。

3. 第三种选择，你站在讲台上等，谁解答完谁举手。这时C、D举手，表示他们解答问题完毕，你下去依次检查C、D的答案，然后继续回到讲台上等。此时E、A又举手，然后去处理E和A。。。 这种就是`IO复用模型`，Linux下的select、poll和epoll就是干这个的。

   将用户socket对应的fd注册进epoll，然后epoll帮你监听哪些socket上有消息到达，这样就避免了大量的无用操作。此时的socket应该采用非阻塞模式。

   这样，整个过程只在调用select、poll、epoll这些调用的时候才会阻塞，收发客户消息是不会阻塞的，整个进程或者线程就被充分利用起来，这就是事件驱动，所谓的reactor模式。

> 作者：柴小喵
> 链接：https://www.zhihu.com/question/28594409/answer/52835876
> 来源：知乎
> 著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。



### 什么是防火墙以及作用？

select、poll、epoll 模型的区别？

简述 进程、线程、协程的区别 以及应用场景？

GIL锁是什么鬼？

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