# 服务端框架 Server-Side Framework

## 概述

服务器端框架(亦称 "web 应用框架") 使编写、维护和扩展web应用更加容易。

它们提供工具和库来实现简单、常见的开发任务, 包括 路由处理, 数据库交互, 会话支持和用户验证, 格式化输出 (e.g. HTML, JSON, XML), 提高安全性应对网络攻击.

## 功能

### 直接处理HTTP请求和响应

web框架允许你编写简单语法的代码，即可生成处理这些请求和回应的代码。这意味着你的工作变得简单、交互变得简单、并且使用抽象程度高的代码而不是底层代码。

### 将请求路由到相关的handler中

大多数的站点会提供一系列不同资源，通过特定的URL来访问。如果都放在一个函数里面，网站会变得很难维护。所以web框架提供一个简单机制来匹配URL和特定处理函数。这种方式对网站维护也有好处，因为你只需要改变用来传输特定功能的URL而不用改变任何底层代码。

### 使从请求中获得数据变得简单

数据在HTTP请求中的编码方式有很多种。一个从服务器获得文件或者数据的HTTP `GET`请求可能会按照URL参数中要求的或者URL结构中的方式进行编码。一个更新服务器上数据的HTTP `POST`请求则会在请求主体中包含像“POST data”这样的更新信息。HTTP请求也可能包含客户端cookie中的即时会话和用户信息。

web框架提供一个获得这些信息的适合编程语言的机制。比如，Django传递给视图函数的`HttpRequest`对象包含着获得目标URL的方式和属性、请求的类型（比如一个HTTP `GET`）、`GET`或者`POST`参数、cookie或者session数据等等。Django也可以通过在URL匹配表中定义“抓取模式”来在URL结构中传递编码了的信息（如上面的编码片段中的最后一行）。

### 抽象和简化数据库接口

网站使用数据库来存储与用户分享的信息和用户个人信息。web框架通常会提供一个数据库层来抽象数据库的读、写、查询和删除操作。这一个抽象层被称作对象关系映射器（ORM）。

使用对象关系映射器有两个好处：

- 你不需要改变使用数据库的代码就可以替换底层数据库。这就允许开发者依据用途优化不同数据库的特点。
- 简单的数据的验证可以被植入到框架中。这会使得检查数据是否按照正确的方式存储在数据库字段中或者是否是特定的格式变得简单（比如邮箱地址），并且不是恶意的（黑客可以利用特定的编码模式来进行一些如删除数据库记录的非法操作）。

## 常见

### Django(Python)

[Django](https://www.djangoproject.com/)是一个高水平的python web框架，它鼓励快速的开发和简洁、务实的设计。

Django遵循“Batteries included”哲学，并且提供了几乎所有大多开发者们想要“开箱即用”的东西。因为它已经包含了所有东西，它作为一个整体一起工作，遵循着一致的设计原则，并且有扩展的、持续更新的文档。它也是非常快、安全和易于扩展的。基于python，Django代码非常容易阅读和维护。

### Flask(Python)

[Flask](http://flask.pocoo.org/)是python的一个微型框架。

Flask已经非常火爆了，部分因为那些需要在小型的、资源受限的系统中提供web服务的开发者们。(比如，在[Raspberry Pi](https://www.raspberrypi.org/), [Drone controllers](http://blogtarkin.com/drone-definitions-learning-the-drone-lingo/)等上面运行服务器)。

### Express(Javascript)

[Express](http://expressjs.com/) 针对 [Node.js](https://nodejs.org/en/) 的快速的、unopinioned、灵活的、小型的web框架(node是用来运行Javascript的无浏览器的环境)。它为web和移动应用提供强大的系列功能，并且传输有用的HTTP工具、方法和[middleware](https://developer.mozilla.org/en-US/docs/Glossary/Middleware).

因为Express是一个小型的web框架，它几乎不包含任何你可能想要使用的组件（比如，数据库接口和对用户和会话的支持通过独立的库来完成）。有很多独立的、非常好的组件，但是有时候你可能很难决定对于特定目的而言哪一个是最好的！ 

### ASP.NET(C#)

[ASP.NET](http://www.asp.net/) 是一个由微软开发的开源Web框架，用于构建现代的Web应用程序和服务。通过ASP.NET你能快速创建基于HTML、CSS、JavaScript的网站，并且能满足大量用户的需求，还可以很容易地添加诸如Web API、数据表单、即时通讯的功能。

ASP.NET的特点之一就是它建立在 [Common Language Runtime](https://en.wikipedia.org/wiki/Common_Language_Runtime) (CLR公共语言运行时)之上。这使得程序员可以使用任何支持的.NET语言（如C#、Visual Basic)来编写ASP.NET代码。和很多微软的产品一样，它得益于出色的开发工具（通常是免费的）、活跃的开发者社区，以及详尽的文档。 

## 参考 References

+ [MDN - 服务端编程介绍](https://developer.mozilla.org/zh-CN/docs/Learn/Server-side/First_steps/Introduction)
+ [MDN - 客户端服务端交互概述](https://developer.mozilla.org/zh-CN/docs/learn/Server-side/First_steps/Client-Server_overview)
+ [MDN - 服务端web框架](https://developer.mozilla.org/zh-CN/docs/Learn/Server-side/First_steps/Web_frameworks)