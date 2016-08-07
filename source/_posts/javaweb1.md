---
title: java web（一）请求过程 
date: 2016-07-20 12:50:12
tags: web
categories: java
---
# curl
## 查看返回的http头信息
curl -I url
## 增加http头信息
curl url -H "Cookie:cna=sd0***"

# http解析
## 请求头
Accept-Charset: 用于指定客户端接受的字符集
Accept-Encoding: 用于指定可接受的内容编码，如gzip，deflate
Accept-Language: 用于指定一种自然语言，如zh-cn
Host
User-Agent
Connection： 当前连接是否保持，如Keep-Alive

## 响应头
Server： 服务器名称
Content-Type: 用来指明发送给接收者的实体正文的媒体类型，如text/html;charset=GBK
Content-Encoding: 与请求报头的Accept-Encoding对应
Content-Language：与请求报头的Accept-Language对应
Content-Length
Keep-Alive：保持连接的时间，如timeout=5，max=120

## 状态码
200
302
400：客户的请求有语法错误，不能被服务器识别
403：服务器收到请求，但是拒绝提供服务
404：请求的资源不存在
500：服务器发生不可预期的错误

## 强制刷新
Ctrl+F5,会在http请求头增加2项，Pragma：no-cache和Cache-Control：no-cache
## Cache-Control/Pragma

* Public,所有内容都缓存
* Private，只缓存到私有缓存
* no-cache，不缓存
* no-store，不缓存到缓存或Internet临时文件
* must-revalidation/proxy-revalidation，如果缓存失效，请求必须发送到服务器/代理以进行验证
* max-age=xxx，缓存内容在xxx秒后失效

## Expires
后面跟一个日期和时间，超过这个时间值后，缓存内容失效

## Last-Modified/Etag
服务器上资源的最后一次修改时间，一般服务器会在响应头返回Last-Modified字段，浏览器再次请求时在请求头增加一个If-Modified-Since字段，询问当前缓存页面是否最新，如果是最新的就返回304状态码，告诉浏览器是最新的，服务器不会传输新的数据

Etag是服务器给每个页面分配的唯一的编号

## DNS解析
1. 浏览器缓存解析
2. 操作系统hosts解析
3. 请求本地dns服务器LDNS，有缓存。（cat /etc/resolv.conf）
4. LDNS向Root Server域名服务器请求，返回gTLD server
5. LDNS向gTLD请求，返回Name Server域名服务器
6. LDNS向Name server请求，返回IP记录和TTL值，会缓存这个结果，时间有TTL控制

dig 域名 +trace ，跟踪域名解析
### 刷新本地缓存
* windows平台， ipconfig /flushdns 
* linux平台， /etc/init.d/nscd restart

### jvm缓存dns
通过InetAddress类完成，在%JAVA_HOME%\lib\security\java.security文件中配置

* networkaddress.cache.ttl 正确结果缓存
* networkaddress.cache.negative.ttl 失败结果缓存

注：-1代表永不失效，10代表缓存10秒

修改缓存方式

* 直接修改java.security文件
* java启动参数增加-Dsun.net.inetaddr.ttl=xxx
* 通过InetAddress类动态修改

### 域名解析记录
* A，指定域名对应的ip地址，可以多域名解析到一个ip，但是不能一个域名解析到多个ip
* MX，域名下的邮件服务器指向的mail server
* CNAME，别名解析
* NS，指定域名解析器
* TXT，说明