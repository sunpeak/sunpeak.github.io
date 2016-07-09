---
title: 使用Hexo搭建git博客
date: 2016-07-09 13:39:05
tags: 
	- "github pages"
	- "hexo"
	- "hexo-theme-next"
	- "markdown"
categories: "git"
---
## 技术说明
* github pages，由github提供的免费空间
* Hexo，基于Node.js开发的快速、简单和强大的博客框架，支持markdown格式。官网 http://hexo.io
* hexo-theme-next，hexo配套的主题，目前在github上star最多。官网 http://theme-next.iissnan.com/

## 安装准备
* node.js  https://nodejs.org/en/
* git

## 创建本地git仓库
本地创建git仓库，并且创建hexo分支。hexo分支用于保存hexo的工作空间，更新博客后都需要提交git来保存markdown格式的原文，这样可以在多台机器上共享hexo来发布博客。而master分支用于保存静态的博客页面，也就是最终呈现的博客html。
在本地目录打开git bash
``` bash
$ git init
$ git branch hexo
$ git checkout hexo 
$ git remote add origin 远程git地址
```
