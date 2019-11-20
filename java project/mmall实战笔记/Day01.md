# Day01

### 1. 数据库设置

搜索并修改默认字符集为utf8。

搜索`default-character-set=`并修改即可

### 2. 修改数据库用户密码

1）`select user,host,password from mysql.user`查看当前用户

2）`set password for root@localhost=password(‘[newpassword]’);`

​	- password()为内置函数

### 3. 删除匿名用户

1）执行`delete from mysql.user where user='';`删除匿名用户

2）执行`flush privileges;`刷新

### 4. 插入新用户

1) `insert into mysql.user(Host,User,Password) values ("localhost","yourUserName",password("yourPassword"));`

2) 执行`flush privileges;`刷新

### 5. 创建database

`CREATE DATABASE 'mmall' DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;`

创建mmall数据库

### 6. 赋予本地用户所有权限

`grant all privileges on mmall.* to yourUserName@localhost identified by 'yourPassword';`

### 7. 开通外网权限

`grant all privileges on mmall.* to 'yourUserName'@'%' identified by 'yourPassword';`

1. %标识不限制ip，也可以替换成具体ip
2. 可以将`all privileges`替换成具体的权限，例如`select,insert,update`

### 8. 设置git

![](http://doze9097.top//20191120111752.png)

![](http://doze9097.top//20191120111909.png)

![](http://doze9097.top//20191120112129.png)

![](http://doze9097.top//20191120112141.png)

![](http://doze9097.top//20191120112650.png)

![](http://doze9097.top//20191120005334.png)

![](http://doze9097.top//20191120005746.png)

gitignore文件：使得git忽略对应的文件夹

![](http://doze9097.top//1574180636701.png)

#### 本地仓库

执行`git init`初始化成功

![](http://doze9097.top//20191120005902.png)

![](http://doze9097.top//20191120110605.png)

![1574219217824](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1574219217824.png)

#### 远程仓库

![](http://doze9097.top//20191120110834.png)

![](http://doze9097.top//20191120110910.png)

![1574220508529](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1574220508529.png)

#### 添加分支

![](http://doze9097.top//20191120121733.png)

![](http://doze9097.top//20191120121809.png)

### 9. 目录结构

![](http://doze9097.top//1574181187212.png)

### 10. Tomcat配置

![](http://doze9097.top//1574181566172.png)

![](http://doze9097.top//1574181863871.png)

Artifact设置

![](http://doze9097.top//20191120004616.png)