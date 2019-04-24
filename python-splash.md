## Splash 对象属性

- args

  - 该属性可以获取加载时配置的参数，比如URL，如果为GET请求，它还可以获取GET请求参数；如果为POST请求，它可以获取表单提交的数据。Splash也支持使用第二个参数直接作为args
  
    - ```lua
      function main(splash,args)
        	local url = args.url
      end
      ```
  
      等价于
  
      ```lua
      function main(splash)
        	local url = splash.args.url
      end
      ```
  
- js_enabled

  - 这个属性是Splash的javaScript执行开关，可以将其配置为true或false来控制是否执行javaScript代码，默认为true
  
    - ```lua
      splash.js_enabled = true/false
      ```
  
      
  
- resource_timeout

  - 此属性可以设置加载的超时时间，单位是秒。如果设置为0或nil，则表示不检测超时

    - ```lua
      splash.resource_timeout = 0.1
      ```

      

- image_enabled

  - 此属性可以设置图片是否加载，默认情况是加载的

    - ```lua
      splash.image_enabled = true/false
      ```

      

- plugins_enabled

  - 此属性可以控制浏览器插件(如Flash插件)是否开启，默认是false

    - ```lau
      splash.plugins_enabled = true/false
      ```

      

- scroll_position

  - 此属性可以控制页面上下或左右滚动

    - ```lua
      splash.scroll_position = {y=400,x=300}
      ```

## Splash 对象的方法

- go()

  - 该方法用来请求某个连接，而且它可以模拟GET或POST请求，同时支持传入请求头、表单等数据

  - ```lua
    splash:go{url,baseurl=nil,headers=nil,http_method="GET",body=nil,formdata=nil}
    ```

    - url: 请求的URL
    - baseurl：可选参数，默认为空，表示资源加载相对路径
    - headers：可选参数，默认为空，表示请求头
    - http_method：可选参数，默认为GET，同时支持POST
    - body：可选参数，默认为空，发POST请求时的表单数据，使用的Content-type为application/json
    - formdata：可选参数，默认为空，POST的时候的表单数据，使用的Content-type为application/x-www-form-urlencoded
  
- wait()

  - 此方法可以控制页面的等待时间

  - ```lua
    splash:wait{time,cancel_on_redirect=false,cancel_on_error=true}
    ```

    - time : 等待的秒数
    - cancel_on_redirect : 可选参数，默认为false，如果为true，表示如果发生了重定向就停止等待，并返回重定向结果
    - cancel_on_error : 可选参数，默认为true，表示如果发生了加载错误，就停止等待

- jsfunc()

  - 此方法可以直接调用JavaScript定义的方法，但是所调用的方法需要用双中括号包围，这相当于实现了JavaScript方法到Lua脚本的转换

    

    

- evaljs()

  - 此方法可以执行JavaScript代码并返回最后一条JavaScript语句的返回结果

- runjs()

  - 次方法可以执行JavaScript代码，它与evaljs()功能类似，但是更偏向于执行某些动作或生命某些方法

- autoload()

  - 此方法可以设置每个页面访问时自动加载的对象，但是此方法只负责加载JavaScript代码或库，不执行任何操作。如果要执行操作，可以调用evaljs()或runjs()方法

  - ```
    aplash:autoload{source_or_url,source=nul,url=nil}
    ```

    - source_or_url : JavaScript代码或者JavaScript库链接
    - source ： JavaScript代码
    - url ： JavaScript库链接

- call_later()

  - 此方法可以通过设置定时任务和延迟时间来实现任何延迟执行，并且可以在执行前通过cancel()方法重新执行定时任务