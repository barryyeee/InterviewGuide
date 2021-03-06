# TCP握手挥手

首先，来认识一下握手挥手中用到的一些标识位和缩写的含义：

- SYN：标识位，表示建立链接
- ACK：标识位，表示响应
- FIN：标识位，表示关闭链接
- seq：顺序号码（TCP连接中传送的字节流中的每个字节都按顺序编号）
- ack：确认号码，是期望收到对方下一个报文的第一个数据字节的序号

TCP三次握手：客户端和服务器都需要知道双方可收发，因此需要三次握手（让我知道你已经知道了）  
![](\Images\TCP握手.png)  TCP客户端最后还要发送一次确认的目的：防止已经失效的连接请求报文突然又传送到服务器，从而导致不必要的错误和资源的浪费。

TCP四次挥手：  
![](\Images\TCP挥手.png)  TCP客户端最后还要等待2*MSL（最长报文段寿命）的目的：保证客户端发送的最后一个ACK报文能够达到服务器；防止已经失效的关闭连接报文段出现在本连接中。

Q1：如果已经建立了连接，但客户端突然出现故障怎么办？

TCP设有一个保活计时器，服务器每收到一次客户端的请求后都会重新复位这个计时器，时间通常设置为2h，若2h之内还没有收到客户端的任何数据，服务器就会发送一个探测报文，之后每隔75s发送一次。若连续发送10个探测报文仍没有回应，服务器就认为客户端出现故障，接着就关闭连接。

Q2：为什么建立连接是三次握手，关闭连接是四次挥手？

建立连接的时候，服务器出于监听状态，一旦收到客户端建立连接请求的SYN报文后，可直接将SYN和ACK放在一个报文中返回客户端。

而关闭连接时，服务器收到客户端关闭连接的FIN报文时仅仅表示对方不再发送数据但仍能接受数据，而自己的数据也未必全部发送给对方了，所以此时发送完数据给对方后，再向客户端发送FIN报文来表示同意现在关闭连接，ACK和FIN的分开发送导致挥手比握手多了一次。



参考：[两张动图-彻底明白TCP的三次握手与四次挥手](https://blog.csdn.net/qzcsu/article/details/72861891)（这篇博客讲的非常好，大家可以看看原文加深理解）