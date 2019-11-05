# ()源计划 Day01

## UserController

### RestTemplate

参考链接：https://www.jianshu.com/p/90ec27b3b518

传统方式下java访问restful服务，一般使用Apache的HttpClient。不过使用复杂，在spring中提供了RestTemplate这种便捷的模板类来操作。

默认情况下，RestTemplate自动注册了一组HttpMessageConvert来处理不同contenType的请求。



### File

使用new file(路径)，创建抽象的文件流

```
substring()：截取该位置到末尾的字符串
```



### MultipartFile

方法：

transferTo(filePath)：将文件流保存到filePath的位置



### Properties

Properties（Java.util.Properties），该类主要用于读取Java的配置文件，不同的编程语言有自己所支持的配置文件，配置文件中很多变量是经常改变的，为了方便用户的配置，能让用户够脱离程序本身去修改相关的变量设置。就像在Java中，其配置文件常为.properties文件，是以键值对的形式进行参数配置的。



## Gson

参考连接：https://www.jianshu.com/p/e740196225a4

使用方法

`fromJson()`：用于解析Json，反序列化

`toJson()`：用于生成Json，序列化



# 增加模块

- 获取给定日期周次的周一

参考链接：https://blog.csdn.net/wylfll/article/details/73088882





# 规划

4个时段

星期几+时间段



# 数据库设置

mysql5.7中，mysql.user中的password列不存在，改为authentication_string。

修改密码应如下

```
update user set authentication_string=password("1234") where user="root";
```

## 重置密码

参考连接：[https://www.stackcc.com/2019/09/22/windows%E4%B8%8Bmysql5-7%E9%87%8D%E7%BD%AE%E5%AF%86%E7%A0%81%E5%BF%98%E8%AE%B0%E5%AF%86%E7%A0%81%E9%87%8D%E7%BD%AEroot%E5%AF%86%E7%A0%81/](https://www.stackcc.com/2019/09/22/windows下mysql5-7重置密码忘记密码重置root密码/)