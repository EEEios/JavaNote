# Spring Day02 Spring MVC

### 跟踪spring mvc的请求

1. 请求进入 DispatcherServlet 

2. DispatcherServlet查询处理器映射选择对应的controller

3. controller处理信息，并返回模型和选定的视图（通常为JSP）给DispatcherServlet 

   > 设计良好的控制器本身只处理很少甚至不处理工作，而是将业务逻辑委托给一个或多个服务器对象进行处理。

4. DispatcherServlet 调用视图解析来完成视图的渲染

5. DispatcherServlet 返回数据给客户端



p138

通过AbstractAnnotationConfigDispatcherServletInitializer配置DispatcherServlet是传统web.xml方式的替代方案。



@EnableWebMvc：注解方式开启SpringMVC

Model实际上就是一个Map（也就是key-value对的集合）



p152

```java
@RequestMapping(method=RequestMethod.GET)
public List<Spittle> spittles(){
	return spittleRepository.findSpittles(Long.MAX_VALUE,20);
}
```

上图代码没有引入模型以及视图名

对于模型：会根据返回的对象或集合推测。

对于视图：会根据mapping路径匹配。（需要去掉开头的斜线）