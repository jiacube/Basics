### http协议

* 请求报文

![请求报文](images/request.png)

* 响应报文

![响应报文](images/response.png)

### Cookie

### TCP/IP
* IP(Internet Protocol)：根据网络情况，将要传输的数据，分为不同大小的包、固定的格式，在源地址和目的地址之间传递。
* TCP(Transmission Control Protocol)：一种面向连接的、可靠的、基于字节流的传输层的传输通信协议。
* TCP首部6个标志比特位

URG：紧急指针

ACK：确认序号有效

PSH：尽可能快地将数据送往接收进程

RST：重建连接

SYN：同步序号用来发起一个连接

FIN：发端完成发送任务

* TCP和UDP的区别

TCP是有连接的，两台主机在进行数据交互之前必须通过三次握手建立连接；而UDP是无连接的，没有建立连接整个过程。

TCP是可靠的传输，TCP协议通过确认和重传机制来确保数据传输的可靠性；而UDP是不可靠传输。

TCP提供了拥塞控制、滑动窗口等机制来保证传输的质量，而UDP是不可靠的传输。

TCP是基于字节流的，将数据看做无结构的字节流进行传输，当应用程序交给TCP的数据长度太长，超过MSS时，TCP就会对数据进行分段，因此TCP的数据是无边界的；UDP是面向报文的，无论应用程序交给UDP层多长的报文，UDP都不会对数据报进行任何拆分等处理，因此UDP保留了应用层数据的边界。

### TCP/IP四层模型和OSI七层模型

![TCP/IP四层模型和OSI七层模型](images/layer.png)

### 三次握手四次挥手

![三次握手四次挥手](images/hand.png)

### 缓存

### 状态码

200 OK   204 No Content

301 Moved Permanently   302 Move temporarily   304 Not Modified

400 Bad Request   401 Unauthorized   403 Forbidden   404 Not Found   405 Method Not Allowed

500 Internal Server Error   502 Bad Gateway   503 Service Unavailable   504 Gateway Timeout   505 HTTP Version Not Supported

### 方法

GET、POST、PUT、DELETE、HEAD

* GET和POST的区别

### 跨域

### 浏览器输入URL到页面显示整个过程发生了什么
*加载过程*
* 浏览器根据DNS服务器解析得到域名的IP地址
* 向这个IP的机器发送HTTP请求
* 服务器收到、处理并返回HTTP请求
* 浏览器得到返回内容

*渲染过程*

* 根据HTML结构生成DOM树
* 根据CSS生成CSSOM
* 将DOM和CSSOM整合成Render Tree
* 根据Render Tree开始渲染和展示
* 遇到script时，会执行并阻塞渲染
