# Mybatis-Spring

## 1. DriverManagerDataSource

配置数据库驱动、url、账号密码

```xml
<bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
            
            <property name="driverClassName">
                <value>com.mysql.jdbc.Driver</value>
            </property>
            
            <property name="url">
                <value>jdbc:mysql://localhost:3306/how2java?characterEncoding=UTF-8</value>
            </property>
            
            <property name="username">
                <value>root</value>
            </property>
            
            <property name="password">
                <value>root</value>
            </property>
            
        </bean>
```



## 2. SqlSessionFactoryBean

相较于Mybatis的工厂模式，在Mybatis-Spring中是由SqlSessionFactoryBean配置的。

并需要在applicationContext.xml中进行配置。

```Xml
<bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">  
       <property name="dataSource" ref="dataSource" />  
       <property name="mapperLocations"  
              value="classpath:com/tiantian/ckeditor/mybatis/mappers/*Mapper.xml" />  
       <property name="typeAliasesPackage" value="com.tiantian.ckeditor.model" />  
</bean>
```

> - mapperLocations：
>
>   表示Mapper文件存放的位置，当我们的Mapper文件跟对应的Mapper接口处于统一位置时可以不用指定该属性值。
>
> - configLocation：（待补充）
>
>   指定Mybatis配置文件的文件位置。
>
> - typeAliasesPackage：
>
>   对应实体类所在的**包**，多个package之间可以用逗号或者分号隔开。

## 3. MapperScannerConfigurer

![img](https://img-blog.csdn.net/20180531192650426?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tldmluX2xvdmluZw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)