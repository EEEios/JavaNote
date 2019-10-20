# Tomcat

参考连接：https://segmentfault.com/a/1190000013122831

文件目录：

![img](https://segmentfault.com/img/remote/1460000013228168?w=728&h=388)

1. bin：启动和关闭tomcat的bat文件
2. conf：配置文件
   - `server.xml`该文件用于配置server相关的信息，比如tomcat启动的端口号，配置主机(Host)
   - `web.xml`文件配置与web应用（web应用相当于一个web站点）
   - `tomcat-user.xml`配置用户名密码和相关权限.
3. lib：该目录放置运行tomcat运行需要的jar包
4. logs：存放日志，当我们需要查看日志的时候，可以查询信息
5. webapps：放置我们的web应用
6. work工作目录：该目录用于存放**jsp被访问后生成对应的server文件和.class文件**

## 虚拟目录

1. 在/conf/server.xml文件中<Host>节点添加 

   ```xml
   <Context path="访问时输入的项目名称" docBase="项目的绝对路径"/>
   ```

   

2. conf/Catalina/localhost创建xml文件，文件名就是访问时输入的项目名称，其中文件的代码如下

   ```xml
   <?xml version="1.0" encoding="UTF-8"?> 
   <Context 
       docBase="项目的绝对路径" 
       reloadable="true"> 
   </Context> 
   ```

## 虚拟主机

使用一个tomcat对多个域名进行负责

- 在server.xml文件中添加主机

  ```xml
  <Host name="zhongfucheng" appBase="D:\web1">
      <Context path="/web1" docBase="D:\web1"/>
  </Host>
  ```

  