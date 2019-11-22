# Day 03

## 用户模块

### 登录功能

![](http://doze9097.top//20191120191203.png)

<img src="http://doze9097.top//20191120191402.png" style="zoom:75%;" />

ResponseBody：该注解可以将返回自动打包成json格式

### 通用的返回对象

需要继承Serializable接口

![](http://doze9097.top//20191120211739.png)

![](http://doze9097.top//20191120221312.png)

![](http://doze9097.top//20191120221335.png)

### 状态码枚举类

![](http://doze9097.top//20191120212608.png) 

## 用户模块

声明Service

![](http://doze9097.top//20191120223701.png)

声明实现类，注入到controller中

![1574260696650](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1574260696650.png)

![](http://doze9097.top//20191120222150.png)

![](http://doze9097.top//20191120222511.png)

![](http://doze9097.top//20191120223323.png)

controller实现：

![1574260902819](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1574260902819.png)

使用内部接口分组：

![](http://doze9097.top//20191121233257.png)