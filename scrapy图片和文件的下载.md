##  scrapy 文件和图片的下载

|          |            FilesPipeline             |             ImagesPipeline             |
| :------: | :----------------------------------: | :------------------------------------: |
| 导入路径 | scrapy.pipelines.files.FilesPipeline | scrape.pipelines.images.ImagesPIpeline |
| Item字段 |           File_urls,files            |           Image_urls,images            |
| 下载目录 |             FILES_STORE              |              IMAGES_STORE              |

* FilesPipeline

  * FIlesPipeline下载完items['file_urls']中所有的文件后，会将各文件的下载结果信息收集到另一个列表，赋值给item的files字段，
  * files详细信息
    * Path文件下载到本地的路径(相当于FILES_STORE的相对路径)
    * Checksum文件校验和
    * url文件的url地址

* ImagesPipelineu

  * 在settings.py中将图片生成缩略图

    * ```python
      IMAGES_THUMBS = {
        'small':(50,50),
        'big':(270,270),
      }
      ```

      开启该功能后，下载一张图片时，本地会出现3张图片(1张原图，2张缩略图)

  * 在settings.py过滤尺寸过小的图片

    * ```python
      IMAGE_MIN_WIDTH = 110
      IMAGE_MIN_HEIGHT = 110
      ```

      这两项分别可以指定图片最小的宽和高，如果图片的宽高不符合标准的话会被抛弃