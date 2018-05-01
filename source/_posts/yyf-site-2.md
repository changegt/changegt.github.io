---
title: yyf-site-2
date: 2018-02-15 23:55:32
tags: [vue, vue-router, element-UI, Promise]
---

## 个人后台建站第二弹————主面板

### 样式
<img src="../../images/left.png">

### 1、路由配置
```js
import Vue from 'vue'
import Router from 'vue-router'
import helloWorld from '@/components/helloWorld'
import login from '@/views/login'
import main from '@/views/main'
import welcome from '@/views/homepage/welcome'
import theVue from '@/views/frames/theVue'

Vue.use(Router)

const arr = [
  {
    name: 'helloWorld',
    component :helloWorld
  },
  {
    name:'main',
    component:main
  },
  {
    name:'welcome', //欢迎页面
    component:welcome
  },
  {
    name:'theVue', //vue框架
    component:theVue
  },
];


const returnArr = [];
arr.forEach((item) => {
  item.path = '/'+item.name;
  returnArr.push(item);
})

export default new Router({
  routes: returnArr
})
```

### 2、主页面配置

```html
<template>
    <el-container>
        <el-aside width="250px">
            <left active="/welcome"></left>
        </el-aside>
        <el-main>
            <div class="welcome-box">
                <a target="_blank" href="https://changegt.github.io/public/index.html"><img src="../../assets/github-logo.jpg" alt=""></a>
            </div>
        </el-main>
    </el-container>
</template>

<script type="text/javascript">
    import left from '@/views/left.vue'
    export default {
        name : 'welcome',
        data () {
            return {

            };
        },
        methods: {
            
        },
        components: {
            left
        }
    }
</script>
```

### 3、左侧bar结构
```html
<template>
        <el-menu
            :default-active="active" 
            class="el-menu-vertical-demo"
            @open="handleOpen"
            router
            @close="handleClose">
            <el-submenu index="0" class="submenu-item tal">
                <template slot="title">
                    <i class="el-icon-bell"></i>
                    <span>主页</span>
                </template>
                <el-menu-item-group>
                    <el-menu-item index="/welcome">欢迎</el-menu-item> <!--路由-->
                </el-menu-item-group>
                <el-menu-item-group>
                    <el-menu-item index="0-2">文章</el-menu-item>
                </el-menu-item-group>
            </el-submenu>

            <el-submenu index="1" class="submenu-item tal">
                <template slot="title">
                    <i class="el-icon-menu"></i>
                    <span>前端</span>
                </template>
                <el-menu-item-group>
                    <el-menu-item index="/theVue">框架</el-menu-item>
                </el-menu-item-group>
                <el-menu-item-group>
                    <el-menu-item index="1-2">工具</el-menu-item>
                </el-menu-item-group>
                <el-menu-item-group>
                    <el-menu-item index="1-3">node框架</el-menu-item>
                </el-menu-item-group>
            </el-submenu>

            <el-submenu index="2" class="submenu-item tal">
                <template slot="title">
                    <i class="el-icon-picture"></i>
                    <span>多媒体</span>
                </template>
                <el-menu-item-group>
                    <el-menu-item index="2-1">视频</el-menu-item>
                </el-menu-item-group>
                <el-menu-item-group>
                    <el-menu-item index="2-2">音频</el-menu-item>
                </el-menu-item-group>
                <el-menu-item-group>
                    <el-menu-item index="2-3">图片</el-menu-item>
                </el-menu-item-group>
            </el-submenu>
            
            <el-submenu index="3" class="submenu-item tal">
                <template slot="title">
                    <i class="el-icon-setting"></i>
                    <span>其他</span>
                </template>
                <el-menu-item-group>
                    <el-menu-item index="3-1">设置</el-menu-item>
                </el-menu-item-group>
            </el-submenu>
        </el-menu>
</template>

<script type="text/javascript">
    export default {
        name : 'left',
        props: ['active'],
        data () {
            return {
            };
        },
        methods: {
            handleOpen () {

            },
            handleClose () {

            }
        }
    }
</script>

<style scoped>
    .tal{
        text-align: left;
    }
    .el-menu-item{
        padding-left: 80px!important;
    }
</style>
```

### 4、export、export default、import
> export 和 export default均用于导出常量，函数，文件，模块
> export 导出的文件，在import引入的时候需要用到 **{ }**
> export 导出默认，只能**导出一个**
> import 引入