
### 1、cookie的处理
设置cookie：给客户端发送cookie，通过res.cookie('属性名'，‘值’，{signed:boolean,path:'/',maxAge:毫秒})，req.secret='fdfsdfs'

'值'可以是对象    signed:true 开启签名模式      req.secret为秘钥
```
const express = require('express');
let server = express();
server.listen(8080);
 
// 给客户端返回cookie
server.use('/',(req,res)=>{
    res.cookie('user','jiang',{path:'/aaa',maxAge:30*24*3600*1000});
    res.send('ok');
});

```

读取cookie：服务端读取客户端设置的cookie，需要中间件cookie-parser,server.use(cookieParser('密钥')); 
req.signedCookies 签名模式的cookies获取     req.cookies  普通模式cookies获取

```
const express = require('express');
// 服务端解析客户端发送过来的cookie，序列化
const cookieParser = require('cookie-parser')
let server = express();
server.listen(8080);
 
// 解析客户端传过来的cookie
server.use(cookieParser());
 
server.use('/aaa',(req,res)=>{
    console.log(req.cookies);
    res.send('ok');
});

```

在服务端给cookie设置密钥，防止别人修改cookie（利用签名在服务端，别人拿不到），并不是所有的cookie都设置密钥，因为cookie的大小有限制，所以尽量不用密钥的cookie就不用

重点变化的地方：

```

// 解析客户端传过来的cookie,要相同的密钥
server.use(cookieParser('dssedsasad'));
 
// 设置密钥
req.secret = 'dssedsasad';
 
res.cookie('user','jiang',{signed:true,path:'/'});
 
// 获取客户端传过来的cookie
console.log('signed cookies:', req.signedCookies);
console.log('unsigned cookies:', req.cookies);


```

```

const express = require('express');
// 服务端解析客户端发送过来的cookie，序列化
const cookieParser = require('cookie-parser')
let server = express();
server.listen(8080);
 
// 解析客户端传过来的cookie,要相同的密钥
server.use(cookieParser('dssedsasad'));
 
// 给客户端返回cookie
server.use('/',(req,res)=>{
    // 设置密钥
    req.secret = 'dssedsasad';
    // signed---签名虽然不能加密，可以通过decodeURIComponent()解析得到cookie值，但是可以防止别人修改cookie
    //签名在服务端，别人拿不到
    //"s:jiang.x9qnDbqoUkB5D/r0gDpEiE6i74K35MpA7RP/1PK7gBI"
    res.cookie('user','jiang',{signed:true,path:'/'});
    res.send('ok');
 
    // 获取客户端传过来的cookie
    console.log('signed cookies:', req.signedCookies);
    console.log('unsigned cookies:', req.cookies);
});

```

删除cookie：res.clearCookie('属性名')

### 2、session的处理

1）引进cookie-parser解析cookie,cookie-session处理session

2）使用上面的插件：

```
// 先解析客户端传过来的cookie
server.use(cookieParser());
// 然后才能用cookie中的sessionId
server.use(cookieSession({
    // session需要传递一个keys进行加密，加在server上，给一个数组即有多个密钥提高安全性
    keys:['aa','bb','cc']
}));


```

3）获取session:req.session

完整的例子：基于session同级website访问的次数

```
// session是基于cookie解析的
const express = require('express');
// 服务端解析客户端发送过来的cookie，序列化
const cookieParser = require('cookie-parser')
// 处理session
const cookieSession = require('cookie-session');
let server = express();
server.listen(8080);
 
 
// 先解析客户端传过来的cookie
server.use(cookieParser());
// 然后才能用cookie中的sessionId
server.use(cookieSession({
    // session需要传递一个keys进行加密，加在server上，给一个数组即有多个密钥提高安全性
    keys:['aa','bb','cc']
}));
 
// 利用session统计网站的访问次数
server.use('/',(req,res)=>{
    console.log(req.session);
    if(req.session['count'] == null){
        // 没有，说明是第一次访问
        req.session['count'] = 1;
    }else{
        // 有，则对count累加
        req.session['count']++;
    }
    res.send('ok');
});
删除session:delete req.session

```





