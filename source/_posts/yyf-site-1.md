---
title: yyf-site-1
date: 2018-02-14 15:25:22
tags: [vue,vue-router,element-UI]
---

## 个人后台建站第一弹————登录
使用技术栈：**vue**、**vue-router**、**element-UI**、**vuex**、**Promise**、**vue-resource**

### 登录实现login

#### 1、element-UI编写登录页面
`html`
```html
    <template>
        <el-form :model="form" status-icon :rules="validate" label-width="0" class="login-box">
            <!--model绑定表单 rules绑定校验 label-width el-input的label设置，可以不设置-->
            <h3 class="title">系统登录</h3>

            <el-form-item prop="username">
                <el-input type="text" v-model="form.username"></el-input>
            </el-form-item>

            <el-form-item prop="password">
                <el-input type="password" v-model="form.password"></el-input>
            </el-form-item>

            <el-form-item class="w100">
                <el-button type="primary" @click="submit" class="w100">login</el-button>
            </el-form-item>

        </el-form>
    </template>
```

`js`
```js
    import LoginApi from '../api/loginApi.js'
    export default {
        name: 'Login',
        data () {
            var validateUsername = (rule, value, callback) => { //验证用户名
                if (value === '') {
                  callback(new Error('请输入用户名'));
                } else if (value !== 'admin') {
                  callback(new Error('请输入正确的用户名'));
                } else {
                  callback();
                }
            };

            var validatePassword = (rule, value, callback) => { //验证密码
                if (value === '') {
                  callback(new Error('请输入密码'));
                } else if (value !== 'admin') {
                  callback(new Error('请输入正确的密码'));
                } else {
                  callback();
                }
            };

            return {
                form: {
                    username: 'admin',
                    password: 'admin'
                },
                validate : {
                    username: [
                        { required: true, message: '请输入用户名', trigger: 'blur' },
                        { validator: validateUsername}
                    ],
                    password: [
                        { required: true, message: '请输入密码', trigger: 'blur' },
                        { validator: validatePassword}
                    ]
                }
            };
        },
        methods: {
            submit () {
                LoginApi({ //登录请求，使用easy-mock模拟接口，登录成功后进入页面
                    username: this.form.username,
                    password: this.form.password
                }).then(data => {
                    if(data.errorCode == 0){
                        this.$router.push('/hello');
                    }else{
                        this.$message.error('登录失败');
                    }
                });
            },
        
        }
    }
```

`登录窗口表现`
<img src="data:image/png;base64,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">