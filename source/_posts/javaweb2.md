---
title: java web（二）I/O机制
date: 2016-07-20 19:49:39
tags: IO
categories: java
---
# 访问文件方式
* 标准访问，read->用户地址空间->内核地址空间->磁盘
* 直接I/O，read->用户地址空间->磁盘
* 同步访问，只有当数据成功写入磁盘，才返回应用程序成功的标志
* 异步访问，当访问的线程发出请求后，线程会接着处理其他事情，不阻塞等待
* 内存映射，操作系统将内存中的某一块区域与磁盘中的文件关联起来

# NIO
selector注册到通信信道上，调用select()方法检测信道io是否ok，如果ok，则将数据分配到对应的buffer中。

# 适配器模式
* 类适配器，通过继承关系来适配，Adapter extends Adaptee implements Target
* 对象适配器，通过关联对象来适配，Adapter implements/extends Target，new Adapter（Adaptee...）

比如，InputStreamReader extends Reader,new InputStreamReader(InputStream in)

# 装饰器模式
FilterInputStream extends InputStream,保留了对InputStream的引用
BufferedInputStream extends FilterInputStream

# 适配器和装饰器对比
* 适配器改变接口
* 装饰器不改变接口，是为了增强功能