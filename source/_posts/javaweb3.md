---
title: java web（三）spring
date: 2016-07-31 21:43:34
tags: spring
categories: java
---
# spring核心模块
* spring core
* spring context
* spring aop
* spring dao
* spring orm
* spring web
* spring web mvc

# ClassLoader
1. 装载
2. 链接
3. 初始化

AppClassLoader,继承自ExtClassLoader，继承自根ClassLoader。

ClassLoader，采用全盘负责委托父装载器装载。

# Resource
* ByteArrayResource
* ClassPathResource
* FileSystemResource
* InputStreamResource
* ServletContextResource
* UrlResource

## Ant风格匹配符
* ? 匹配文件名中一个字符
* * 匹配文件吗中任意字符
* ** 匹配多层路径

# BeanFactory初始化顺序
1. 创建配置文件
2. 装载配置文件
3. 启动IOC容器
4. 获取Bean实例

# ApplicationContext实现类
* ClassPathXmlApplicationContext
* FileSystemXmlApplicationContext
* ConfigurableApplicationContext

# spring配置文件
* beans
* bean
* constructor-arg
* property
* lookup-method
* replace-method


## beans
属性

* default-laze-init,延迟加载，默认false
* default-dependency-check,默认none
* default-autowire，默认no

## bean property
* **Map**

&lt;property&gt;

&lt;map&gt;

&lt;entry&gt;

&lt;key&gt;&lt;/key&gt;

&lt;value&gt;&lt;/value&gt;

&lt;/entry&gt;

&lt;/map&gt;

&lt;/property&gt;


* **Properties**

&lt;property&gt;

&lt;props&gt;

&lt;prop key="p01"&gt;v01&lt;/prop&gt;

&lt;/props&gt;

&lt;/property&gt;

## 工厂方法
* 非静态

&lt;bean id factory-bean factory-method&gt;

* 静态

&lt;bean id factory-method&gt;

## bean依赖关系
* 继承，abstract parent
* 依赖，depends-on
* 引用

