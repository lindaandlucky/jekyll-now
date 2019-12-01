# 模块： CommonJS规范

```js
使用<scripts/>管理有一些问题： 

   		脚本变多，需要手动管理加载顺序

			不同脚本之间逻辑调用，需要通过全局变量的方式

			没有html怎么办

```

# npm

```js
npm 是什么？ node.js的包管理工具
包是什么？ 别人写的node.js模块
```



# 模块： node.js内置模块

EventEmitter

​    观察者模式： addEventListener     removeEventListener

  调用vs抛事件

​       关键在于不知道被通知者存在以及没有人听还能继续下去

# 非阻塞I/O

I/O就是Input/Output,一个系统的输入和输出

阻塞I/O和非阻塞I/O的区别就在于系统接收输入再到输出期间，能不能接收其他输入

理解非阻塞I/O的要点在于：1确定一个进行Input/Output的系统 2 思考在I/O过程中，能不能进行其他I/O

# 异步编程之callback

回调函数格式规范     error-first callback.       Node-style callback

第一个参数是error,后面的参数才是结果

# 事件循环

事件循环是非阻塞I/O的基础，是能够实现非阻塞I/O的关键

# 异步编程之promise

## promise

当前事件循环得不到的结果，但未来的事件循环会给到你结果

是一个状态机： pending ,fulfilled/resolved   rejected

## .then 和.catch

resolve状态的promise会回调后面的第一个.then

rejected状态的promise会回调后面的第一个.catch

任何一个rejected状态且后面没有catch的promise,都会造成浏览器/node环境的全局错误

执行then和catch会返回一个新的promise，该promise最终的状态根据then和catch的回调函数的执行结果决定

如果回调函数最终是throw,该promise是rejected状态

如果回调函数最终是return,该promise是resolved状态

但如果回调函数最终return了一个promise,该promise会和回调函数return的promise状态保持一致

Promise.all([])可以解决并发的异步调用

# 异步编程之async 和await

async/await

async function 是Promise的语法糖封装，是一个穿越事件循环存在的function

异步编程的终极方案——以同步的方式写异步

​    1await关键字可以暂停async function 的执行

​    2await关键字可以以同步的写法获取promise的执行结果

​    3 try-catch可以获取await所得到的错误

并行的异步任务：await Promise.all([interview(1), interview(2), interview(3)]);

# HTTP: 什么是HTTP

http是应用层协议，属于计算机五层网络协议之一，

计算机的5层网络： 应用层，运输层，网络层，数据链路层，物理层

一个网页请求，包含两次http包交换：1 浏览器向http服务器发送请求http包     2http服务器向浏览器返回http包

## http要做的事情：

​        解析进来的http请求报文

​       返回对应的http返回报文

# expresss

要了解一个框架，最好的方法是；了解它的关键功能，推导出它要解决的问题是什么

## 核心功能

路由

request/response简化：request:pathname,query等。    Response: send(),json(),jsonp()等

# koa

Koa的路由中间件Koa-mount

```js
核心功能： 1.比express更极致的request/response简化

ctx.status=200

ctx.body ="hello world"
2. 使用async function 实现的中间件
    有暂停执行的功能。      在异步的情况下也符合洋葱模型

```

```js
express vs koa
express门槛更低，koa更加强大优雅
express封装更多东西，开发更快速，koa可定制性更高
```

# RPC调用：什么是RPC调用

Remote Procedure Call(远程过程调用)

和ajax有什么相同点？

都是计算机之间的网络通信

需要双方约定一个数据格式

和ajax有什么不同点？

不一定使用dns作为寻址服务

应用层协议一般不使用http

基于Tcp或者udp协议

## RPC调用

寻址/负载均衡

```js
ajax： 使用dns进行寻址
RPC: 使用特有服务进行寻址
```

TCP通信方式

```js
单工通信：只能单向通信
半双工通信：同一时间内，只能由一方向一方发送（轮番单工通信）
全双工通信：比较自由的通信方式，客户端服务器和服务端服务器可以自由通信
```

二进制协议

```js
ajax都是使用http协议
RPC使用二进制协议： 更小的数据包体积，更快的编解码速率
```

## RPC调用：node.js buffer编解码二进制数据包

