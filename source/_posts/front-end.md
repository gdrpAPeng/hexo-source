---
title: 前端面试题
urlname: front-end
date: 2019-05-28 14:21:07
tags:
---

整理了一下之前面试遇到的题  2019年三月份

[CSS 篇](#CSS)

[JS 篇](#JS)

[VUE 篇](#VUE)

[算法 篇](#算法)

[其他](#其它)

<!-- more -->

## CSS

##### 1、div 水平垂直居中
```css
  /* 定位 */
  position: absolute;
  top: 50%;
  left: 50;
  transform: translate(-50%, 50%);
  /* flex 布局 */
  display: flex;
  justify-content: center;
  align-items: center;
```

##### 2、css 盒模型
* box-sizing: content-box; (标准模型)
 width = content
* box-sizing: border-box; (IE盒模型)
 width = content + padding + border


##### 3、inline 和 inline-block 的区别
 * inline 只能设置左右 margin、padding, 不能设置 width 和 height
 * inline-block 生成一个块级别框，但是框的行为跟内联元素一样

##### 4、css 中使用过哪些图片替换方法，如何选择使用
##### 5、link 跟 @import 的区别
 * link 是 HTML 提供的标签
 * link 引用的 css 会同时被加载，而 import 引用的 css 会等到页面全部被下载完后再加载
 * import 老版本浏览器不支持
 * DOM可控性区别：无法使用 dom 方法插入样式

##### 6、css 样式优先级
 内联样式 > ID 选择器 > 类选择器 = 属性选择器 = 伪类选择器 > 标签选择器 = 伪元素选择器

## JS

##### 1、async/await 跟 promise 的区别
 * Promise 代码完全都是 Promise 的 API (then、catch 等)
 * async/await 是 Generator 函数的语法糖

##### 2、闭包的特性合优缺点
* 什么是闭包?
 闭包就是能够读取其他函数内部变量的函数 (来源: https://blog.csdn.net/yingzizizizizizzz/article/details/72887161)
* 优点
 读取函数内部的变量
 让局部变量保存在内存中，实现变量数据共享
* 缺点
 * 由于闭包会使得函数中的变量都被保存在内存中，内存消耗很大，所以不能滥用闭包，否则会造成网页的性能问题，在IE中可能导致内存泄露。解决方法是，在退出函数之前，将不使用的局部变量全部删除
 * 闭包会在父函数外部，改变父函数内部变量的值。所以，如果你把父函数当作对象（object）使用，把闭包当作它的公用方法（Public Method），把内部变量当作它的私有属性（private value），这时一定要小心，不要随便改变父函数内部变量的值。
 * 来源： https://www.jianshu.com/p/8376170fb228

##### 3、原型、原型链，有什么特点
 关于原型其实文章还是蛮多的，看着也有点迷糊 https://segmentfault.com/a/1190000008959943

##### 4、如何判断对象类型
 typeof、 instanceof 看 https://www.jianshu.com/p/5be700ee60df
##### 5、宿主对象和原生对象的区别
 * 原生对象： Object、Function、Array、String、Boolean、Number、Date、RegExp、Error、EvalError、RangeError、ReferenceError、SyntaxError、TypeError、URIError、Global
 * 宿主对象： 有宿主提供的对象，在浏览器中window对象以及其下边所有的子对象(如bom、dom等等)，在node中是globla及其子对象，也包含自定义的类对象。【何为“宿主对象”？  在web中，ECMAScript中的“宿主”当然就是我们网页的运行环境，即“操作系统”和“浏览器”。所有非本地对象都是宿主对象（host object），即由 ECMAScript 实现的宿主环境提供的对象。】

##### 6、call 和 apply 的区别
 * .call(this, arg1, arg2, arg3)
 * .apply(this, arguments)

##### 7、什么是闭包
##### 8、解释 js 的 同源策略， 如何实现跨域访问
* 同源：
> 如果两个页面拥有 相同 的 协议（protocol），端口（如果指定），和 主机，那么这两个页面就属于同一个源（origin）。 (协议、域名、端口)
* 跨域
 * jsonp
 * iframe
 * 跨域资源共享(CORS)
 * nginx 代理跨域

##### 9、== 和 === 的区别
 看: https://blog.csdn.net/chenchunlin526/article/details/78850171

##### 10、数组方法 pop, push, unshift, shift
 * pop: 删除数组最后一个元素，返回删除的那个元素
 * push: 往数组结尾添加元素
 * shift: 删除数组第一个元素，返回该元素
 * unshift: 往数组前添加元素

##### 11、事件委托是什么
 事件委托就是利用冒泡的原理，把事件加到父元素或祖先元素上，触发执行效果。

 优点: 提高性能，显著提高事件处理速度，减少内存占用

```js
var btn6 = document.getElementById("btn6");
document.onclick = function(event){
  event = event || window.event;
  var target = event.target || event.srcElement;
  if(target == btn6){
    alert(btn5.value);
  }
}
```

##### 12、split()、join() 的区别
##### 13、例举 3 种强制类型转换和 2 种隐式类型转换
##### 14、js 的原始类型和引用类型有哪些
 Undefined、Null、Boolean、String、Number、Symbol、Object

##### 15、1.toString() 会输出什么
 * 1.toString() => 报错
 * 1..toString() => "1"
 * 1.0.toString() => "1"

##### 16、什么是回调函数？有哪些缺点？如何解决回调地狱？
 * 在JavaScript中，回调函数具体的定义为：函数A作为参数(函数引用)传递到另一个函数B中，并且这个函数B执行函数A。我们就说函数A叫做回调函数。如果没有名称(函数表达式)，就叫做匿名回调函数。因此callback 不一定用于异步，一般同步(阻塞)的场景下也经常用到回调，比如要求执行某些操作后执行回调函数。
 * 如何解决回调地狱
 * - 保持代码简短
 * - 模块化
 * - 处理每一个错误

##### 17、如何实现一个可设置过期时间的 localStorage

## VUE

##### 1、vue 常见报错
##### 2、父组件通过 props 给子组件传值，子组件能否修改该值，会有什么影响
 做了个小测试，看: http://note.youdao.com/noteshare?id=a1031ade751ba1c2526e7df9e7ecd3e0

##### 3、vue 双向数据绑定原理
 https://juejin.im/entry/5923973da22b9d005893805a

##### 4、v-if 和 v-show 指令有什么相同和不同
 v-if 直接从 dom 树上删除或重建元素节点, v-show 只是修改 display 的值
 v-if 高消耗，不适合做频繁切换

##### 5、<keep-alive> 有什么作用
 keep-alive 是 Vue 内置的一个组件，可以使被包含的组件保留状态，或避免重新渲染

##### 6、简述 vue 里面的虚拟 dom


## 算法

##### 假设你正在爬楼梯，需要 n 步你才能到达顶部，但每次你只能爬一步或者两步，你能有多少种不同的方法爬到楼顶？

## 其它

##### 项目部署流程
##### 服务器部署项目常见错误，一般根据什么来判断
##### git 不常用的命令
##### 什么情况下会遇到跨域，怎么解决
##### webpack 的作用
 看这篇吧 (什么是WebPack，为什么要使用它) https://www.jianshu.com/p/d745b94ae920


---

欢迎提建议，意见，谢谢