---
title: messy-js-note
date: 2018-04-22 23:49:42
tags: [js, es5, es6, es7]
---

## js相关知识点的杂记

### 1、instanceof和typeof的区别
instanceof 运算符用来测试一个对象在其原型链中是否存在一个构造函数的 prototype 属性。【Object.getPrototypeOf(b) == a.protptype】

<img src="../../images/messy/messy-js-img1.png">
1、该实例中a为一个构造函数（构造函数记得要首字母大写，哈哈哈），A存在prototype的原型对象
2、同时A.prototype原型对象中存在constructor属性，是一个指向构造函数A的指针
3、实例b有一个\_\_proto\_\_的属性指向构造函数的原型对象

-----------------------
<img src="../../images/messy/messy-js-img2.png">
4、万物皆对象，任何实例的\_\_proto\_\_属性都是指向其构造函数的的原型对象
	除了null和undefined外，String，Number，Boolean和其他构造函数等都是存在__proto__属性，而且最后原型链终端是Object的原型对象
-----------------------

	比如构造函数A的原型对象的__proto__指向的就是Object的原型对象
-----------------------

<img src="../../images/messy/messy-js-img3.png">
5、Object的原型对象的__proto__指向的就是null，但是本质上null也是一个对象


注意：
1、原型对象可以修改
<img src="../../images/messy/messy-js-img4.png">
2、\_\_proto\_\_属性也可以修改