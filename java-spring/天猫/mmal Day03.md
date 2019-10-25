# mmal Day03

## 目录结构

### 包目录

util：工具类

pojo：简单数据库的对象

vo（view object，value object）：负责封装pojo

common：常量，异常的公共类

## 包关系

common：存放响应对象，封装有要相应的属性。

>- status
>- msg
>- data

controller

service：声明方法接口

service.Impl：实现service，实现所有service的方法

## 实战

common：包含响应对象，响应code的枚举类。

common.ServiceResponse：创建响应的Json，使用common.ResponseCode中的状态码

service.IUserService：返回ServerResponse<User>泛型对象

service.UserServiceImpl：声明为@Service,实现IUserService接口，实现方法。调用dao层实现数据库操作，并使用common.ServiceResponse创建响应类。并在controller进行调用



dao层类实现：在接口中传入多个参数需要用到`@Param("...")`注解，在mapper.xml使用时可以使用注解中的值指定

> parameterType：调用java的类型
>
> parameterMap：在mysql中声明的对象

#### Usercontroller

用户登录方法：

```java
@RequestMapping(value = "login.do", method = RequestMethod.POST)
    public ServerResponse login(String code, HttpSession session) {
        
        ServerResponse serverResponse = iUserService.login(code);
        //如果登录成功，把用户添加进入会话
        if (serverResponse.isSuccess()) {
            session.setAttribute(Const.LOGINING_USER,serverResponse.getData());
        }
        return serverResponse;
    }
```

