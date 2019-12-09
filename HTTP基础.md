##HTTP基础

- HTTP(Hyper Text Transfer Protocol)
  - 超文本传输协议，是用于从网络传输超文本数据到本地浏览器的传送协议,是由"W3C"和"IETF"共同合作制定的规范
- W3C(World Wide Web Consortium)
  - 万维网联盟，是万维网的主要国际标准组织
- IETF(Internet Engineering Task Force)
  - Internet工程任务小组，负责互联网标准的开发和推动
- HTTPS(Hyper Text Transfer Protocol over Secure Socket Layer)
  -  是以安全为目标的HTTP通道，简单讲是HTTP的安全版，即HTTP下加入SSL层

## 网页请求头详细信息

- Accept
  - 请求报头域，用于指定客户端可接受哪些类型的信息
-  Accept-Language
  - 指定客户端可接受的语言类型
- Accept-Encoding
  - 指定客户端可接受的内容编码
- Host
  - 用于指定请求资源的主机IP和端口号，其内容为请求URL的原始服务器或网关的位置
- Cookie
  - 这是网站为了辨别用户进行会话跟踪而存储在用于本地的数据。它的主要功能是维持当前访问会话
- Referer
  - 此内容用来标识这个请求是从哪个页面发过来的，服务器可以拿到这一信息并做相应的处理，如做来源统计、防盗链处理等
- User-Agent
  - 它是一个特殊的字符串头，可以使服务器识别客户使用的操作系统及版本、浏览器及版本等信息
- Content-Type
  - 也叫互联网媒体类型（Internet Media Type）或MIME类型，在HTTP协议消息头重，它用来表示具体请求中的媒体类型信息