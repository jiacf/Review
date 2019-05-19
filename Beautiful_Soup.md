## 

|  Python标准库   |              使用方法              |                           优势                            |                       劣势                       |
| :-------------: | :--------------------------------: | :-------------------------------------------------------: | :----------------------------------------------: |
|  Python标准库   | BeautifulSoup(markup,"html.parse") |     Python的内置标准库、执行速度适中、文档容错能力强      | Python2.7.3及Python3.2.2之前的版本文档容错能力差 |
| lxml HTML解析库 |    BeautifulSoup(markup,"lxml")    |                  速度快、文档容错能力强                   |                 需要安装C语言库                  |
| lxml XML解析库  |    BeautifulSoup(markup,"xml")     |                速度快、唯一支持XML的解析库                |                 需要安装C语言库                  |
|    html5lib     |  BeautifulSoup(markup,"html5lib")  | 最好的容错性、以浏览器的方式解析文档、生成HTML5格式的文档 |              速度慢、不依赖外部扩展              |

