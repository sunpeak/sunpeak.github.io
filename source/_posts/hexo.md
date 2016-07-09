---
title: 使用Hexo搭建git博客
date: 2016-07-09 13:39:05
tags: ["github pages","hexo","hexo-theme-next","markdown"]
categories: "hexo"
---
## 技术说明
* github pages，由github提供的免费空间
* Hexo，基于Node.js开发的快速、简单和强大的博客框架，支持markdown格式。官网 http://hexo.io
* hexo-theme-next，hexo配套的主题，目前在github上star最多。官网 http://theme-next.iissnan.com/

## 安装准备
* node.js  
* git

## hexo安装
``` bash
全局安装hexo框架
$ npm install -g hexo

初始化hexo工作空间
$ mkdir your-hexo-site
$ cd your-hexo-site
$ hexo init
```

## next安装
``` bash
$ cd your-hexo-site
$ git clone https://github.com/iissnan/hexo-theme-next themes/next
```

## hexo配置
在 Hexo 中有两份主要的配置文件，其名称都是 _config.yml。 
其中，一份位于站点根目录下，主要包含 Hexo 本身的配置；
另一份位于主题目录下，这份配置由主题作者提供，主要用于配置主题相关的选项。
为了描述方便，在以下说明中，将前者称为 站点配置文件， 后者称为 主题配置文件。
注：yml的格式,":"符号后有空格，格式不对，hexo构建会失败。

### 站点配置文件
``` bash
启用 NexT 主题
theme: next

设置语言环境
language: zh-Hans

设置 作者昵称
author: myname

部署
deploy:
  type: git
  repo: <repository url>
  branch: master

其他配置详见 http://theme-next.iissnan.com/getting-started.html
```

### 主题配置文件
```
选择 Scheme
scheme: Mist

设置菜单
menu:
  home: /
  archives: /archives
  categories: /categories
  tags: /tags
    
设置代码高亮主题
highlight_theme: night 

在首页显示文章的摘录并显示 阅读全文 按钮，可以通过以下方法：
auto_excerpt:
  enable: true
  length: 150

其他配置详见 http://theme-next.iissnan.com/theme-settings.html
```

### 添加「标签」页面
```
$ cd your-hexo-site
$ hexo new page tags

修改页面类型
编辑刚新建的页面，将页面的类型设置为 tags ，主题将自动为这个页面显示标签云。页面内容如下：
type: "tags"

禁用评论示例
comments: false
```

### 添加「分类」页面
```
$ cd your-hexo-site
$ hexo new page categories

修改页面类型
编辑刚新建的页面，将页面的类型设置为 categories ，主题将自动为这个页面显示分类。页面内容如下：
type: "categories"

禁用评论示例
comments: false
```



## github管理
### github仓库
登录github后，在首页点击「New Repository」
填写项目信息：
project name：myname.github.io
注：Github Pages的Repository名字是特定的，比如我Github账号是myname，那么我Github Pages Repository名字就是myname.github.io。


### 本地仓库
本地创建git仓库，并且创建hexo分支。
hexo分支用于保存hexo的工作空间，更新博客后都需要提交git来保存markdown格式的原文，这样可以在多台机器上共享hexo来发布博客。
master分支用于保存静态的博客页面，也就是最终呈现的博客html。
在your-hexo-site目录打开git bash:
``` bash
初始化本地git仓库
$ git init

将README.md上传master
$ git add README.md
$ git commit -m "注释"

创建分支并切换分支
$ git branch hexo
$ git checkout hexo 

新建.gitignore文件，忽略hexo发布的静态文件，内容如下
db.json
public/

提交hexo分支到github保存
$ git add .
$ git commit -m "注释"
$ git remote add origin 远程git地址
$ git push origin hexo:hexo
```

## 部署博客
```
构建预览博客
$ cd your-hexo-site
$ hexo clean && hexo g && hexo s

发布博客
$ npm install hexo-deployer-git --save
$ hexo deploy

浏览myname.github.io
```

## 其他问题
tags: #文章标签，可空，多标签请用格式[tag1,tag2,tag3]

