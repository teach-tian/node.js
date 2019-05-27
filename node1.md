

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
