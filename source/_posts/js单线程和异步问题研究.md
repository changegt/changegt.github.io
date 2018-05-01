---
title: js单线程和异步问题研究
date: 2018-04-16 16:37:00
tags:
---

### 1、js引擎机制
> **变量提升** js先解析代码中对象和函数，由于ES6前没有块级作用域的概念，只有全局作用域和函数作用域，所以解析的时候会将变量提升到所在作用域的顶端，同时赋值为undefined。

```js
console.log(a); // undefined
var a = 'a';
console.log(a); // a
console.log(c); // Uncaught ReferenceError: a is not defined ,a的作用域在函数b中
function b(){
	console.log(c); // undefined
	var c = 'c';
	console.log(c); // c
}
b()
```
> **函数提升** 函数的定义分为函数申明（function a(){}），函数表达式（var a = function(){}）和构造函数（new Function()），所以只有函数声明才能支持函数提升，其他两个都是属于变量提升， **同时函数的提升是优先于变量的提升**
```js
var a = function(){ console.log(1); } //顶部已经存在了a的函数，此时a的变量将a的函数覆盖了，所以下面执行的是a的变量函数

function a () { console.log(2); } //当前函数先于变量提升到顶部

a(); // 输入 1
```

### 2、js单线程

### 3、js异步
	setTimeout，setInterval等定时器，ajax等涉及http请求的


setTimeout异步机制 【3s时间】

代码执行到此时，将setTimeout的方法推入event table, 过了3秒后，setTimeout的方法被推入event queue中，然后查看当前主线程是否空闲，空闲就执行，不空闲就等到主线程空闲的时候才去执行


【event loop 事件循环】
1、浏览器js引擎解析的时候会将异步执行代码放入event table
2、异步任务在event table中注册函数，当满足条件之后，会被推入event queue
3、同步任务进入主线程后一直执行，直到主线程空闲的时候，才会执行event queue中查看是否有可执行的异步任务，有的话就被推入主线程中执行

```js
console.log('start');
new Promise(function(resolve, reject){
	console.log(0);
	setTimeout(function(){
		console.log(1);
		resolve();
	});
}).then(function(){
	console.log(2);
})
console.log(3);
```


宏任务：整体的js代码，setTimeout，setInterval
微任务：Promise，process.nextTick

宏任务先执行，执行结束后，查看是否有微任务，有的话执行，没有的话执行新的宏任务