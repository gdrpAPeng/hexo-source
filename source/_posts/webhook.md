---
title: webhook 实现项目自动部署
urlname: webhook
date: 2019-11-05 16:28:47
tags:
---

## 利用 github webhook 实现项目自动部署

[项目地址 https://github.com/gdrpAPeng/webhooks](https://github.com/gdrpAPeng/webhooks)

<!-- more -->

将接口地址挂到 github 仓库上的 webhooks 之后，触发更新条件 github 就会给你发送如下一堆数据，然后你就可以根据自己的需求为所欲为为所欲为为所欲为了
```js
{
  "ref": "refs/heads/master",
  "repository": {
    "name": "webhooks",
    "full_name": "gdrpAPeng/webhooks",
    "private": false,
    "html_url": "https://github.com/gdrpAPeng/webhooks",
    "description": "自动化部署工程",
    "git_url": "git://github.com/gdrpAPeng/webhooks.git",
    "clone_url": "https://github.com/gdrpAPeng/webhooks.git",
    "svn_url": "https://github.com/gdrpAPeng/webhooks",
    "default_branch": "master",
    "stargazers": 0,
    "master_branch": "master"
  }
}
```