# HTML

**一、HTML5新增内容**

- 新语义化标签：header、footer、nav、section、aside、article、main、figure
- 新增input类型：color、url、email、date、week、time、number、range、search、tel
- 新增表单控件属性：placeholder/设置文本框默认提示文字、autofocus/自动获得焦点、autocomplete/联想关键词
- 存储：提供了sessionStorage、localStorage和本地离线存储（使用manifest配置文件）
- 多媒体：音频元素audio、视频元素vedio、source、embed
- 地理定位、canvas画布、拖放API、多线程编程的webworker、websocket协议

**二、Doctype有什么作用？有哪几种模式？**

Doctype声明在文档的最前面，告诉浏览器以哪种方式来渲染页面：

严格模式：排版和JS运作模式是以该浏览器支持的最高标准运行的  
混杂模式：向后兼容，模拟老式浏览器，防止浏览器无法兼容页面

**三、什么是iframe？有什么缺点？**

iframe元素会创建包含另一文档的内联框架

缺点：

- 会阻塞主页面的onload事件
- 搜索引擎无法解读这种页面
- 主页面和iframe共享连接池，而浏览器对相同区域有限制，所以会影响性能

**四、什么是WebSocket？有什么特点？**

WebSocket是HTML5中新增的协议，支持持久性连接，解决了HTTP协议通信只能由客户端发起的缺陷。

特点：  

- 服务器可以主动向客户端发送信息，客户端也可以主动向服务器发送信息，实现了双向平等对话
- 建立在TCP协议之上，服务端的实现比较容易
- 与HTTP协议有着良好的兼容性。默认端口也是80和443，握手阶段采用HTTP协议，因此不容易屏蔽，且能通过各种HTTP代理服务器
- 数据格式（帧）比较轻量，性能开销小，通信效率高
- 可以发送文本或二进制数据
- 无同源限制，客户端可以与任意服务器通信
- 协议标识符是ws（加密则为wss），服务器网址就是URL

参考：[WebSocket协议：5分钟从入门到精通](https://www.cnblogs.com/chyingp/p/websocket-deep-in.html)

**五、WebSocket连接如何建立？**

客户端通过http请求与WebSocket服务端协商升级协议，协议升级完成后，后续的数据交换遵照WebSocket的协议。

1. 客户端申请协议升级，采用标准HTTP报文格式，且只支持GET方法

   请求首部：

   Connection: Upgrade 表示要升级协议

   Upgrade: websocket 表示要升级到websocket协议

   Sec-WebSocket-Version 表示websocket版本

   Sec-WebSocket-Key 与后续服务端响应首部Sec-WebSocket-Accept配套，提供基本的防护，如恶意的连接或无意的连接

2. 服务端响应协议升级，返回如下内容，状态代码101表示协议切换。至此完成协议升级，后续的数据交互都按照新协议来

   Connection: Upgrade 

   Upgrade: websocket 

   Sec-WebSocket-Accept 根据Sec-WebSocket-Key计算

**六、HTML5的拖放API**

在HTML5之前，如果要实现拖放效果，一般会使用mousedown、mousemove和mouseup三个事件进行组合来模拟出拖拽效果，比较麻烦。而HTML5规范实现了原生拖放功能，使得元素拖放的实现更加方便和高效。

- dragstart：事件主体是被拖放元素，在开始拖放被拖放元素时触发
- drag：事件主体是被拖放元素，在正在拖放被拖放元素时触发
- dragenter：事件主体是目标元素，在被拖放元素进入目标元素时触发
- dragover：事件主体是目标元素，在被拖放元素在目标元素内移动时触发
- dragleave：事件主体是目标元素，在被拖放元素移出目标元素时触发
- drop：事件主体是目标元素，在目标元素完全接受被拖放元素时触发
- dragend：事件主体是被拖放元素，在整个拖放操作结束时触发