# mmall 实战 Day02

@JsonIgnore（方法上）：使之不在json序列化结果中。

@JsonSerialize（include = JsonSerialize.Inclusion.NON_NULL）

> NON_NULL，如果是null对象，key也会消失



## 泛型冲突

当泛型和具体类型冲突时，系统会选择具体类型优先。

```Java
private ServerResponse(int status, S tring msg){
        this.status = status;
        this.msg = msg;
}
//传入类型为String时，发生冲突，但是系统会调用上方类型更具体的方法    
private ServerResponse(int status, T data){
        this.status = status;
        this.data = data;
}
```

```java
public static <T> ServerResponse<T> createBySuccess(T data){
	return new ServerResponse<T>(ResponseCode.SUCCESS.getCode(), data);
}
//将String传入T后，还是T类型，所以会调用上面T的构造器
public static <T> ServerResponse<T> createBySuccess(String msg, T data){
	return new ServerResponse<T>(ResponseCode.SUCCESS.getCode(), msg, data);
}
```



## 生成Token（Guava）

token：具有有效期，使用Guava Cache实现有效期

> 回答问题正确之后跳转到修改密码界面
>
> 如果不使用Token作为标识，可能会出现抓包横向越权等漏洞

UUID.randomUUID().toString();

