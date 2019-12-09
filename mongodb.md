MAC 启动、停止和重启mongodb命令

- MAC 启动、停止和重启mongodb命令

  - ```
    brew serives start mongodb
    brew services stop mongodb
    brew services restart mongodb
    ```

    

- Python下操作MongoDB数据

  - 通过python连接到MongoDB数据库并指定数据库和集合

  - ```python
    import pymongo
    #传入MongoDB的IP及端口即可，其中第一个参数为地址host，第二个参数为端口port(默认为27017)
    client = pymongo.MongoClient(host='localhost',port=27017)
    #直接传入MOngoDB连接字符串也可以达到相同的效果
    clinet = pymongo.MongoClient('mongodb://localhost:27017')
    #指定要使用的数据库
    db = client.text
    db = client['text'] #这两种指定数据库的方法效果是一样的
    #指定要使用的集合
    collection = db.students
    collection = db['students']  #这两种指定集合的方法效果是一样
    ```

  - 插入数据

    ```python
    #插入单条数据可以使用insert_one()方法
    student = {'id':111111,
              'name':'aaabbcc',
              'age':20,
              'gender':11222}
    result = collection.insert_one(student)	#返回的结果是InsertOneResult对象
    result.inserted_id	#可以调用inserted_id属性获取_id
    
    #插入多条数据可以使用insert_many()方法
    student = {'id':111111,
              'name':'aaabbcc',
              'age':20,
              'gender':11222}
    student1 = {'id':111111,
              'name':'aaabbcc',
              'age':20,
              'gender':11222}
    result = collection.insert_many([student,student1])	#可以将数据以列表的形式进行传入，返回的结果是InserManyResult
    result.inserted_ids	#调用inserted_ids属性可以获取插入数据的_id列表
    ```

  - 查询数据

    ```
    
    ```

    