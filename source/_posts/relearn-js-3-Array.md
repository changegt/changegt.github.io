---
title: relearn-js-3-Array
date: 2018-04-25 22:17:48
tags: [js, ES5, ES6]
---

## 重新认识JS——step3

### 数组认识

#### 1、创建
```js
var arr1 = [];// [1,2]
var arr2 = new Array(1,2); //无参数的时候是空数组， 一个参数是length， 多个参数就是添加数组元素
var arr3 = Array(1,2);
```

**一个有趣的问题：如何快速创建一个长度为100的元素全是0的数组**
> a
```js
new Array(101).join(0).split('') //['0','0'.....100位]
```
> b
```js
//执行后a还是一个空数组，因为forEach方法对空数组执行的时候是不会执行回调函数的
var a = new Array(100); a.forEach( (val, index) => { a[index] = 0; } ) 

//使用apply方法将数组变为每个元素为undefined，不再是空数组，所以能使用forEach
var b = Array.apply(null, new Array(100)); b.forEach( (val, index) => { b[index] = 0; } ) 

//使用map , 虽然map不会检查空数组，但是还是需要需要转化为非空数组
var c = Array.apply(null, new Array(100)); console.log(c.map( (val, index) => { return 0; })) 
```
> c
```js
var a = new Array(100); for(var i=0; i<a.length; i++){a[i] = 0;}
```

