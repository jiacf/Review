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
    splash:go(url,baseurl=nil,headers=nil,http_method="GET",body=nil,formdata=nil)
    ```

    - url: 请求的URL
    - baseurl：可选参数，默认为空，表示资源加载相对路径
    - headers：可选参数，默认为空，表示请求头
    - http_method：可选参数，默认为GET，同时支持POST
    - body：可选参数，默认为空，发POST请求时的表单数据，使用的Content-type为application/json
    - formdata：可选参数，默认为空，POST的时候的表单数据，使用的Content-type为application/x-www-form-urlencoded
  
  