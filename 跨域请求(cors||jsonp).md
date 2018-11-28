### jsonp 跨域请求原理
跨域的安全限制都是对浏览器端来说的，服务器端是不存在跨域安全限制的。

浏览器的同源策略限制从一个源加载的文档或脚本与来自另一个源的资源进行交互。

如果协议，端口和主机对于两个页面是相同的，则两个页面具有相同的源，否则就是不同源的。

如果要在js里发起跨域请求，则要进行一些特殊处理了。或者，你可以把请求发到自己的服务端，再通过后台代码发起请求，再将数据返回前端。
## 先看下准备环境：两个端口不一样，构成跨域请求的条件

html前端代码
```
<html>
<head>
    <title>跨域测试</title>
    <script src="http://code.jquery.com/jquery-latest.js"></script>
    <script>
        //回调函数
        function showData (result) {
            var data = JSON.stringify(result); //json对象转成字符串
            $("#text").val(data);
        }

        $(document).ready(function () {

            $("#btn").click(function () {
                //向头部输入一个脚本，该脚本发起一个跨域请求
                $("head").append("<script src='http://localhost:9090/student?callback=showData'><\/script>");
            });

        });
    </script>
</head>
<body>
    <input id="btn" type="button" value="跨域获取数据" />
    <textarea id="text" style="width: 400px; height: 100px;"></textarea>

</body>
</html>
```

node 后端
```
var http = require('http')
var url = require('url')
var querystring = require('querystring')
 
var port = 9090
//数据
var jsonData = "{ 'name': 'xiaohong', 'job': 'daboss' }"
http.createServer(function (req, res) {

    var obj=url.parse(req.url,true);
    var pathname=obj.pathname;
    var query=obj.query;
    console.log(query);
    
    if(pathname=='/student'){
        //用回调函数名称包裹返回数据，这样，返回数据就作为回调函数的参数传回去了
        var str=query.callback+'('+jsonData+')';
        console.log(str);
         res.end(str)
    }
 
}).listen(port, function () {
  console.log('server is runing at port ' + port)
})
```

### 总结：
以上使用<script src="">来完成一个跨域请求，
当点击"跨域获取数据"的按钮时，添加一个<script>标签，用于发起跨域请求；注意看请求地址后面带了一个callback=showData的参数；
showData即是回调函数名称，传到后台，用于包裹数据。数据返回到前端后，就是showData(result)的形式，因为是script脚本，所以自动调用showData函数，而result就是showData的参数。

### 再来看jquery的jsonp方式跨域请求：

服务端代码不变，js代码如下：最简单的方式，只需配置一个dataType:'jsonp'，就可以发起一个跨域请求。jsonp指定服务器返回的数据类型为jsonp格式，
可以看发起的请求路径，自动带了一个callback=xxx，xxx是jquery随机生成的一个回调函数名称。
至此，我们算是跨域把数据请求回来了，但是比较麻烦，需要自己写脚本发起请求，然后写个回调函数处理数据，不是很方便。

这里的success就跟上面的showData一样，如果有success函数则默认success()作为回调函
```

<html>
<head>
    <title>跨域测试</title>
    <script src="http://code.jquery.com/jquery-latest.js"></script>
    <script>

        $(document).ready(function () {

            $("#btn").click(function () {

                $.ajax({
                    url: "http://localhost:9090/student",
                    type: "GET",
                    dataType: "jsonp", //指定服务器返回的数据类型
                    success: function (data) {
                        var result = JSON.stringify(data); //json对象转成字符串
                        $("#text").val(result);
                    }
                });

            });

        });
    </script>
</head>
<body>
    <input id="btn" type="button" value="跨域获取数据" />
    <textarea id="text" style="width: 400px; height: 100px;"></textarea>

</body>
</html>
```
