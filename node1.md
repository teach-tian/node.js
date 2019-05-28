

# node 概念

1. Node.js 就是运行在服务端的 JavaScript
2. Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境(平台)
3. Node.js是一个基于事件驱动的I/O服务端JavaScript环境，基于Google的V8引擎，V8引擎执行Javascript的速度非常快，性能非常好。

# node安装

node 下载地址[http://nodejs.cn/](http://nodejs.cn/)

### Node.js REPL(交互式解释器) 
```
打开终端

输入:
node -v   检测node版本
简单的表达式运算：
$ node
> 1 +4
5
> 5 / 2
2.5
> 3 * 6
18
> 4 - 1
3
> 1 + ( 2 * 3 ) - 4
3
>
使用变量：
$ node
> x = 10
10
> var y = 10
undefined
> x + y
20
> console.log("Hello World")
Hello World
undefined
多行表达式：
$ node
> var x = 0
undefined
> do {
... x++;
... console.log("x: " + x);
... } while ( x < 5 );
x: 1
x: 2
x: 3
x: 4
x: 5
undefined
>
```

### 退出REPL

```
control + cc

```

### 简单服务器的创建

```

   // 引入http包
        var http = require('http');

        // 创建服务
        var server = http.createServer(function(req,res){
            // req   request    请求对象
            // res   response   响应对象
            res.end('<h1>node.js 主体结构</h1>');//逻辑代码  终止浏览器响应  end 会把响应的信息在浏览器body中显示
        });
        
        从0~65535全部是标准端口，但是从0~1024号端口是系统端口，用户无法修改
        从1025~65534端口是系统为用户预留的端口，而65535号端口为系统保留

        // 监听端口   选择端口  不常用端口 比如：3000 4000 8080 8090 9000
        server.listen(4000,'localhost');

        // 提示
        console.log('服务器：localhost  端口号：4000');



```
### 请求对象，响应对象
```
 req 请求对象
        请求方法    method
        请求路径    url
        协议版本    httpVersion
        请求头         headers
    res 响应对象    
      
                         
        响应体     write()
        结束(必加)  end()

```

### 解决中文乱码的问题
```
  res.setHeader('Content-Type','text/html,charset=utf-8')
```

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

//追加
fs.appendFile('./data/b.txt',data,'utf8',function(err, ret) {
                if(err) {
                        throw err
                }
                console.log('success')
            }
```
