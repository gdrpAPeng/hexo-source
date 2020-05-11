---
title: js 题库
urlname: js-question-bank
date: 2020-01-17 17:56:46
tags:
---

到处 copy 的一些 js 基础题

<!-- more -->

1. undefined 和 null 有什么区别？
    
   null 表示一个'无'的对象, undefined 表示一个 '无'的原始值
  
   Number(null) === 0 , Number(undefined) === NaN 

   ---

2. && 运算符能做什么
3. || 运算符能做什么

    && 逻辑与: a && b, 若 a 为 true, 则返回 b, 否则返回 a 

    || 逻辑或: a || b, 若 a 为 true, 则返回 a

    !  逻辑非, !a, 若 a 可转换为 true, 则返回 false, 否则返回 true

4. 使用 + 或一元加运算符是将字符串转换为数字的最快方法吗？

    将字符串转换为数字的几种方法
    
    - parseInt - 应该是最快的
    - parseFloat - 可以解析十六进制
      > parseInt("44.jpg"); // returns 44
      >
      > parseFloat("44.jpg"); // returns 44
    - Number - 最慢
    - 一元运算符
      > '1.23' * 1 // return 1.23
      >
      > '55' - 0 // return 55
      >
      >  \+ '12' // return 12

5. DOM 是什么？

   DOM 是 Document Object Model(文档对象模型)的缩写

   在浏览器渲染机制中，浏览器解析HTML标签，构建DOM树

   > 文档对象模型 (DOM) 是HTML和XML文档的编程接口。 
   >
   > 它提供了对文档的结构化的表述，并定义了一种方式可以使从程序中对该结构进行访问，从而改变文档的结构，样式和内容。


6. 什么是事件传播?

   js 的事件传播流程主要分为三个阶段： 事件捕获，处于目标，事件冒泡

   document -> html -> body -> div -> p -> div -> body -> html -> document

7. 什么是事件冒泡？

    > 当事件发生时，该事件首先被最内层元素接受到，然后依次向外层元素传播。（从下向上）
    >
    > 事件会从最内层的元素开始发生，一直向上传播，直到document对象

   p -> div -> body -> html -> document

8. 什么是事件捕获？

    > 当事件发生时，该事件首先被最外层元素接受到，然后依次向内层元素传播。（从上向下）
    >
    > 与事件冒泡相反，事件会从最外层开始发生，直到最具体的元素

    document -> html -> body -> div -> p
---
> 冒泡和捕获两种事件传播方式,
>
> 用哪种事件传播方式完全是我们自己说了算的，我们可以使用
>
> addEventListener(type, listener, useCapture) // useCapture 为 false 则是冒泡
---

9. event.preventDefault() 和 event.stopPropagation()方法之间有什么区别？
    
   example: 点击 a 标签

   - preventDefault : 阻止默认事件 (在这里指的是 a 标签的跳转行为)
   - stopPropagation : 用于'冒泡'传播方式, 阻止向上继续传播
   - return false : 相当于 preventDefault + stopPropagation
   

10. 如何知道是否在元素中使用了event.preventDefault()方法？
     
    event.defaultPrevented

11. 为什么此代码obj.someprop.x会引发错误?

    ```
    let obj = {}
    obj.someprop // undefined
    obj.someprop.x // undefined 没有属性 x
    ```

12. 什么是event.target？
13. 什么是event.currentTarget？
    
    target 是事件元素

    currentTarget 事件的监听元素

14. == 和 === 有什么区别？

    - === 严格相等

        1. 比较前不进行隐式转换
        2. 类型、值 一样
           - 非 number 类型, 两个变量全等
           - number : 两个都不是 NaN, 且数值相同(包括 +0 和 -0), 则全等
    - == 非严格相等

      比较前转换为相同类型的值 ('隐式转换' 敲一下重点)

15. 为什么在 JS 中比较两个相似的对象时返回 false？

    对象是引用类型，实际上比较的是引用地址

    > JavaScript 中共有 6 种基本数据类型：Undefined、Null、Boolean、Number、String、Symbol (new in ES 6) 
    >
    >  Object 类型。细分的话，有：Object 类型、Array 类型、Date 类型、RegExp 类型、Function 类型 等

16. !! 运算符能做什么？

    将变量转换为布尔值

17. 如何在一行中计算多个表达式的值？
18. 什么是提升？
19. 什么是作用域？
20. 什么是闭包？
21. JavaScript中的虚值是什么？
22. 如何检查值是否虚值？
23. 'use strict' 是干嘛用的？
24. JavaScript中 this 值是什么？
25. 对象的 prototype 是什么？
26. 什么是IIFE，它的用途是什么？
27. Function.prototype.apply方法的用途是什么？
28. Function.prototype.call方法的用途是什么？
29. Function.prototype.apply 和 Function.prototype.call 之间有什么区别？
30. Function.prototype.bind的用途是什么？
31. 什么是函数式编程? JavaScript的哪些特性使其成为函数式语言的候选语言？
32. 什么是高阶函数？
33. 为什么函数被称为一等公民？
34. 手动实现Array.prototype.map方法
35. 手动实现Array.prototype.filter方法
35. 手动实现Array.prototype.reduce方法
37. arguments 的对象是什么？
38. 如何创建一个没有 prototype(原型) 的对象？
39. 为什么在调用这个函数时，代码中的b会变成一个全局变量?
40. ECMAScript是什么？
41. ES6或ECMAScript 2015有哪些新特性？
42. var,let和const的区别是什么
43. 什么是箭头函数？
44. 什么是类？
45. 什么是模板字符串？
46. 什么是对象解构？
47. 什么是 ES6 模块？
48. 什么是Set对象，它是如何工作的？
49. 什么是回调函数？
50. Promise 是什么？
51. 什么是 async/await 及其如何工作？
52. 展开运算符和Rest运算符有什么区别？
53. 什么是默认参数？
54. 什么是包装对象（wrapper object）？
55. 隐式和显式转换有什么区别？
56. 什么是NaN？ 以及如何检查值是否为 NaN？
57. 如何判断值是否为数组？
58. 如何在不使用%模运算符的情况下检查一个数字是否是偶数？
59. 如何检查对象中是否存在某个属性？
60. AJAX 是什么？
61. 如何在JavaScript中创建对象？
62. Object.seal 和 Object.freeze 方法之间有什么区别？
63. 对象中的 in 运算符和 hasOwnProperty 方法有什么区别？
64. 有哪些方法可以处理javascript中的异步代码？
65. 函数表达式和函数声明之间有什么区别？
66. 调用函数，可以使用哪些方法？
67. 什么是缓存及它有什么作用？
68. 手动实现缓存方法
69. 为什么typeof null返回 object？ 如何检查一个值是否为 null？
70. new 关键字有什么作用？
71. 什么时候不使用箭头函数? 说出三个或更多的例子？
72. Object.freeze() 和 const 的区别是什么？
73. 如何在 JS 中“深冻结”对象？
74. Iterator是什么，有什么作用？
75. Generator 函数是什么，有什么作用？


