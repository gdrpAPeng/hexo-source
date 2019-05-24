---
title: hexo命令
urlname: hexo
date: 2019-05-24 09:43:29
tags:
---

## 常用命令

```c
// 创建新文章
hexo n [layout] '文章名'  =>  hexo new '文章名'  // 前者是后者的简写, layout 默认 post
// 发表草稿
hexo p => hexo publish
// 生成静态档案
hexo g => hexo generate
// 启动热更新预览, 默认是 http://localhost:4000
hexo s => hexo server
// 部署网站
hexo d => hexo deploy
```

<!-- more -->
## 服务器命令
```c
// 开启监听
hexo server
// 静态模式
hexo server -s
// 修改端口
hexo server -p 5000
// 自定义 ip
hexo server -i [ip]
// 清除缓存
hexo clean
// 生成静态网页
hexo g
// 部署
hexo d
```


