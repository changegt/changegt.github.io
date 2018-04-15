---
title: yyf-site-3
date: 2018-02-16 20:46:58
tags: [vue,vue-resource,vue-router]
---

## 个人后台建站第三弹————网易云音乐移动端demo

### 样式
<img src="../../images/music163-print.png" alt="">

### 1、页面 样式编写
使用了element-UI的组件去编写页面样式，其中他的tab组件有点坑，下面的active的bar是动态的去计算宽度，和位移位置，而且他的计算没有一个很好的额扩展，导致我修改了部分宽度的样式就导致了问题出现了。

### 2、接口问题
不得不吐槽一下，网易的接口数据真的不好获取，不能直接调用接口，所以我就把数据给扒了下来，直接在最后的接口api文件中引入对应的数据文件然后返回，在接口调用的时候一般都会用到**Promise去做处理**
```js
//获取音乐top10数据的接口，由于这个接口是post请求，而且会出现跨域问题，所以我直接把数据拷了下来
import vue from 'vue'
import {newsong} from './newsongData'
import Msg from '@/util/msg'
/**
 * 获取top10
 * @return {[type]} [description]
 */
const getNewSong = () => {
    return new Promise((resolve, reject) => {
        const returnArr = Msg.get(0, 'success');
        returnArr.result = newsong;
        resolve(returnArr);
        // vue.http.post('http://music.163.com/weapi/personalized/newsong').then(data => {
        //  resolve(data.data);
        // });
    });
}

export {
    getNewSong
}
```

### 3、其余部分尚未实现，有空再去实现
