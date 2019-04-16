---
title:  利用hexo搭建个人博客
date:  2019-03-31 21:15:40
tags:  hexo

categories: hexo_categories
---



## Hexo简介

Hexo是一款基于Node.js的静态博客框架，依赖少易于安装使用，可以方便的生成静态网页托管在GitHub和Coding上，是搭建博客的首选框架。先安装nodejs,windows系统的百度下载安装包安装[nodejs](https://nodejs.org/en/download/),linux:

```bash
sudo apt-get install nodejs
sudo apt-get install npm
```

检查安装是否成功：

```bash
node -v
npm -v
```

教程分三个部分:

- 第一部分：hexo的初级搭建以及常见错误的解决方法
- 第二部分：hexo的基本配置，更换主题，以及相关美化
- 第三部分：hexo添加各种功能，包括搜索的SEO，阅读量统计，访问量统计和评论系统等



## 第一部分
hexo的初级搭建还有部署到github page上，以及个人域名的绑定。

1. 安装Hexo
2. 发布文章

### 1.安装Hexo

```bash
npm install -g hexo-cli
```

> 安装完成以后使用　hexo -v查看是否安装成功

然后创建博客

```bash
hexo init blog
```

上面的blog就博客的根文件，名字可以自己随便取一个。创建成功以后进入blog文件夹,安装npm插件

```bash
cd ./blog
npm install
```

在linux系统中安装插件需要给npm赋予权限： <!-- more -->

```
sudo chown -R $USER:$GROUP ~/.npm
sudo chown -R $USER:$GROUP ~/.config
```

安装完成以后，文件内各文件夹的作用：

- node_modules: 依赖包

- public：存放生成的页面

- scaffolds：生成文章的一些模板

- source：用来存放你的文章

- themes：主题

- ** _config.yml: 博客的配置文件**

  

hexo 常用命令:

```
hexo generate  //生成静态文件
hexo clean //删除静态文件以及缓存
hexo deploy　//部署
hexo init  //创建一个新的hexo文件夹
hexo publish //发布文章
```

启动hexo server:

```
hexo g
hexo server
```

### 启动hexo时常见错误：

###### 1. 执行命令hexo server， 提示找不到该指令

解决方法: 在Hexo 3.0 后server被单独出来了，需要安装server，安装的命令如下：npm install hexo-server –save 安装此server后再试，问题解决。

###### 2.端口已被占用

解决方法：更换端口　**hexo s -pid **pid为需要更换成其他的端口

###### 3 YAMLException: incomplete explicit mapping pair; a key node is missed; or followed by a non-tabulated empty line at line x ,column y

解决方案：

（1）出现这种情况，一般都是缺少空格，在:冒号之后要有空格！检查x行y列附近的冒号，其之后是否跟了空格。
 （2）仔细检查_config.yml文件中所有冒号后面的空格，格式很严格，必须是只有一个，半角。不管是多了还是少了都会报错，这是yml解释器所定义的语法。

## ２．主题安装

hexo官网提供了很多[主题](https://hexo.io/themes/index.html)，不过常用的就这么几个。这里安装的时非常流行的Next主题：

```
git clone https://github.com/iissnan/hexo-theme-next themes/next
```

下载好以后解压到博客的theme文件夹下,修改博客站点配置文件_config.yml 注意:冒号后一定要有一个空格，不要会报错。

![a.png](/imgs/a.png)