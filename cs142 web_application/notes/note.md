# 学习笔记

**DOM**

文档对象模型（DOM, Document Object Model）是一种编程技术接口，它能帮助我们修改HTML文档中的元素。

> DOM stands for Document Object Model. It is a programming interface that allows us to create, change, or remove elements from the document.

DOM将HTML文档视为一棵树，而树中的节点则是HTML元素。

![](https://www.freecodecamp.org/news/content/images/size/w1000/2021/09/Document.jpg)

**MVC**

![](https://qph.fs.quoracdn.net/main-qimg-516787d69e66c408be4b543baf7cd4f1-pjlq)

+ [quora - is MVC a frontend or backend technique?](https://www.quora.com/Which-part-of-Mode-View-Controller-MVC-pattern-is-about-the-front-end-and-which-part-is-about-the-back-end-programming)

**MVC vs dao&service**

> You should not compare these directly with each other. Services and  DAOs form layers in any n-layered application. MVC application can  include Services and DAOs.
> 
> **Service layer** is a generic term that basically acts  as an entry point to the application domain and typically includes  business logic. For a web application, you could treat the business  logic layer as a service layer, or for mobile clients, you could expose a web API and treat is a service layer. In short irrespective of GUI/  Client, you should be able to re-use business logic as-is. 
> 
> **DAO**s are just the objects that abstract away the data storage mechanism.
> 
> **MVC** is a design pattern where V and C are "strictly" form the presentation layer, and M can include everything that is  beyond presentation (GUI). The model part in MVC has been an opinion  based topic for a long time. But here's how I would structure a typical  MVC application.

+ [stackoverflow - Service and Dao vs MVC](https://stackoverflow.com/questions/45490749/service-and-dao-vs-mvc)
