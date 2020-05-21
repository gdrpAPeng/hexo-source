---
title: Babel 使用
urlname: babel-notes
date: 2020-05-12 22:43:32
tags:
---
## Babel是一个JavaScript编译器
Babel是一个工具链，主要用于将ECMAScript 2015+版本的代码转换为向后兼容的JavaScript语法，可以使之运行在当前和旧版本的浏览器或其他环境中
<!-- more -->

[babel 文档](https://www.babeljs.cn/docs/)
>Babel 是一个 JavaScript 编译器，用于将 ECMAScript 2015+ 版本的代码转换为向后兼容的 JavaScript 语法，以便能够运行在当前版本和旧版本的浏览器或其他环境中。简单来说 Babel 的工作就是：
- 语法转换
- 通过 Polyfill 的方式在目标环境中添加缺失的特性
- JS 源码转换

```
{
  "presets": [
    "@babel/preset-flow",
    [
      "@babel/preset-env",
      {
        "targets": {
          "node": "8.10"
        },
        "corejs": "3", // 声明 corejs 版本
        "useBuiltIns": "usage"  // 按需加载 polyfill 
        /*
        false：此时不对Polyfill 做操作，如果引入 @babel/polyfill 则不会按需加载，会将所有代码引入
        
        usage：会根据配置的浏览器兼容性，以及你代码中使用到的 API 来进行 Polyfill ，实现按需加载
                
        entry：会根据配置的浏览器兼容性，以及你代码中使用到的 API 来进行 Polyfill ，实现按需加载，不过需要在入口文件中手动加上import ' @babel/polyfill'
        */
      }
    ]
  ]
}
```