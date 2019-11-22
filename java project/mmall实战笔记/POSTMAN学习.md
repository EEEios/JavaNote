# POSTMAN学习

![](http://doze9097.top//20191122161649.png)

![](http://doze9097.top//20191122161734.png)

![](http://doze9097.top//20191122162139.png)

## POST不同的区别

### form-data

http请求中的multipart/form-data，会将表单数据处理为一条消息，以标签为单元，用分隔符分开。

既可以上传键值对，也可以上传文件（用boundary隔离）。

上传的是文件时：

	- 会有Content-Type来表明文件类型；
	- 有content-disposition说明字段信息



### x-www-form-urlencoded

http请求中的application/x-www-from-urlencoded，会将表单中的数据转换为键值对，比如`name=java&age=23`



### raw

可以上传**任意格式的文本**，例如text、json、xml、html等



### binary

相当于Content-Type:application/octet-stream。只能上传二进制数据，通常用来上传文件，由于没有键值，只能上传一个文件。





