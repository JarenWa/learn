---
layout: post
title: "springframework"
date: 2023-11-15
permalink: /tech/SSM/springframework/
---
<p style="font-size:30px;">SpringFramework</p>
<a href="https://zhuanlan.zhihu.com/p/557762402" target="_blank">真香！这篇文章终于让我弄懂了啥是Spring framework - 知乎</a>
<p style="font-size:20px;">目录</p>
<!-- TOC -->

- [1 SpringFramework](#1-springframework)
    - [SpringFramework 主要功能模块](#springframework-主要功能模块)
    - [SpringFramework 主要优势](#springframework-主要优势)
- [2 Spring IoC](#2-spring-ioc)
    - [组件和组件管理](#组件和组件管理)
    - [Spring IoC 容器](#spring-ioc-容器)
        - [Spring IoC 容器接口](#spring-ioc-容器接口)
        - [ApplicationContext 容器实现类](#applicationcontext-容器实现类)
    - [Spring 框架的配置方式](#spring-框架的配置方式)
        - [XML配置](#xml配置)
        - [注解](#注解)
        - [Java配置类](#java配置类)
- [3 Spring AOP](#3-spring-aop)
- [4 Spring 声明式事务](#4-spring-声明式事务)
- [5 总结](#5-总结)

<!-- /TOC -->
# 1 SpringFramework
## SpringFramework 主要功能模块

|功能模块|功能介绍|
|-|-|
|Core Container|核心容器，在 Spring 环境下使用任何功能都必须基于 IOC 容器。|
|AOP&Aspects|面向切面编程|
|TX|声明式事务管理。|
|Spring MVC|提供了面向Web应用程序的集成功能。|
||


## SpringFramework 主要优势



# 2 Spring IoC
Inversion of Control 控制反转，面向对象编程设计思想。

降低bean之间的耦合

IoC通过依赖注入实现，IoC容器是实现依赖注入的关键。

## 组件和组件管理
组件：可以复用的java对象
- 组件一定是对象
- 对象不一定是组件

Spring 充当组件管理

组件可以完全交给Spring 框架进行管理，Spring框架替代了程序员原有的new对象和对象属性赋值动作等！
- 组件对象实例化
- 组件属性属性赋值
- 组件对象之间引用
- 组件对象存活周期管理
- ......

我们只需要编写元数据（配置文件）告知Spring 管理哪些类组件和他们的关系即可！
- xml、java注解、java代码（类）

## Spring IoC 容器
### Spring IoC 容器接口

### ApplicationContext 容器实现类

## Spring 框架的配置方式
### XML配置
### 注解
### Java配置类



# 3 Spring AOP

# 4 Spring 声明式事务

# 5 总结




工具类：dbutils 是数据库简化技术  

框架-（有jar包，配置文件-（可定制化））：log4j ：日志输出技术  .info()  .error(

)