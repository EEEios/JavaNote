# JSON

1. 配置viewResolver
2. 配置defaultViews

![](http://doze9097.top//1571372021743.png)

3. @ResponseBody

   ![](http://doze9097.top//1571374194158.png)



## 总结

1. 通过`ContentNegotiatingViewResolver`类处理格式转换
2. 通过返回`ResponseEntity`，即返回js格式
3. 使用`@ResponseBody/@ResquestBody`获取json请求