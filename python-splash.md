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
  
- http_get()

  - 此方法可以模拟发送HTTP的GET请求

  - ```lua
    splash:http_get{url,headers=nil,follow_redirects=true}
    ```

    - url : 请求URL
    - headers：可选参数，默认为空，请求头
    - follow_redirects：可选参数，表示是否启动自动重定向，默认为true

- http_post()

  - 此方法用来模拟发送POST请求，不过多了一个参数body

  - ```
    splash：http_post{url,headers=nil,follow_redirects=true,body=nil}
    ```

    - url：请求URL
    - headers：可选参数，默认为空，请求头
    - follow_redirects：可选参数，表示是否启动自动重定向，默认为true
    - body：可选参数，即表单数据，默认为空

- set_content()

  - 此方法用来设置页面的内容

- html()

  - 此方法用来获取网页的源代码，它是非常简单又常用的方法

- png()

  - 此方法用来获取PNG格式的网页截图

- jpeg()

  - 此方法用来获取GPEG格式的网页截图

- har()

  - 此方法用来获取页面加载过程描述

- url()

  - 此方法可以获取当前正在访问的URL

- get_cookies()

  - 此方法可以获取当前页面的Cookies

- add_cookies()

  - 此方法可以为当前页面添加Cookie

  - ```lua
    splash:add_cookies{name,value,path=nil,domin=nil,httpOnly=nil,secure=nil}
    ```

- clear_cookies()

  - 此方法可以清除所有的Cookies

- get_viewport_size()

  - 此方法可以获取当前浏览器页面的大小，即宽高

- set_viewport_size()

  - 此方法可以设置当前浏览器页面的大小，即宽高

- set_viewport_full()

  - 此方法可以设置浏览器全屏显示

- set_user_agent()

  - 此方法可以设置浏览器的User_Agent

- set_custom_headers()

  - 此方法可以设置请求头

- select()

  - 该方法可以选中符合条件的第一个节点，如果有多个节点符合条件，则只会返回一个，其参数是CSS选择器

- select_all()

  - 此方法可以选中所有符合条件的节点，其参数是CSS选择器

- mouse_click()

  - 此方法可以模拟鼠标点击操作，传入的参数为坐标值x和y。此外，也可以直接选中某个节点，然后调用此方法


## Splash API调用

- render.html

  - 此接口用于获取JavaScript渲染的页面的HTML代码

  - 'http://localhost:8050/render.html?url=https://www.baidu.com'

    

  - |   参数    | 是否必选 |  类型   |                     描述                     |
    | :-------: | :------: | :-----: | :------------------------------------------: |
    |    url    |   必选   | string  |              需要渲染页面的url               |
    |  timeout  |   可选   |  float  |               渲染页面超时时间               |
    |   proxy   |   可选   | string  |                代理服务器地址                |
    |   wait    |   可选   |  float  |               等待页面渲染时间               |
    |  images   |   可选   | integer |            是否下载图片，默认为1             |
    | js_source |   可选   | string  | 用户自定义的JavaScript代码，在页面渲染前执行 |

    

- render.png

  - 此接口可以获取网页截图，其参数比render.html多了几个，例如可以通过width和height来控制宽高，返回的是PNG格式的图片二进制数据

- render.jpeg

  - 此接口和render.png类似，不过它返回的是JPEG格式的图片二进制数据，此接口比render.png多了一个quality参数，可以用来设置图片质量

- render.har

  - 此接口用于获取页面加载的HAR数据，返回的是一个JSON格式的数据，其中包含页面加载过程中的HAR数据

- render.json

  -  此接口包含了前面接口的所有功能，返回结果是JSON格式