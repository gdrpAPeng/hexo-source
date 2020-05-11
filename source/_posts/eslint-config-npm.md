---
title: 发布 eslint 配置 npm 包
urlname: eslint-config-npm
date: 2020-05-11 11:06:26
tags:
---

发布一个 eslint 配置 npm 包

<!-- more -->

## 制作一个包

- 新建一个文件夹命名为 eslint-config-myeslintconfig(name)
- npm init 初始化
- 新建 index.js 
```
module.exports = {
    globals: {
        MyGlobal: true
    },
    rules: {
        "no-var": "error",
    }
}
```

## 发布

- npm link 测试 (npm 会把该包关联到本机的 npm 全局安装目录下)
- 本地项目可以使用 npm link eslint-config-myeslintconfig 使用该包
- npm publish 发布到 npm (需要 login)

## 使用
在项目 .eslintrc 文件添加
```
"extends": ["myeslintconfig"] // eslint 会自动匹配 eslint-config 前缀
```






