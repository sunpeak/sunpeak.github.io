---
title: maven构建
date: 2016-07-18 19:11:57
tags: maven
categories: java
---
# 安装maven
## 前提
安装jdk，且设置好了环境变量JAVA_HOME

## 环境变量
M2_HOME=maven path

PATH中添加 %M2_HOME%\bin

## 测试
mvn -version

# 模板项目
mvn archetype:generate

# 打包项目
mvn package

生成到target目录下

# 命令说明
* mvn 生命周期
* mvn 插件:目标

一个生命周期上可以绑定多个插件目标

mvn package

mvn archetype:generate

插件是目标的集合，而maven是插件的框架

# 常见插件
* maven-archetype-plugin
* maven-dependency-plugin
* maven-help-plugin
* maven-resources-plugin 资源文件
* maven-surefire-plugin
* jetty-maven-plugin 
* maven-enforcer-plugin 规则

插件列表 http://maven.apache.org/plugins/index.html

# 依赖管理
scope取值：

* compile 编译范围，默认
* provided 已提供范围
* runtime 运行时范围
* test 测试范围
* system 系统范围

# 仓库
* 本地仓库，优先使用
* 远程仓库

修改本地仓库，maven conf目录下setting.xml中 localRepository节点

修改远程仓库，pom中repositories节点的repository子节点

# jetty运行web项目
mvn jetty:run

# 使用pluginManagement管理插件
build->pluginManagement->plugins
