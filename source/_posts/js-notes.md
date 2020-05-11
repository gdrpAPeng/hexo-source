---
title: js-notes
urlname: js-notes
date: 2020-05-11 02:37:36
tags:
---

js 笔记

<!-- more -->

ts：

抽象类：

不能被实例化，只能被继承

父类的抽象方法必须被子类继承

event loop
js 是单线程语言，所有异步都是通过同步的方式来实现的

执行机制：
分为同步任务，异步任务
又分为宏任务，微任务
宏任务执行完再执行微任务，微任务执行完再执行宏任务


bind、call、apply
- bind 和 call、apply 的区别
> bind 返回改变上下文的一个函数
>
> call、apply 改变函数的 this 上下文后直接执行函数
- call、apply 的区别
> apply 第二个参数是个数组

实现 bind
```
Function.prototype.myBind = function (obj, ...arg) {
    self = this
    return function() {
        // console.log(arguments, '==')
        let newP = arg.concat(...arguments)
        return self.apply(obj, newP)
    }
}

Function.prototype.myCall = function (obj, ...arg) {
    self = this
    // return function() {
        return self.apply(obj, [...arg])
    // }()
}
// 不使用 apply 实现
Function.prototype.ownCall = function(context, ...args) {
    const key = Symbol()
    context[key] = this
    const result = context[key](...args)
    delete context[key]
    return result
    // return function() {
    //     return obj[key](...arg)
    // }()
}

Function.prototype.ownBind = function(context) {
    const key = Symbol()
    context[key] = this
    return function() {
        return context[key]()
    }
}

const O = {
    a: 'In',
    test: function() {
        return this.a
    }
}
const OO = {
    a: 'OUT',
}

console.log(O.test.ownBind(OO)())
```


执行上下文：
- 变量、函数声明
- this 指向
- 赋值

多态：
- 同一个方法，不同对象，返回不同的结果

闭包：
> 闭包是指有权访问另一个
函数作用域中的变量的函数。创建闭包的常见方式，就是在一个函数内部创建另一个函数
- 返回一个函数
- 将函数当成参数
```
function fn() {
    var max = 10
    return function fun(x) {
        return x + max
    }
}
var f = fn()
var max = 100
f(1)
/*
* 函数作用域在创建的时候已经决定了，所以 fun 拿到的 max = 10，
* 因为 fun 里需要获取到 max， 所以执行完 fn 没有销毁上下文环境
*/
```