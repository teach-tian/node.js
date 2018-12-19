# node安装

node 下载地址[http://nodejs.cn/](http://nodejs.cn/)

# NVM的安装

## nvm是什么？

nvm 是node版本管理工具 （nvm是一款工具，使用这款工具可以很方便的下载所需版本的node，十分的方便。）

## windows下的安装：

windows下的离线安装：

* nvm 的windows下载地址：[https://github.com/coreybutler/nvm-windows/releases](https://github.com/coreybutler/nvm-windows/releases) , 选择第二个nvm-setup.zip(第一次安装默认到底，减少后面环境出错的几率，等玩熟了在自定义位置)

* 将下载的文件进行解压：nvm-setup.exe，单击开始安装，直接点击下一步解可以，当然我们需要注意一下两个界面：
  > ![设置nvm路径](https://img-blog.csdn.net/20170209085726130?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvYmFpZHVfMzIyNjIzNzM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
  > ![设置node路径](https://img-blog.csdn.net/20170209085757334?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvYmFpZHVfMzIyNjIzNzM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
  
## 安装完成后： 

* nvm安装路径默认为: C://Users/Administrator/AppData/Roming/nvm 
* nvm安装的node路径默认为: C://ProgramFile/nodejs （其实是个快捷方式） 
* nvm安装多个版本的node，原理是替换C://ProgramFile/nodejs中的node.exe




## windows下nvm的命令([]中的参数可有可无)：


```
nvm list [available]         
  - nvm list   查看已经安装的版本
  - nvm list available 查看网络可以安装的版本
nvm version         // 查看nvm版本
nvm install 4.6.2   // 安装node4.6.2版本
nvm uninstall 4.6.2 // 卸载node4.6.2版本
nvm list            // 查看node版本
nvm use 4.6.2       // 将node版本切换到4.6.2版本
nvm install latest  //下载最新的node版本
```




# nodejs具体安装过程：


应为需要我们这里安装的是nodejs5.3.0版本，
windows（安装windows 32位 nodejs5.3.0）:
```
nvm install 5.3.0 32
```

# nvm安装常见问题：
1. 安装完成后在cmd中输入 nvm 提示nvm不是内部命令或方法？（一般默认到底的安装都自动配好了环境变量，没有的话手动加一下，类似java环境变量配法）

原因：没有配置环境变量。找到nvm安装路径cd C:\Users\Administrator\AppData\Roaming\nvm,再键入nvm即可

2. settings.txt 系统不能找到指定的文件？

解答：替换 C://Users/Administrator/AppData/Roming/nvm目录中settings.txt的内容

```
root: C:\Users\Administrator\AppData\Roaming\nvm 
path: C:\Program Files\nodejs 
arch: 64 
proxy: none 
node_mirror: https://npm.taobao.org/mirrors/node/ 
npm_mirror: https://npm.taobao.org/mirrors/npm/
```

## Linux 命令 (苹果系统)：
```
1.	ls 查看文件/目录
2.	pwd  显示当前的工作目录 
3.	cd    进入目录
   [例子]： 
   cd 回到注册进入时的目录 
   cd /tmp 进入 /tmp 目录 
   cd ../ 进入上级目录 
4.	mkdir  创建目录
5． rmdir  删除目录
6． cat  显示文件至标准输出
7． cp   拷贝
     [例子]: 
    cp file1 file2 将文件 file1 拷贝到文件 file2 
8. mv 移动
     - i 在覆盖已存在文件时作提示，若回答 y 则覆盖，其他则中止
[例子]: 
     mv file1 file2 将文件 file1 改名为 file2 
     mv file1 file2 /tmp 将文件 file1 和文件 file2 移动到目录 /tmp 下
9. touch 创建文件
10.vi 编辑 
    i 插入  编辑内容
    esc  退出编辑
    ：wq 保存并退出
    
   ```
   
### windows常用新建文件命令：

dir 查看当前路径下有哪些文件（或者文件夹）

cd 路径切换 （cd .. 返回上一级） （d: 盘符跳转）

创建文件夹：md 文件夹名

创建空的文件：type nul>文件名

创建有内容文件：echo "内容">文件名

查看文件内容：type +文件名

查看目录及子文件：dir

删除空文件夹：rd 文件夹名

删除文件及所有子文件：rd /s/q 文件夹名

删除文件：del 文件名

### http模块---->创建服务器
```
        // 引入http包
        var http = require('http');

        // 创建服务
        var server = http.createServer(function(req,res){
            res.writeHeader(200,{'Content-type':'text/html;charset=utf8'});//设置相应头
            // req   request    请求对象
            // res   response   响应对象
            res.end('<h1>node.js 主体结构</h1>');//逻辑代码  终止浏览器响应  end 会把响应的信息在浏览器body中显示
        });

        // 监听端口   选择端口  不常用端口 比如：3000 4000 8080 8090 9000
        server.listen(4000,'localhost');

        // 提示
        console.log('服务器：localhost  端口号：4000');

```
node.js 中内置对象  req请求对象  和  res响应对象
```
    req 请求对象
        请求方法    method
        请求路径    url
        协议版本    httpVersion
        请求头         headers
    res 响应对象    
        响应码     statusCode
        响应体     write()   
        响应头     writeHeader(200,{'name':'value'});  //响应头信息                            
        响应体     write()
        结束(必加)  end()

```
常见的http协议
```
常见HTTP状态码(200、301、302、500等）解说
对网站管理工作者来说有个词不陌生，HTTP状态码，它是用以表示网页服务器HTTP响应状态的3位数字代码。状态码的第一个数字代表了响应的五种状态之一。

1XX系列：指定客户端应相应的某些动作，代表请求已被接受，需要继续处理。由于 HTTP/1.0 协议中没有定义任何 1xx 状态码，所以除非在某些试验条件下，服务器禁止向此类客户端发送 1xx 响应。
2XX系列：代表请求已成功被服务器接收、理解、并接受。这系列中最常见的有200、201状态码。
200状态码：表示请求已成功，请求所希望的响应头或数据体将随此响应返回
201状态码：表示请求成功并且服务器创建了新的资源，且其 URI 已经随Location 头信息返回。假如需要的资源无法及时建立的话，应当返回 '202 Accepted'
202状态码：服务器已接受请求，但尚未处理

3XX系列：代表需要客户端采取进一步的操作才能完成请求，这些状态码用来重定向，后续的请求地址（重定向目标）在本次响应的 Location 域中指明。这系列中最常见的有301、302状态码。
301状态码：被请求的资源已永久移动到新位置。服务器返回此响应（对 GET 或 HEAD 请求的响应）时，会自动将请求者转到新位置。
302状态码：请求的资源临时从不同的URI响应请求，但请求者应继续使用原有位置来进行以后的请求
304自从上次请求后，请求的网页未修改过。服务器返回此响应时，不会返回网页内容。 如果网页自请求者上次请求后再也没有更改过，您应将服务器配置为返回此响应(称为 If-Modified-Since HTTP 标头)。
4XX系列：表示请求错误。代表了客户端看起来可能发生了错误，妨碍了服务器的处理。常见有：401、404状态码。
401状态码：请求要求身份验证。 对于需要登录的网页，服务器可能返回此响应。
403状态码：服务器已经理解请求，但是拒绝执行它。与401响应不同的是，身份验证并不能提供任何帮助，而且这个请求也不应该被重复提交。
404状态码：请求失败，请求所希望得到的资源未被在服务器上发现。没有信息能够告诉用户这个状况到底是暂时的还是永久的。假如服务器知道情况的话，应当使用410状态码来告知旧资源因为某些内部的配置机制问题，已经永久的不可用，而且没有任何可以跳转的地址。404这个状态码被广泛应用于当服务器不想揭示到底为何请求被拒绝或者没有其他适合的响应可用的情况下。
5xx系列：代表了服务器在处理请求的过程中有错误或者异常状态发生，也有可能是服务器意识到以当前的软硬件资源无法完成对请求的处理。常见有500、503状态码。
500状态码：服务器遇到了一个未曾预料的状况，导致了它无法完成对请求的处理。一般来说，这个问题都会在服务器的程序码出错时出现。
503状态码：由于临时的服务器维护或者过载，服务器当前无法处理请求。通常，这个是暂时状态，一段时间会恢复
了解基本SEO状态码，是SEO优化人员必备知识。HTTP状态码是服务器和客户端之间交流信息的语言。通过查看网站日志的HTTP码，我们可以清楚查看搜索引擎在网站的爬取情况。

```
   
### 解决中文乱码乱码问题

```
  res.setHeader('Content-Type','text/html;charset=utf-8')
```

### 解决跨域问题
```
  res.setHeader('Access-Control-Allow-Origin': '*')//允许 任何跨域请求
```

### fs模块

```

var fs=require('fs');
//异步读取文件  
fs.readFile('./www/index.html',function(err,data){
  if(!err){
  console.log(data) ; // Buffer  对象  （二进制流）
  console.log(data.toString()) ;  //字符串
})

// 同步读取文件

var buff=fs.readFileSync('./www.index.html');

//异步写入文件

fs.writeFile('./www/a.txt','hello world',function(err){
  if(!err){
     console.log('写入成功')
  }
})

//同步写入

fs.writeFileSync('./www/a.txt','aaaaaa');

```
### 同步&异步

```
同步： 在没做完一件事之前，不可以做下一件事

异步： 基于回调函数的，第一件事放在回调函数（内存）中运行，接着处理下一件事  （比如定时器，ajax, fs.readFile()）

```
   
### 注册登录前端
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    
    <form action="http://localhost:8888/home/list/li/abc" method="post">
 
       用户名：<input type="text" name='user'> <br>
       密码：<input type="password" name='pass'>  <br>
       <button type="submit">登录</button>

    </form>
</body>
</html>
```

### 后端

```
var http=require('http');

var fs=require('fs');

var app=http.createServer(function(req,res){
    
    console.log(req.url)//     /aaa?user=lisi&pass=1234567889


    // var url='/aaa';

    // var obj={user:'lisi',pass:123456789}


    var str=req.url; // /aaa?user=lisi&pass=1234567889


      var obj={}

    var url_str=str.split('?');//字符串 以 指定字符 分割成数组   ['/aaa','user=lisi&pass=1234567889']

        var url=url_str[0];  //   路径 /aaa

        var arr=url_str[1].split('&');  //   ['user=lisi','pass=1234567889']

         for(var i=0;i<arr.length;i++){
              var arr1= arr[i].split("=") //  [uaer,lisi]  
              obj[arr1[0]]=arr1[1]
         }


   console.log(url,obj)




   
})


app.listen(8888,function(){
    console.log('服务器运行成功')
})
```

### querystring 模块

```
//参数解析模块
var querystring=require('querystring');

var str= '/aaa?user=lisi&pass=1234567889';


 var arr=str.split('?');


 var url=arr[0];

 var objstr=arr[1];  //  user=lisi&pass=1234567889

 var query=querystring.parse(objstr)


console.log(url,query)

```
### url 模块


// url模块 解析 url
var urlLib=require('url')

var str= '/aaa?user=lisi&pass=1234567889';


var obj=urlLib.parse(str,true);

var url=obj.pathname; //路径

var urlObj=obj.query


console.log(url,urlObj)


### post请求
```
    var url=urlLib.parse(req.url,true).pathname;

    var str=''
    req.on('data',function(thunk){
        str+=thunk;
    })

    req.on('end',function(){
        console.log(url,querystring.parse(str))
    })

  
```

### data 分次发送

```

    var str=req.url;//  /home

    var url=urLib.parse(str,true).pathname;

    var str=''
      
    var i=0;

    //分段传送  每当有一段数据提交过来 data事件就会触发一次
    req.on('data',function(thunk){
        i++
        console.log("当前次数为"+i)
        str+=thunk;
    });

    req.on('end',function(){
        console.log(querystring.parse(str));
    })

```

### 模块

Node.js 提供了 exports 和 require 两个对象，其中 exports 是导出模块的方法，require 从外部获取一个模块的接口的方法

下面，我们创建hello.js文件，并用exports导出一个模块
```
exports.world = function() {
  console.log('Hello World');
}
```

接下来我们创建 main.js文件，用require导入刚才定义好的模块

```
var hello = require('./hello');
hello.world();

```

有时候，我们一次想导出多个方法 ,如下 ：创建 hello.js文件

```
module.exports = {
  getName:function(name){console.log('我的名字是'+name)},
  setName:function(name){console.log('我的名字改为'+name)}
}

```

导入模块没有变，如下：创建main.js文件

```
var hello = require('./hello');
hello.getName('tom');
hello.setName('kiry');

```


### npm 包发布


1.创建文件  loverqq

2.cd loverqq

3.执行 npm init  

       配置向导  name  version  description .....

       生成package.json  文件
      
       创建 index.js   
              --------定义模块 并且导出

4.注册  npm 账号 

   执行  npm adduser    // 注册npm

         username:tianxing
         password:11111111
         email:25554544@xx.com

     Logged in as tianxing on       https://registry.npmjs.org/.


5.发布 模块

    执行 npm publish --access public


6.使用

  npm install loverqq     cnpm install loverqq
  
  
### 通过HTTP请求响应过程了解HTTP协议
      首先了解一次完整的HTTP请求到响应的过程需要的步骤

      1. 域名解析 
      2. 发起TCP的3次握手 
      3. 建立TCP连接后发起http请求 
      4. 服务器端响应http请求，浏览器得到html代码 
      5. 浏览器解析html代码，并请求html代码中的资源 
      6. 浏览器对页面进行渲染呈现给用户
      1.域名解析
      就是将网站名称转变成IP地址：localhost-->127.0.0.1
      DNS域名解析等等可以实现这种功能
      2.发起TCP的3次握手
      在客户机和服务器之间建立正常的TCP网络连接时：

      客户机首先发出一个SYN消息，

      服务器使用SYN+ACK应答表示接收到了这个消息，

      最后客户机再以ACK消息响应。

      这样在客户机和服务器之间才能建立起可靠的TCP连接，数据才可以在客户机和服务器之间传递。
      下面一段内容引自一次完整的HTTP事务是怎样一个过程？

      拿到域名对应的IP地址之后，User-Agent（一般是指浏览器）会以一个随机端口（1024 < 端口 < 65535）向服务器的WEB程序（常用的有httpd,nginx等）80端口发起TCP的连接请求。这个连接请求（原始的http请求经过TCP/IP4层模型的层层封包）到达服务器端后（这中间通过各种路由设备，局域网内除外），进入到网卡，然后是进入到内核的TCP/IP协议栈（用于识别该连接请求，解封包，一层一层的剥开），还有可能要经过Netfilter防火墙（属于内核的模块）的过滤，最终到达WEB程序（本文就以Nginx为例），最终建立了TCP/IP的连接。
      
      3.发起HTTP请求(HTTP Request)
      所谓的HTTP请求，也就是Web客户端向Web服务器发送信息，这个信息由如下三部分组成：

      （1）请求行

      例如：GET www.cnblogs.com HTTP/1.1
      请求行写法是固定的，由三部分组成，

      第一部分是请求方法：

      除了常见的只有Get和Post方法，实际上HTTP请求方法还有很多，比如： PUT方法，DELETE方法，HEAD方法，CONNECT方法，TRACE方法

      第二部分是请求网址，

      第三部分是HTTP版本。
      （2）HTTP头

      HTTP头在HTTP请求可以是3种HTTP头：1. 请求头(request header)  2. 普通头(general header)  3. 实体头(entity header)

      通常来说，由于Get请求往往不包含内容实体，因此也不会有实体头。
      （3）内容

      只在POST请求中存在，因为GET请求并不包含任何实体
      4.服务器端HTTP响应(HTTP Response)请求
      当Web服务器收到HTTP请求后，会根据请求的信息做某些处理(这些处理可能仅仅是静态的返回页，或是包含Asp.net, PHP, Jsp等语言进行处理后返回)，相应的返回一个HTTP响应。HTTP响应在结构上很类似于HTTP请求，也是由三部分组成，分别为:

      1.状态行

      例如：HTTP/1.1 200 OK

      第一部分是HTTP版本

      第二部分是响应状态码
      第三部分是状态码的描述

          信息类 (100-199)
          响应成功 (200-299)
          重定向类 (300-399)
          客户端错误类 (400-499)
          服务端错误类 (500-599)
      详细HTTP 状态消息请看:HTTP 状态消息
      
      常见状态代码、状态描述的说明如下。
      200 OK：客户端请求成功。
      400 Bad Request：客户端请求有语法错误，不能被服务器所理解。
      401 Unauthorized：请求未经授权，这个状态代码必须和WWW-Authenticate报头域一起使用。
      403 Forbidden：服务器收到请求，但是拒绝提供服务。
      404 Not Found：请求资源不存在，举个例子：输入了错误的URL。
      500 Internal Server Error：服务器发生不可预期的错误。
      503 Server Unavailable：服务器当前不能处理客户端的请求，一段时间后可能恢复正常，举个例子：HTTP/1.1 200 OK（CRLF）。

      2.HTTP头

      HTTP响应中包含的头包括：1. 响应头(response header) 2. 普通头(general header) 3. 实体头(entity header)。
      3.返回内容

      HTTP响应内容就是HTTP请求所请求的信息。这个信息可以是一个HTML，也可以是一个图片。响应的数据格式通过Content-Type字段来获得：Content-Type：image/png；或者我们熟悉的Content-Type：text/html
      下面是一些常见的Content-Type字段的值。

          text/plain
          text/html
          text/css
          image/jpeg
          image/png
          image/svg+xml
          audio/mp4
          video/mp4
          application/javascript
          application/pdf
          application/zip
          application/atom+xml

      5.浏览器解析html代码，并请求html代码中的资源
      了解持久连接

      有时候我们获取一个HTML页面，在对浏览器对HTML解析的过程中，如果发现额外的URL需要获取的内容，会再次发起HTTP请求去服务器获取，比如样式文件，图片。许多个HTTP请求，只依靠一个TCP连接就够了，这就是所谓的持久连接。也是所谓的一次HTTP请求完成。


# 跨域请求
node跨域请求，主要介绍了两种方法，一种是jsonp，另一种CORS(CORS是一个W3C标准，全称是"跨域资源共享"（Cross-origin resource sharing）。

它允许浏览器向跨源服务器，发出XMLHttpRequest请求，从而克服了AJAX只能同源使用的限制。)

下面cors跨域案例
node部分
```
var http = require('http')
var url = require('url')
var querystring = require('querystring')
 
var port = 9000
var jsonData = { 'name': 'xiaohong', 'job': 'daboss' }
http.createServer(function (req, res) {
  // var pathStr = url.parse(req.url)
    res.writeHead(200, {
    'Content-Type': 'application/json;charset=utf-8',
    'Access-Control-Allow-Credentials': true,
    'Access-Control-Allow-Origin': '*'
  })
  var type = req.method;
  if (type == 'GET') {
    
    res.end(JSON.stringify(jsonData))
  } else if (type == 'POST') {
    var str = '';
    req.on('data',function(chunk){
      str += chunk;
    })
     
    req.on('end',function(){
      var data = querystring.parse(str)
      console.log(data)
      if(data.name == "" || data.job == ""){
        res.end(JSON.stringify({'success':true,msg:'填写有误'}))
      }else{
        res.end(JSON.stringify({'success':false,msg:'添加成功'}))
      }
 
    })
  }
 
}).listen(port, function () {
  console.log('server is runing at port ' + port)
})

```

html 部分
```
<!DOCTYPE html>
<html lang="en">
 
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>
  <a class="click" href="javascript:get_jsonp()" rel="external nofollow" >click me</a>
  <p class="result"></p>
  <label>姓名:</label>
  <input class="name" type="text" />
  <label>职位：</label>
  <input class="job" type="text">
  <a class="add" href = "javascript:add()">添加</a>
  <p class="msg"></p>
  <script src="http://code.jquery.com/jquery-latest.js"></script>
  <script>
    function get_jsonp() {
      $.ajax({
        type: 'get',
        dataType: 'json',
        url: 'http://localhost:9000',
        success: function (data) {
          $('.result').html('my name is ' + data.name)
        },
        error: function (err) {
          $('.result').html('出错了 ' + err.status)
        }
      })
    }
    function add(){
      $.ajax({
        type:'post',
        url:'http://localhost:9000',
        // dataType:'json',
        data:{
          'name':$(".name").val(),
          'job':$(".job").val()
        },
        success:function(data){
            console.log(data);
          $('.msg').html(data.msg)
        },
        error:function(err){
           
           $('.msg').html('出错了'+err.status)
        }
      })
    }
  </script>
</body>
</html>
```

### express
 1. cnpm install -g express   全局安装express 
     //跳过1直接安装4.0以上版本
  
 2. cnpm install -g express-generator  安装4.0之后的express
 3. express -V                检测express 版本号
 4. express -e blog && cd blog
         （ blog是安装的文件夹名）

5. npm install
       （安装express及依赖）

6. npm start
（这里需要注意 express 4.x 无法以 node app.js 为启动方式，而是用指令 npm start 作为启动）

 访问 http://localhost:3000/ 出现熟悉的Welcome to Express，证明安装成功。
---------------------------------------------------------------------------------------
项目创建成功之后，生成四个文件夹，

app.js 是主文件

packetage.json 是配置信息文件

bin是项目的启动文件，配置以什么方式启动项目，默认 npm start

public是项目的静态文件，放置js css img等文件

routes是项目的路由信息文件,控制地址路由

views是视图文件，放置模板文件ejs或jade,swig等（其实就相当于html形式文件啦~)

node_modules 是项目依赖的各种插件

express这样的MVC框架模式，是一个Web项目的基本构成。
-----------------------------------------------------------------------------------------

## app.js

```

var express=require("express");  //http 

var app=express();// 创建app服务器  === http.createServer()

var RouterA=require('./routes/a.js');
var RouterHome=require('./routes/home')

var path=require("path");

var port=3000; //端口

var ejs=require("ejs");

//设置 视图文件路径
app.set("views",path.join(__dirname,"views"));

//设置解析 视图文件的引擎
app.set('view engine','ejs')

//设置静态资源的路径
app.use('/public',express.static(path.join(__dirname,'public')))

var ip='127.0.0.1';//ip

app.listen(port,ip,function(){  //app服务器监听端口
  console.log("服务器运行在http://"+ip+":"+port)
});


app.use('/',RouterHome)
app.use('/a',RouterA)


function fn(req,res){ // app添加 get请求根路径的路由
    // res.send("hello world");// 向前台输出
    console.log(req.url)
    res.write("hello express123");
    res.end()
}


// module.exports=app;

```
#bodyParser中间件的使用
```
执行指令： cnpm install body-parser -D

var bodyParser=require('body-parser');

app.use(bodyParser.urlencoded({extended:true,limit:100}))

app.post('/api',function(req,res,next){
  console.log(req.body)
})

```


# bodyParser 中间件的封装
```
var str=''
var querystring=require('querystring')
app.use(function(req,res,next){
   
     req.on('data',function(thunk){
         str+=thunk;

     })
     req.on('end',function(){
           req.body=querystring.parse(str);
           next();
     })
})

app.post('/add',function(req,res,next){
       console.log(req.body);
})
```

# mongoose 操作
```
数据库连接：

 mongoose.connect('mongodb://127.0.0.1:27017/xyz',function(err){

     if(err){
         console.log('数据库连接失败')
     }else{
       console.log('数据库连接成功')
      server.listen(port);
      server.on('error', onError);
      server.on('listening', onListening);
     }
 })
 
 创建schema
 
var mongoose=require('mongoose');
var schema=mongoose.Schema;
// 数据库中 集合的 文档 结构
var mySchema=new schema({
    user:{type:String,default:'张三'},
    txt:'string',
    times:{type : Date, default: Date.now},
})

module.exports=mySchema;


创建 model

var mongoose=require('mongoose');
var schema=require('../shemas/user')
//创建集合类  
var user=mongoose.model('user',schema);
module.exports=user;


添加数据

   基于model操作
1. collection.create({user:user,txt:txt,times:new Date()},function(err,doc){
           if(err){
               console.log('写入失败')
           }else{
               console.log('写入成功：插入的文档为'+doc);
               res.redirect('/')
           }
    })
    
    基于 entity 操作
2.  var entity={user:user,txt:txt,times:new Date()};
    var mydb=new collection(entity);
            mydb.save(function(err,doc){
                        if(!err){
                        console.log('写入成功'+doc);
                    }
            })
            
 3. 删除
   
    colletion.remove({_id:c}).then(function(){
        console.log("删除成功");
        res.redirect('/')
    })
 4. 修改
 
     collection.update({_id:id},{$set:{user:'张三',txt:'hello word',times:new Date()}},function(err,data){
       if(!err){
      res.redirect("/")
        }
      })
 
 5.查找
 
   collection.find({}).sort({_id:-1}).skip(5).limit(5).exac(function(err,docs){
     
   })
```

# cookie 
```
const express=require('express');
const cookieParser=require('cookie-parser');

var server=express();



//添加cookie 签名
server.use(cookieParser('wesdfw4r34tf'));

server.use('/', function (req, res){

  //向浏览器存入 带签名的cookie
  res.cookie('user', 'xiaoming', {signed: true});
  
  //向浏览器存入不带签名的cookie
  res.cookie('pass',123456)

  console.log('签名cookie：', req.signedCookies)
  console.log('无签名cookie：', req.cookies);
 
  //清除cookie
   res.clearCookie('user');
  res.send('ok');
});

server.listen(8080);

```

# session
```

```

# jade

### 根据缩进划分层级
```
//安装jade
cnpm install jade

+index.jade
 ----------------------------------
doctype html
heml
    head
        title 我的博客
    body
        div
           h1 积云博客
-----------------------------------
+server.js
var jade=require('jade');
//将jade文件渲染成html文件   pretty 格式化
var str=jade.renderFile('./index.jade',{pretty:true});
console.log(str);

执行代码：node server  


1.选择器的使用

p#box.a.b ------>  <p class='a b' id='box'>

2.如果省略标签元素，默认是div

#box----------> <div></div>

3.属性的使用 多个属性用,号隔开

input.a(name='user',type='text')  -----> <input class='a' name='user' type='text'>

也可以换行 （此时,可以省略）
input.a(name='user'
type='text')                -----> <input class='a' name='user' type='text'>

style属性 用{}   带有杠的CSS属性写法

a(style={'z-index':'99',color:'red'})------------><a style="z-index":99,color:red></a>

class属性用 []
p(class=['a','b']) --------------->  <p class='a b'></p>

4.字符转义

使用=赋值会进行转义

div(href="https://www.baidu.com/s?wd=jade&ws=jades")
编译后:
<div href="https://www.baidu.com/s?wd=jade&amp;ws=jades"></div>
& 发生了转义 &amp;

使用!=不会转义

div(href!="https://www.baidu.com/s?wd=jade&ws=jades")
编译后:
<div href="https://www.baidu.com/s?wd=jade&ws=jades"></div>

5.变量的使用

单个变量

- var code = 1;
p.bt #{code}   -----------><p class="bt">1</p>

对象

- var code = {z:1,q:2};
p.bt #{code.q} -----------------><p class="bt">2 </p>

字符串拼接
- var code = {z:1,q:2};
p(class='bt'+code.z) #{code.q} ----------------><p class="bt1">2</p>

!{} 不对字符串进行转义
- var str = 'user=小明&psss=123456'
p #{str} ------------> <p>user=小明&amp;psss=123456</p>
p !{str} ------------> <p>user=小明&psss=123456</p>

6.流程控制语句

For 语句

- for(var i=0;i<2;i++)
   div #{i} //注意缩进       -------->     <div>0</div>
                                           <div>1</div>
                                           
If...else 语句

- var ifv = true;
if(ifv)
    div  为真               ---------->    <div>为真</div>
else
    div 为假         
    
    
case 语句  （等同于js中的 switch语句）


- var i=0;
case i
    when 0
        div 变量为#{i}
    when 1               ------------------><div>变量为0</div>
        div 变量为1
    default
        div 没有匹配项
7.注释

html可见注释

//html可见注释
div.bt         ---------->    <!--html可见注释-->
                               <div class="bt"></div>


html不可见注释

//-html不可见注释
div.bt         ------------->   <div class="bt"></div>


多行注释(注意缩进)

//
  div.bt      -------------->   <!--div.bt-->

8.include


doctype html
html
  head
    style
      include style.css
  body
    script
      include script.js
 
编译后:（一定要有这两个文件，不然jade会报错）

<!DOCTYPE html>
<html>
  <head>
    <style>
    p{
    color:red;
    }
    </style>
  </head>
  <body>
    <script>console.log(1)</script>
  </body>
</html>


9.extends与block


layout.jade
----------------------------
doctype html
html
    head
        title hello jade!
    body
　　　　 block content
        
        block foot        
---------------------------

index.jade
--------------------------
extends ./layout.jade

block content
       h1 content主体部分 

block foot
    h1 foot脚注部分
-------------------------


 编译后：
--------------------------------
<!DOCTYPE html>
<html>
  <head>
    <title>hello jade!</title>
  </head>
  <body>
    <h1>content主体部分</h1>

    <h1>foot脚注部分</h1>
  </body>
</html>
-------------------------------


10.jade中写行内js或css

doctype html
html
  head
    style.
    p{color:red}
  body
    script.
    console.log(OK)

编译后:

<!DOCTYPE html>
<html>
  <head>
    <style>p{
    color:red;
    }
    </style>
  </head>
  <body>
    <script>console.log(OK)</script>
  </body>
</html>
```

# layui

layui 官网：[https://www.layui.com/](https://www.layui.com/)
```

获得 layui 后，引入下述两个文件：
       ./layui/css/layui.css
       ./layui/layui.all.js
```
# path


```
全局对象
__dirname  表示当前执行脚本所在的目录。
—filename  表示当前执行脚本文件路径（绝对路径）

const path=require('path');

var str='c:\\wamp\\www\\a.html';
1.path.parse() 解析地址
var obj=path.parse(str);

//base      文件名部分   a.html
//ext       扩展名      .html
//dir       路径        c:\\wamp\\www
//name      文件名部分   a
2.path.normalize()    格式化路径   注意'..' 和 '.'

console.log(path.normalize('/test/test1//2slashes/1slash/tab/..'));  ----------> /test/test1/2slashes/1slash

3.path.join() 连接路径
console.log(path.join('/test', 'test1', '2slashes/1slash', 'tab', '..')); --------> /test/test1/2slashes/1slash

4.path.resolve()  转换为绝对路径
console.log(path.resolve('main.js'));   ---------> /web/com/1427176256_27423/main.js  == __filename
console.log(path.resolve());   ---------> /web/com/1427176256_27423/main.js  == __direname
```
# 文件上传 multer

```

body-parser	解析post数据
multer		  解析post文件

前端文件：
  <form action="http://localhost:8080/" method="post" enctype="multipart/form-data">
      文件：<input type="file" name="f1" /><br>
      <input type="submit" value="上传">
   </form>

后端文件：

下载 multer模块： cnpm i multer --save

const multer=require('multer');
//指定磁盘存放路径
var objMulter=multer({dest: './www/upload/'});
//使用中间件
server.use(objMulter.any());
//新名字
var newName=req.files[0].path+pathLib.parse(req.files[0].originalname).ext;
// 设置新名字   fs.rename(老名, 新名, function (err){})
  fs.rename(req.files[0].path, newName, function (err){
    if(err)
      res.send('上传失败');
    else
      res.send('成功');
  });
```
### JSON和JSONP
```
JSONP的全称是JSON with Padding，由于同源策略的限制，XmlHttpRequest只允许请求当前源（协议，域名，端口）的资源。如果要进行跨域请求，我们可以通过使用html的script标记来进行跨域请求，并在相应中返回要执行的script代码，其中可以直接使用JSON传递javascript对象。这种跨域的通讯方式成为JSONP。

由此我们可以看出两者的区别：

json： 一种轻量级的数据格式。

jsonp：为实现跨域，而采用的一种脚本注入方法
 ```
### 实现

我们要读取数据都是

```
var data = {'name': 'jifeng', 'company': 'taobao'};

```

服务器端代码
```
var http = require('http');
var urllib = require('url');
 
var port = 10011;
var data = {'name': 'jifeng', 'company': 'taobao'};
 
http.createServer(function(req, res){
 var params = urllib.parse(req.url, true);
 console.log(params);
 if (params.query && params.query.callback) {
 //console.log(params.query.callback);
 var str = params.query.callback + '(' + JSON.stringify(data) + ')';//jsonp
 res.end(str);
 } else {
 res.end(JSON.stringify(data));//普通的json
 }  
}).listen(port, function(){
 console.log('server is listening on port ' + port); 
})
```

游览器端代码，为方便起见，我直接用了jquery的方法

```
<html> 
<head> 
 <script src="http://code.jquery.com/jquery-latest.js"></script> 
 <meta http-equiv="Content-Type" content="text/html; charset=utf-8"> 
</head> 
<body> 
<script type="text/javascript"> 
function get_jsonp() { 
 $.getJSON("http://127.0.0.1:10011?callback=?", 
 function(data) {
 $('#result').val('My name is: ' + data.name); 
 }); 
} 
</script> 
<a href="javascript:get_jsonp();" rel="external nofollow" >Click me</a><br /> 
<textarea id="result" cols="50" rows="3"></textarea> 
</body> 
</html> 
```
jquery中getJSON（）方法可以参见：[http://www.w3school.com.cn/jquery/ajax_getjson.asp](http://www.w3school.com.cn/jquery/ajax_getjson.asp)





