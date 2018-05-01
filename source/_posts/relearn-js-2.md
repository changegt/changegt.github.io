---
title: relearn-js-2
date: 2018-04-22 23:38:05
tags: [relearnJS, js, es5, es6, es7]
---

## 重新认识JS——step1

### 浏览器对象

#### 1、window对象：浏览器打开的窗口或者是文档中存在frame和iframe的时候的指向对象

a、常用的window属性：
>+ document, history, navigator, location(引用History等对象)
>+ innerHeight, innerWidth(窗口文档显示宽高：即普通网页的宽高)
>+ outerWidth, outerHeight(窗口的外部高度：即浏览器宽度) 
>+ opener(返回创建窗口的引用)
>+ parent 父窗口， self 当前窗口的引用 top 返回最顶层的先辈窗口
>+ screenLeft,screenTop,screenX,screenY


**opener**	[就是被创建窗口会有一个opener属性，指向创建新窗口的window]

<img src="../../images/relearn/relearn-js-img4.png">


b、常用方法

<img src="../../images/relearn/relearn-js-img5.png">

#### 2、Navigator对象：包含浏览器信息的对象

常用：userAgent

<img src="../../images/relearn/relearn-js-img6.png">

#### 3、Screen对象：包含有关客户端显示屏幕的信息。

#### 4、History对象：包含用户访问过得对象
方法： back （放回上一个url），forward（去下一个存在的url，无的话不执行）， go（以当前页面为index=0进行跳转，上一个页面传参-1，下一个页面传参1，下两个页面传参2）

history.go() 相当于刷新当前页面

#### 4、Location对象：包含当前URL的信息