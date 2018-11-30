
# mongodb 安装      
      
      
1.安装：[下载mogodb](https://www.mongodb.com/download-center#community)

> 添加环境变量
```
在环境变量PATH中加入 “C:\Program Files\MongoDB\Server\3.4\bin>“

```


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

  
  (第一种方法)
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
    （第二种方法）
    mongod --config c:/mongodb/etc/mongo.conf       启动后无任何反应
```
   7.以Windows服务器运行MongoDB
     以管理员方式打开CMD窗口，运行如下命令安装MongoDB服务，
     然后按下 window+R 键 在运行栏目输入：services.msc 找到名为“MongoDB”的服务右键启动
     
     ```
     mongod --config "c:\mongodb\db\mongo.conf" --install
     ```
     
      启动服务方式二
      在CMD窗口中运行如下命令，也可以在可以在 “控制面板\所有控制面板项\管理工具\服务”
     ```
     net start mongodb
     
     net stop mongodb  关闭服务
     ```
   8. 连接数据库

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
 db.user.save({name:'张三',age:30}) 等同于 insert
 
 虽然insert和save方法都可以插入数据，当“_id”值已存在时，调用insert方法插入会报错；而save方法不会,会更新相同的_id所在行数据的信息
 
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

db.user.find({age:{$gt:20}});查询年龄大于20的  $lt  $eq   $lte $gte   $ne 不等
db.user.find({'age':{$gt:20,$lt:30}})  大于20 并且小于30
db.user.find({'name':{$ne:'lv'}});    $ne不等于
db.user.find({$or:[{'name':'lv'},{'name':'chen'}]})  $or选择器   只要满足一个条件   
db.user.find({$and:[{'name':'lv'},{price:5000}]})   $and  多添件同事满足

db.user.find({age:{$in:[20,21,22]}})  ;  $in 包含
db.user.find({age:{$nin:[20,21,22]}})  ;  $nin 不包含

db.user.find().sort({age:1})  1：表示升序  -1：表示降序
db.user.find().limit(10)　　限制数量：db.表名.find().limit(数量);
db.user.find().skip(5)　　 跳过指定数量：db.表名.find().skip(数量);
db.user.find({},{name:1,age:1,sex:0})  指定字段返回   1：返回  0：不返回

-------改-------------------------------------------
db.user.update({name:"张三"}，{$set:{age:25}}) 更新数据： (只改第一条）  与 save()方法相同，（save有则改，没有则添加）
db.user.update({name:"张三"}，{$set:{age:25}},{multi: true})  更新数据： (匹配到的所有）
db.user.update({name:"张三"}，{$set:{'class.age':25}})
---------------------------------------------------
```



### mongoose 

NodeJS操作MongoDB,要使用MongoDB驱动,MongoDB驱动实际上就是为应用程序提供的一个接口，不同的语言对应不同的驱动，NodeJS驱动不能应用在其他后端语言中

首先，安装mongodb
```

```
