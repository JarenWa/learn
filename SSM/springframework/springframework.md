---
layout: post
title: "springframework"
date: 2023-11-15
permalink: /tech/SSM/springframework/
---
<p style="font-size:30px;">SpringFramework</p>

<p style="font-size:20px;">目录</p>
<!-- TOC -->

- [1 SpringFramework](#1-springframework)
    - [SpringFramework 主要功能模块](#springframework-主要功能模块)
    - [SpringFramework 主要优势](#springframework-主要优势)
- [2 Spring IoC](#2-spring-ioc)
    - [组件和组件管理](#组件和组件管理)
    - [Spring IoC 容器接口和实现类](#spring-ioc-容器接口和实现类)
    - [Spring IoC 容器的配置方式](#spring-ioc-容器的配置方式)
    - [使用基于Java注解的配置方式创建和使用Spring容器](#使用基于java注解的配置方式创建和使用spring容器)
        - [Bean注解标记和扫描](#bean注解标记和扫描)
        - [Bean作用域注解](#bean作用域注解)
        - [Bean周期方法注解](#bean周期方法注解)
        - [Bean属性赋值：引用类型自动装配（DI）](#bean属性赋值引用类型自动装配di)
        - [Bean属性赋值：基本类型属性赋值（DI）](#bean属性赋值基本类型属性赋值di)
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
- **IoC容器**

  Spring IoC 容器，负责实例化、配置和组装 bean（组件）核心容器。容器通过读取配置元数据来获取有关要实例化、配置和组装组件的指令。

  降低bean之间的耦合

- **IoC（Inversion of Control）控制反转**

    面向对象编程设计思想

  IoC 主要是针对对象的创建和调用控制而言的，也就是说，当应用程序需要使用一个对象时，不再是应用程序直接创建该对象，而是由 IoC 容器来创建和管理，即控制权由应用程序转移到 IoC 容器中，也就是“反转”了控制权。这种方式基本上是通过依赖查找的方式来实现的，即 IoC 容器维护着构成应用程序的对象，并负责创建这些对象。

- **DI (Dependency Injection) 依赖注入**

  DI 是指在组件之间传递依赖关系的过程中，将依赖关系在容器内部进行处理，这样就不必在应用程序代码中硬编码对象之间的依赖关系，实现了对象之间的解耦合。在 Spring 中，DI 是通过 XML 配置文件或注解的方式实现的。它提供了三种形式的依赖注入：构造函数注入、Setter 方法注入和接口注入。

IoC通过依赖注入实现，IoC容器是实现依赖注入的关键。


- 理解控制反转（IoC）

创建类、配置文件。由IoC容器读取配置文件，在IoC容器中通过反射机制完成实例化。对象的创建权限给了Spring核心容器。


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

## Spring IoC 容器接口和实现类

ApplicationContext

## Spring IoC 容器的配置方式
XML配置、注解、Java配置类

在SpringBoot框架下，推崇“0配置文件” 不用xml配置

用配置类+注解


## 使用基于Java注解的配置方式创建和使用Spring容器
组件交给Spring IoC 容器管理，并获取和使用的步骤：
配置元数据--实例化IoC容器--获取组件(Bean)

1、类上添加IoC注解

2、（提高性能）告诉SpringIoC容器，在哪些包下添加了IoC注解（用xml文件 指定注解生效包的信息）

### Bean注解标记和扫描
1 准备组件类：普通组件、Controller组件、Service组件、Dao组件

Spring 提供了以下多个注解，这些注解可以直接标注在 Java 类上，将它们定义成 Spring Bean。

|注解|说明|
|-|-|
|@Component|该注解用于描述 Spring 中的 Bean，它是一个泛化的概念，仅仅表示容器中的一个组件（Bean），并且可以作用在应用的任何层次，例如 Service 层、Dao 层等。 使用时只需将该注解标注在相应类上即可。|
|@Repository|该注解用于将数据访问层（Dao 层）的类标识为 Spring 中的 Bean，其功能与 @Component 相同。|
|@Service|该注解通常作用在业务层（Service 层），用于将业务层的类标识为 Spring 中的 Bean，其功能与 @Component 相同。|
|@Controller|该注解通常作用在控制层（如SpringMVC 的 Controller），用于将控制层的类标识为 Spring 中的 Bean，其功能与 @Component 相同。|

> 理解：不同注解对于Spring使用IOC容器管理这些组件来说没有区别，也就是语法层面没有区别。所以@Controller、@Service、@Repository这三个注解只是给开发人员看的，让我们能够便于分辨组件的作用。

> !!!@Repository 能够启动与Spring数据访问相关联的其他功能 

2 xml配置文件确定扫描范围

在resources下添加.xml配置文件

```
<!--1. 普通配置包扫描
           base-package 指定ioc容器去哪些包下查找注解类 -> ioc容器
           一个包或者多个包  com.atguigu,com.atguigu.xxx 包,包
           指定包,相当于指定了子包内的所有类
    -->
    <context:component-scan base-package="com.atguigu.ioc_01" />
```

### Bean作用域注解



### Bean周期方法注解


周期方法：定义当 IoC 容器在实例化（之后）、销毁（之前） 组件对象时的操作

### Bean属性赋值：引用类型自动装配（DI）

### Bean属性赋值：基本类型属性赋值（DI）


# 3 Spring AOP

# 4 Spring 声明式事务

# 5 总结




工具类：dbutils 是数据库简化技术  

框架-（有jar包，配置文件-（可定制化））：log4j ：日志输出技术  .info()  .error(

)