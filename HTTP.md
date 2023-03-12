# HTTP

[article](https://mp.weixin.qq.com/s?__biz=MzUxODAzNDg4NQ==&mid=2247483971&idx=1&sn=8f2d5dae3d95efc446061b352c8e9961&chksm=f98e46e9cef9cfff1f6bee1974b8dc27dcc42f0627dcf8ff0c0df8dbaa7a1f74587e3fafc167&scene=178&cur_album_id=1337204681134751744#rd)

![image-20230305093737478](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20230305093737478.png)

- **HTTP状态码：**
  - 1xx 提示信息，表示目前是协议处理的中间状态
  - 2xx 成功，报文已经收到并被正确处理
  - 3xx 重定向，资源位置发生变动，需要客户端重新发送请求
  - 4xx 客户端错误，请求报文有误，服务器无法处理
  - 5xx 服务器错误，服务器在处理请求时内部发生了错误
- **优缺点**
  - 优点
    - 简单 
    - 灵活和易拓展
    - 应用广泛和跨平台
  - 缺点
    - 无状态双刃剑
    - 明文传输双刃剑
    - 不安全
- **HTTP性能**
  - 长连接
  - 管道传输协议
  - 队头阻塞
- **HTTPS对比HTTP解决了（加入了SSL/TLS协议）**
  - 信息加密
  - 校验机制
  - 身份证书
- **HTTP/2 优点**
  - 头部压缩
  - 二进制格式
  - 数据流
  - 多路复用
  - 服务器推送



# TCP

<img src="https://mmbiz.qpic.cn/mmbiz_png/J0g14CUwaZeo9xBVAyPJ8iaWCC6sYS843ZPb6tFLvCVuXEn98khfs7y2KRvOV0ia5icVByzIK3aAKRURuVZKagsKw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1" alt="图片" style="zoom: 50%;" />

<img src="https://mmbiz.qpic.cn/mmbiz_png/J0g14CUwaZeo9xBVAyPJ8iaWCC6sYS843tzTAWL4l6rZB0pulNqkLno7buMqnh5Hlphn7aibB798ga1t3a0Dqmzg/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1" alt="图片" style="zoom: 67%;" />



- TCP是面向连接的、可靠的、基于字节流的传输层通信协议
- TCP是工作在传输层的可靠数据传输的服务，它能确保接受端接受的网络包是无损坏、无间隔、非冗余和按序的
- 使用TCP四元组可以唯一地确定一个连接
  - 源地址
  - 源端口
  - 目的地址
  - 目的端口

<img src="https://mmbiz.qpic.cn/mmbiz_png/J0g14CUwaZeo9xBVAyPJ8iaWCC6sYS8431Mymq2yPGjMPGodSEg8b31eoyQbibzGjDEHiaQUUDlbvCEwcXN3aicOTw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1" alt="图片" style="zoom:67%;" />

<img src="https://mmbiz.qpic.cn/mmbiz_png/J0g14CUwaZeo9xBVAyPJ8iaWCC6sYS8436nKau10lAsztRqbyhjC1C1GRcsEz04icZmomMjwcxgeGn97BnKUoxibw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1" alt="图片" style="zoom: 50%;" />



- **为什么三次握手才可以初始化Socket、序列号和窗口大小并建立 TCP 连接。**
  - 三次握手才可以阻止历史重复连接的初始化（主要原因）
  - 三次握手才可以同步双方的初始序列号
  - 三次握手才可以避免资源浪费
- **不使用「两次握手」和「四次握手」的原因：**
  - 「两次握手」：无法防止历史连接的建立，会造成双方资源的浪费，也无法可靠的同步双方序列号
  - 「四次握手」：三次握手就已经理论上最少可靠连接建立，所以不需要使用更多的通信次数

<img src="https://mmbiz.qpic.cn/mmbiz_png/J0g14CUwaZeo9xBVAyPJ8iaWCC6sYS843KaMMu2mHfFLZNgiaREDZ5JicRYrlaiciayQjh9HDsacxIbMT0emGUpAX5w/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1" alt="图片" style="zoom:50%;" />



# IP

<img src="https://mmbiz.qpic.cn/mmbiz_png/J0g14CUwaZdpI5tWwB8wMfZQ8ichJW1yu3u9AgedCb0tFU7W1fZlqG0ImZVnIoAan7z2vX71WYeKZz1waagqoXw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1" alt="图片" style="zoom: 67%;" />















































