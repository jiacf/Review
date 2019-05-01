## SplashRequest 构造方法

- url
  - 与scrapy.Request中的url相同，也就是待爬取页面的url（注意：不是Splash服务器的地址）
- headers
  - 与scrapy.Request中的headers相同
- cookies
  - 与scrapy.Request中的cookies相同
- args
  - 传递给Splash的参数（除url以外），如wait、timeout、images、js_source等
- cache_args
  - 如果args中的某些参数每次调用都重复传递并且数量较大（例如一段JavaScript代码），此时可以把该参数名填入cache_args列表中，让Splash服务器缓存该参数
- endpoint
  - Splash服务端点，默认为'render.html'，即Java