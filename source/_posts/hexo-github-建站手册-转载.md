---
title: hexo github 建站手册
date: 2018-11-14 12:59:28
categories:
- Hexo
tags:
- Hexo
- github.io
---
### 前言
之前也建立过个人博客，但是没怎么写，加上服务器到期，也就废置了。这次再度萌生了写博客的想法，是因为想记录一下阅读vue源码的笔记，希望对自己和他人都能有所益处。<br>
写博客，需要一个博客网站，这样的选择很多。
<!-- more -->
- 笔记类，如**有道云笔记**，它严格来说不算博客网站，但是有笔记的功能很完善，我之前有很多东西就是写在上面的。
- 博客网站，如**CSDN**、**博客园**。这类网站有成熟的博客机制，也支持自定义皮肤等个性化配置，开箱即用。
- 技术网站文章类，如**简书**、**segmentfault**。这类网站以技术分享为主，有分类和推荐机制，对于增加热度很有帮助。
- 自己建站，如**WordPress**、**firekylin**。需要自己购买服务器和域名，甚至还要自己搭建框架。不过内容都属于自己，有逼格，也适合添加在简历上。

有了以上分类，就可以根据自己的需求来选择合适的做法，我理了下我的需求——我完全是觉得好玩和喜欢折腾才选择了用`Hexo`和`Github`来搭建博客网站，事实上无论从便利性、可靠性或是其它方面，比它更好的选择都有很多。继续下去之前，说一下Hexo比较显著的缺点。
1. 博客是用md编写然后打包发布成静态html资源，也就是说只能通过编辑md文件来修改文章，而不能通过网页直接编辑修改。
2. 定时发布等高级功能没有，起码我现在还没发现。
3. 配置虽然简单，但是编辑配置文件的方式不太友好。

优点的话，可能是可以生态静态网站.....吧。
### 介绍
下面简单介绍一下二者。默认本文读者已对`node`、`git`、`github`有基础了解。
> Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

> github应该不用介绍，这里说一下`github.io`，是github为用户免费提供静态资源访问的机制。为仓库创建`gh-pages`分支或者指定`master`分支下`docs`目录为根目录或其它，即可通过`username.github.io/repository_name`访问对应内容。创建名为`username.github.io`的仓库后则可直接访问`username.github.io`。

### 步骤
1. 在github上创建`your-github-name.github.io`的仓库，拉取到本地后创建`hexo`分支。
2. 安装hexo
```sh
npm install -g hexo-cli
```
3. 初始化
```sh
# Tips: 初始化之前需要清空文件夹，否则会失败。可以剪切.git，初始化后粘贴，也可手动重新关联，详情搜索git remote
hexo init
```
4. 运行
``` sh
hexo server
#运行成功后可访问http://localhost:4000查看
```
5. 部署

&emsp;&emsp;配置文件在根目录下的`_config.yml`，找到`deploy`字段

&emsp;&emsp;修改前
```yml
# Deployment 
## Docs: http://hexo.io/docs/deployment.html 
deploy:   
  type:
```
&emsp;&emsp;修改后
```yml
# Deployment 
## Docs: http://hexo.io/docs/deployment.html 
deploy:   
  type: git
  repository: git@github.com:your/your.github.io.git #你的仓库地址
  branch: master
```

