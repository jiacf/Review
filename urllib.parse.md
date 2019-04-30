## urllib.parse

- urllib.parse模块，它定义了处理URL的标准接口，例如实现URL各部分的抽取、合并以及链接转换。它支持如下协议的URL处理：file、ftp、gopher、hdl、http、https、imap、mailto、mms、news、nntp、prospero、rsync、rtsp、rtspu、stfp、sip、sips、snews、svn、svn+ssh、telnet和wais

  - urlparse()

    - 该方法可以实现URL的识别和分段

      ```python
      urllib.parse.urlparse(urlstring,scheme='',allow_fragments=True)
      ```

      - urlstring：这是必填项，即待解析的URL
      - scheme：它是默认的协议(比如http或https等)。假如这个链接没有带协议信息，会将这个作为默认协议
      - allow_fragments：即是否忽略fragment。如果它被设置为False，fragment部分就会被忽略，它会被解析为path、parameters或query的一部分，而fragment部分为空

    - 返回结果是一个ParseResult类型的对象，它包含6个部分，分别是scheme、netloc、path、params、query和fragment。

      - Scheme:代表协议
      - netloc：代表域名
      - path：访问路径
      - params：代表参数
      - query：？后面的是查询条件，一般用作GET类型的URL
      - fragment：#后面的是锚点，用于直接定位页面内部的下拉位置

  - urlunparse()
    - urlparse()对立方法urlunparse(),它接受的参数是一个可迭代对象，但是它的长度必须是6，否则会抛出参数数量不足或过多的问题
  - urlsplit()
    - 类似于urlparse()方法，只不过它不再单独解析params这一部分，只返回5

