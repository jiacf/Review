## time库

#### 处理时间是程序最常用的功能之一，time是Python提供的处理时间标准库。time库提供系统级精确计时器的计时功能，可以用来分析程序性能，也可以让程序暂停运行时间。

#### 时间处理主要包括4个函数：time.time(),time.gmtime(),time.localtime(),time.clime()

#### 时间格式化主要包含3个函数：

#### time.mktime()、time.strftime()、time.strptime

#### 计时主要包含3个函数：

#### time.sleep()、time.monotonic()、time.perf_counter()

- time.time()
  - 作用：获取当前时间戳
- time.gmtime(now)
  - 作用：获取当前时间戳对应的struct_time对戏那个
- time.localtime(now)
  - 作用：获取当前时间戳对应的本地时间的struct_time对象
- time.ctime(secs)
  - 作用：获取当前时间戳对应的易读字符串表示，内部会调用time.localtime()函数以输出当前时间