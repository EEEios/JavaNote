# Day02

## IDEA配置

![](http://doze9097.top//20191120190532.png)

![](http://doze9097.top//20191120190714.png)

## mybatis-generator配置

1. copy配置文件

![](http://doze9097.top//20191120122541.png)

2. 创建数据库的资源文件

   ![](http://doze9097.top//20191120122951.png)

3. 配置generator

   ![](http://doze9097.top//20191120123139.png)

![](http://doze9097.top//20191120123218.png)

![](http://doze9097.top//20191120123925.png)

4. 配置数据表

   ![](http://doze9097.top//20191120124203.png)

5. 生成pojo、dao、mapper

   ![](http://doze9097.top//20191120124423.png)

   ![](http://doze9097.top//20191120125802.png)

6. 修改 create_time和update_time

![](http://doze9097.top//20191120132921.png)

![](http://doze9097.top//20191120132942.png)

![](http://doze9097.top//20191120132955.png)

![](http://doze9097.top//20191120133005.png)



## mybatis-plugins安装（略）



## mybatis-pagehelper分页插件

官方文档：https://github.com/pagehelper/Mybatis-PageHelper

1. 在pom中引入插件



## 配置spring

#### spring模板：

http://projects.spring.io/spring-framework

http://github.com/spring-projects/spring-mvc-showcase

http://github.com/spring-projects/spring-petclinic

http://github.com/spring-projects/greenhouse

http://github.com/spring-projects/spring-boot



## Web.xml

1. characterEncodingFilter：字符过滤器

2. org.springframework.web.context.request.RequestContextListener：负责容器开启/关闭的监听器

3. org.springframework.web.context.ContextLoaderListener：web容器和spring容器进行整合的监听器

4. contextConfigLocation：指向spring配置文件

   > RequestContextListener通过加载contextConfigLocation中的配置文件使得spring和web进行整合

5. <servlet\>dispatcher：spring mvc配置

   > <load-on-startup\> > 0 时在初始化时加载这个servlet

6. <servlet-mapping\>：url拦截



## applicationContext.xml（spring配置）

1. 包自动扫描注解配置：<context:component-scan base-package="com.mmall" annotation-config="true"/>

2. aop配置：<aop:aspectj-autoproxy/ \>

3. 分离的spring配置文件的定位：<import resource="applicationContext-datasource.xml"/ \>

   > 包括：
   >
   > - 数据库配置
   > - 分页插件配置
   > - sqlSessionFactory
   > - mapper扫描
   > - 事务管理



## dispatcher-servlet.xml（spring mvc配置）

1. 包扫描
2. 编码配置（utf-8）
3. spring mvc自动反序列化配置类
4. 文件上传配置



## logback.xml

copy logback.xml 到 resources

1. 项目日志