# Spring Day01 序章

装配：创建应用组件之间的协作

加载上下文：

 - ClassPathXmlApplication("file")；
   - getbean("...");
   - close()

```
@Configuration
@Bean
```



#### 面向切面编程（AOP）

横切关注点：日志、事务管理、安全等跨越系统多个组件的功能；

```xml
<aop:config>
	<aop:aspect ref="...">
        <aop:pointcut id="..."/>
        <aop:before pointcut-ref="{id}" method="..."/>
        <aop:after pointcut-ref="{id}" method="..."/>
    </aop:aspect>
</aop:config>
```



#### spring容器

spring自带多个容器实现

分类：

	- bean工厂，提供DI支持
	- 应用上下文，并提供应用框架级别的服务

##### 应用上下文

可以实现从java的配置类、类路径下xml、文件系统中的xml、web应用下的xml加载上下文定义



#### bean的生命周期