---
title: 了解cookie-session-token
top: false
cover: false
toc: true
mathjax: true
date: 2024-07-01 13:22:00
password: 
summary: 
tags:
  - web
categories:
---


### 基础cookie

cookie：浏览器给首次服务器发送http请求时进行用户登录验证，用户名密码验证成功，服务器在响应时会set-cookie也就是cookie设置（包含name-value属性，理解为用户名和密码），浏览器收到响应后将cookie保存起来（通过DevTools开发者工具-application-cookie可查看，**保存在浏览器中**），后面浏览器发送的每一个HTTP请求都会附上cookie（作为请求头的一部分）。

问题：如果把用户名密码存在cookie中，当电脑被黑，会泄露信息很不安全。

解决方案：在cookie中不存放用户名密码，而是session id

### 基于cookie的session

session：将浏览器访问服务器行为看作会话，用户登录验证通过后，服务器生成新的session对象，包含{SessionId: xxPSnj01(无规律字符串，唯一), Max-Age:会话结束时间对应cookie有效期…}（**保存在服务器自身数据库中**），在响应请求进行set-cookie时将上述信息放到cookie中（此时不包含用户名和密码），浏览器拿到cookie后保存（黑客入侵拿到SessionId无法推断用户名密码），在下次请求时放到请求头cookie中（DevTools-Network，对应请求的Headers中包含cookies），如果黑客修改了SessionID，浏览器可以通过签名知道。cookie失效后，浏览器会自动删除该cookie。用户logout时，会话结束，服务器保存的session会清除。

问题：大量用户同时访问服务器时，产生大量sessionId，

- 性能问题

因为，验证请求是根据sessionid 到数据库中查找session表的，而数据库操作是服务端常见的性能瓶颈，尤其是当用户量比较大的时候。

- 扩展性问题

当系统用户特别多的时候，后端处理请求的服务端通常由多个，部署在多个节点上。 但是多个节点都要访问session表，这样就要求数据库服务能够被多个节点访问，不方便切分数据库以提高性能。

解决方案：JWT（Json Web Token）

### Token

![](image-20240701133048798.png)


用户登录验证成功后，服务器产生一个JWT返回给浏览器，服务器自身不保存JWT，只保存一个JWT签名的密文，浏览器以cookie或storage的方式存储JWT（**JWT保存在浏览器，服务器保保存一个密钥**secret key）。再次发送请求时附上JWT。

JWT由 header.payload.signature组成：（token中三个字符串由.分割）

- header：生成签名的算法，一般是哈希算法
- payload：数据，比如有效期
- signature：签名信息，header和payload分别通过base64编码（编码和加密的区别，编码可以解码），服务器保存的密钥secret key和两段编码进行算法运算得到签名信息。

三部分相关联，修改其中一部分，服务器计算得到的签名就不一致，一定程度上保证安全。Token相当于访问服务器的令牌。

综上，cookie是一种数据载体。