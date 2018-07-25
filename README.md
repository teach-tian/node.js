# NVM的安装

## nvm是什么？

nvm 是node版本管理工具 （学习node，首先要安装node的环境，nvm是一款工具，使用这款工具可以很方便的下载所需版本的node文件以及npm，十分的方便。）

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

## 安装完成以后需要进行配置

```

这两行代码就是链接淘宝镜像，在下载node和npm速度会快很多（不用去国外的github上下了）
/**
*node下载源
*/
nvm node_mirror https://npm.taobao.org/mirrors/node/
/**
*npm下载源
*/
nvm npm_mirror  https://npm.taobao.org/mirrors/npm/

```


## windows下nvm的命令([]中的参数可有可无)：


```
nvm arch                         查看当前系统的位数和当前nodejs的位数
nvm install <version> [arch]     安装制定版本的node 并且可以指定平台 version 版本号  arch 平台
nvm list [available]         
  - nvm list   查看已经安装的版本
  - nvm list installed 查看已经安装的版本
  - nvm list available 查看网络可以安装的版本
nvm version         // 查看nvm版本
nvm install 4.6.2   // 安装node4.6.2版本（附带安装npm）
nvm uninstall 4.6.2 // 卸载node4.6.2版本
nvm list            // 查看node版本
nvm use 4.6.2       // 将node版本切换到4.6.2版本
nvm root　　　　     // 查看nvm安装路径 
nvm install latest  //下载最新的node版本和与之对应的npm版本
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

## Linux 命令：
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
7．cp   拷贝
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

