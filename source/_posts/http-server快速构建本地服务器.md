---
title: http-server快速构建本地服务器
date: 2019-06-24 22:54:27
tags:
---
### 在静态页面中需要进行局域网进行访问时，可以开启这个http-server来进行访问

> 在静态页面中需要进行局域网进行访问时，可以开启这个http-server来进行访问

*   1.该环境是基于node环境的，所以必须先安装node.js

> 先打开命令行模式，输入 `node -v`
> 如果显示了版本号，就说明已经安装完成。如果提示没有这个命令，请安装node.js，官网链接 [node.js官网](http://nodejs.cn/)进行安装。

*   2.如果完成上一步，在node命令行下敲下 `npm install http-server -g` 后回车

> 如果提示一下命令，说明安装成功

```
C:\Users\Administrator\AppData\Roaming\npm\hs -> C:\Users\Administrator\AppData\Roaming\npm\node_modules\http-server\bin\http-server
C:\Users\Administrator\AppData\Roaming\npm\http-server -> C:\Users\Administrator\AppData\Roaming\npm\node_modules\http-server\bin\http-server
+ http-server@0.11.1
updated 1 package in 2.133s

```

*   3.进入你需要局域网访问的目录，敲`hs`命令就会显示访问的端口,复制其中一个就可以进行访问了

```
$ hs
Starting up http-server, serving ./
Available on:
http://10.1.43.229:8080
http://127.0.0.1:8080
Hit CTRL-C to stop the server

```
