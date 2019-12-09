## Request的属性解释
* * `Request(url,[,callback,method="GET",headers,body,cookies,meta,encoding="utf-8",priority=0,dont_filter=False,errback])`
  * **url**	
    * 请求页面的url地址，bytes或str类型。
  * **callback**    
    * 页面解析函数，Callable类型，Request对象请求的页面下载完成后，由该参数指定的页面解析函数被调用。如果未传递该参数，默认调用Spider的parse方法
  * **method**   
    *  HTTP请求的方法，默认为“GET”
  * **headers**    
    * HTTP请求的头部自定，dict类型，如果其中某项的值为None，就代表不发送该项HTTP头部。
  * **body**    
    * HTTP请求正文，bytes或str类型
  * **cookies**    
    * Cookie信息字典，dict类型
  * **meta**    
    * Request的元数据字典，dict类型，用于给框架中其他组件传递信息，比如中间件Item Pipeline，其他组件可以使用Request对象的meta属性访问该元数据字典(request.meta),也用于给相应处理函数传递信息
  * **encoding**    
    * url和body参数的编码类型，默认为“utf-8”
  * **prioity**    
    * 请求的优先级默认值为0，优先级高的请求优先下载
  * **dont_filter**    
    * 默认情况下(dont_filter=False)，对同一个url地址多次提交下载请求，后面的请求会被去重过滤器过滤，如果将该参数设置为True，可以使请求避免过滤，强制下载。
  * **errback**    
    * 请求出现异常或出现HTTP错误是的回调函数

## Response的属性和方法

* **url**
  * **HTTP**响应的url地址，str类型
* **status**
  * **HTTP**响应的状态码，int类型
* **headers**
  * **HTTP**响应头部，类字典类型，可以调用get或getlist方法对其进行访问
* **body**
  * **HTTP**响应正文，bytes类型
* **text**
  * 解码后的**HTTP**响应正文，str类型
* **encoding**
  * **HTTP**响应正文的编码，它的值可能是从HTTP响应头部或正文中解析出来的
* **request**
  * 产生该**HTTP**响应的Request对象
* **meta**
  * response.request.meta,在构造Request对象时，可将要传递给响应处理函数的信息通过meta参数传入；响应处理函数响应时，通过response.meta将信息取出
* **selector**
  * 选择器对象，用于在Response中提取数据
* **urljoin**
  * 用于构造绝对url。当传入的url参数是一个相对url时，根据response.url计算出绝对url



