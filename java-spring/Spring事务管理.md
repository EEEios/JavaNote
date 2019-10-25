# Spring事务管理

## 接口

TransactionDefinition - [事务定义信息](##事务定义信息)

platformTransactionManager - [事务管理器](##事务管理器)

TransactionStatus - [事务具体运行状态](##事务具体运行状态)



## 事务管理器

TransactionDefinition：定义了一组常量信息

![](http://doze9097.top//1571321466563.png)

![1571321652503](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1571321652503.png)

## 事务定义信息

根据不同的持久层框架选择不同的事务管理器的具体实现类。 

## 事务具体运行状态

获取事务响应的状态

## 开发式事务管理

### 基于TransactionProxyFactoryBean的事务管理

1. 引入依赖

   ![](http://doze9097.top//1571323119384.png)

2. 在事务中注入代理类

   ![](http://doze9097.top//1571323217629.png)

   ![1571323358678](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1571323358678.png)



### 基于aop的事务管理

![](http://doze9097.top//1571323524129.png)

其中：

![](http://doze9097.top//1571323599238.png)



### 基于注解的事务管理

配置注解事务管理

![](http://doze9097.top//1571323677045.png)

给要代理的类或方法发添加注解

![](http://doze9097.top//1571323720181.png)

其中：

![](http://doze9097.top//1571323769670.png)

## 编程式事务管理

1. 引入依赖：

![](http://doze9097.top//1571322563295.png)

2. 注入模板

   ![](http://doze9097.top//1571322649654.png)

3. 配置好事务管理

   ![](http://doze9097.top//1571322684896.png)

   

   > .execute()方法中传入的是TransactionCallbackWithoutResult()对象，图片中使用了匿名内部类。

