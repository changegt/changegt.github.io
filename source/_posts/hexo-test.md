---
title: hexo-test
date: 2018-02-09 00:03:34
tags: hexo
---

## hexo学习记录

### 1、安装hexo
```node
/*加载hexo包和相关工具*/

$ npm install hexo 

$ npm install hexo-server --save  //由于Hexo3.0将服务器模块独立了，所以需要引入
```

```node
/*初始化hexo项目*/

$ hexo init [folder]    //新建一个网站。如果没有设置 folder ，Hexo 默认在目前的文件夹建立网站。

$ hexo new [layout] <title> //新建一篇文章。默认使用 _config.yml 中的 default_layout 参数代替。如果标题包含空格的话，请使用引号括起来。

$ hexo generate      //生成静态文件。 简写 hexo g
```

```node
$ hexo server   
```
启动服务器，默认情况下，访问网址为： `http://localhost:4000/`

| 选项 | 描述 |
| ---- | ---- |
| `-p --port` | 重设端口 |
| `-s --static` | 只使用静态文件 |
| `-l --log` | 启动日记记录，使用覆盖记录格式 |

```node
/*其他*/

$ hexo deploy       //$ hexo d 部署网站。

$ hexo render <file1> [file2] ... //渲染文件。

$ hexo clean //清除缓存文件 (db.json) 和已生成的静态文件 (public)。
```

### 2、安装hexo主题

hexo官方主题：https://hexo.io/themes/

> 1、初始化一个hexo工程
> 2、选择一种主题，将文件down下来放入hexo工程的themes文件夹内 （或者进入themes后pull下主题）
> 3、修改下载下来的主题中的_config.yml配置文件，同时修改hexo工程路径下面的_config.yml文件的theme参数，改为你需要的主题名称

### 3、markdown学习

> hexo的bolg编写方式是markdown写法，所以需要学习一下markdown

### 4、编写文章

