
# mongodb 安装      
      
      
1.安装：[下载mogodb](https://www.mongodb.com/download-center#community)


2.创建数据库 
```
   cd c:\  (进入c盘根路径）
   mkdir data (创建文件夹data)
   cd data    (进入文件夹)
   mkdir db   (创建文件夹db)
 ```
3.连接数据库服务器
```
   进入 C:\Program Files\MongoDB\Server\3.4\bin
   
   注意：   mongod  服务器的可执行文件
            mongo   客户端的可执行文件

  

  mongod --dbpath=c:/mongodb/db --port 27017  启动数据库服务器跑在27017端口上

  mongo  连接数据库服务器

  show dbs  查看数据库
  
  ```

4.创建服务器配置
```
  cd c:\data   (进入data目录)  
  
  mkdir etc     (创建etc目录)
  cd etc        (进入etc目录)
  type nul>mongo.conf  (创建空文件mongo.conf)     
  
  //将以下内容复制到 mongo.conf 文件中
  
             #数据库路径
            dbpath=c:\data\db\
            #日志输出文件路径
            logpath=c:\data\log\mongodb.log
            #错误日志采用追加模式，配置这个选项后mongodb的日志会追加到现有的日志文件，而不是从新创建一个新文件
            logappend=true
            #启用日志文件，默认启用
            journal=true
            #这个选项可以过滤掉一些无用的日志信息，若需要调试使用请设置为false
            quiet=false
            #端口号 默认为27017
            port=27017
```
  5.创建日志文件
  ```
   cd c:\data   (进入data目录)  
   md log    (创建目录log)
   cd log    (进入目录log)
   type nul>mongodb.log  （创建日志文件mongodb.log）
  
   以上操作形成如下目录结构
   
   data  数据库目录
    -----db 数据库文件
    -----etc 数据库配置文件 
            -----mongo.conf
    -----log 数据库日志    
            -----mongodb.log
```
  6. 启动数据库服务器   
```
    C:\Program Files\MongoDB\Server\3.4\bin

    mongod --config c:/mongodb/etc/mongo.conf       启动后无任何反应
```
   7. 连接数据库

     mongo 


-------------------------------------------------------------------------------------------------------
# mongodb 终端操作

```

 mongodb 增删改查

 启动：mongod --config e:\mongodb\etc\mongod.conf
 连接：mongo

--------增---------------
 use demo   创建demo数据库
 show dbs   看不到
 db.createCollection('user') 创建user集合
 show collections  查看集合  show tables 相同
 db.user.insert({name:'张三',age:20})   创建users 集合 并插入一条文档
 db.user.insert([{name:'张三',age:20},{name:'李四'，age:30}])  插入多条文档
 
------------删--------------------
db.dropDatabase() ;删除当前所在数据库
db.user.drop() 删除集合
db.user.remove({name:'张三'});删除name为张三的文档     参数 {} 删除所有


--------------查-------------------
show dbs 查询数据库
show collections 查询当前数据库下的集合   也可 show tables
db.user.find(); 查询所有  想格式化 .pretty()
db.user.findOne();查询第一条  
db.user.find().count(); 查询集合文档条数
 db.user.find({"_id": ObjectId("584bc73ea635e489676cf5db")})   根据id查询数据

db.user.find({age:{$gt:20}});查询年龄大于20的  $lt  $eq   $lte
db.user.find({'age':{$gt:20,$lt:30}})
db.user.find({$or:[{'name':'lv'},{'name':'chen'}]})  $or选择器
db.user.find({'name':{$ne:'lv'}});    $ne不等于
-------改-------------------------------------------
db.user.update({name:"张三"}，{$set:{age:25}}) 更新数据： (只改第一条）
db.user.update({name:"张三"}，{$set:{age:25}},{multi: true})  更新数据： (匹配到的所有）
db.user.update({name:"张三"}，{$set:{'class.age':25}})
---------------------------------------------------
```
