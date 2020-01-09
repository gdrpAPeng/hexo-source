---
title: 笔记
urlname: notes
date: 2019-12-09 15:47:38
tags:
---

每天记录一下

<!-- more -->

> 记录一下每天看博客的一两句总结

#### 前端模块化
- 每个文件都是一个模块，都有自己的作用域

#### ES Module 和 CommonJs 的区别
- ES Module 是对值的引用 (可以当成全局变量来用)
- CommonJs 是对值的拷贝

## webSocket

### socket.io

这里使用 socket.io 进行连接

github：[https://github.com/socketio/socket.io-client](https://github.com/socketio/socket.io-client)

文档地址：[https://socket.io/get-started/chat/#Homework](https://socket.io/get-started/chat/#Homework)

- 客户端

```js
    <input id="input" />
    <button id="btn">提交</button>

     <script src="https://cdn.jsdelivr.net/npm/socket.io-client@2/dist/socket.io.js"></script>

    <script>
      //  三种获取 io 对象的方法
      //  cdn  import  require
      //  import io from "socket.io-client";
      //  const io = require('socket.io-client')

      // 连接 socket ，这里连接上 node 服务器
      const socket = io("http://localhost:3000");

      // 连接成功
      socket.on("connect", function(e) {
        console.log("connect");
      });
      // 断开连接
      socket.on("disconnect", function() {
        console.log("disconnect");
      });
      socket.on("info", function(data) {
        console.log(data, 'chat');
      });
      const input = document.querySelector("#input");
      document.querySelector("#btn").addEventListener("click", function(e) {
          //    触发广播给服务端推送一条消息
        socket.emit("info", input.value);
      });
    </script>
```

- 服务端

```js
const app = require("express")();
const http = require("http").createServer(app);
const io = require("socket.io")(http);

app.get("/", function(req, res) {
  res.send("app success");
});

io.on("connection", function(socket) {
  // 处于连接状态
  // 监控客户端 广播 emit
  socket.on("info", function(msg) {
    // 利用 emit 给客户端推送消息
    io.emit("info", msg);
  });
});

http.listen(3000, function() {
  console.log("listen 3000");
});
```
