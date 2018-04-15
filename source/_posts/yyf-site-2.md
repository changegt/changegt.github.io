---
title: yyf-site-2
date: 2018-02-15 23:55:32
tags: [vue, vue-router, element-UI, Promise]
---

## 个人后台建站第二弹————主面板

### 样式
<img src="data:image/png;base64,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">

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