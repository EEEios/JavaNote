# Spring Day01 第2章

装配机制：（括号为推荐等级，1为最高级）

- 显示配置：xml（3）、java（2）
- 隐式配置：bean发现机制和自动装配（1）

配置中，没有声明ID的Bean，默认ID为类名第一个字母小写

#### 注解

@Component("{id}")：说明该类需要创建bean，id为重设id（也可以使用@Named[不推荐]）

配置类：

@ContextConfiguration(...)：为该类加载配置

@Configuration：声明该类为java类配置

@ComponentScan(basepackage**s**={" ... "," ... "})：开启扫描，数组参数为多个基础包

> 参数中：
>
> basePackageClasses：可以指定被扫描类
>
> 也可以@ComponentScan("...")

`<context：component-scan base-package="..."/>`



### 自动装配

#### 注解

@Autowired：为目标bean、方法，自动装载依赖

> 1. 若没有适合的bean，会抛出异常
>
>    可以通过将参数中 required = false 关闭
>
>    此时bean处于为装配状态，可能出现NullPointerException
>
> 2. 多个bean都满足，也会抛出遗产
>
> 使用java依赖注入规范的 @Inject 注解也可以



### Java配置

在@Configuration的配置类下：

```java
@Bean	//说明返回的对象需注册为bean
public CompactDisc sgtPeppers(){
	//bean id一般和方法名相同
	return new sgtPeppers();
}
```

注入依赖

```java
@Bean
public CDPlayer cdPlayer(){
	return new CDPlayer(sgtPeppers());//使用方法状态
}
//sgtPeppers()的调用，会被sgtPeppers()方法拦截，并检查是否已经创建过bean，若有则返回bean，而不是调用该方法重新创建一个bean。
```



或使用



```java
@Bean
@Bean
public CDPlayer cdPlayer(CompactDisc compactDisc){
	return new CDPlayer(compactDisc);//使用方法状态
}
```

此时，会自动装配CompactDisc类的bean



### XML配置



#### 构造器

#### 类依赖

```xml
<bean id="..." class="全限定类名"> 
	<constructor-arg ref="{id }">
</bean>
<!-- 注册目标class为bean -->
```



或者

c-命名空间实现

```xml
<bean id="..." class="全限定类名" c-_0=ref="{id}"/> 
```

xml配置需注意：

	- 类是否存在
	- 后期对类的重命名

### 值依赖

c-命名空间不可实现，只能由xml配置

```xml
<bean id="..." class="全限定类名"> 
	<constructor-arg value=...>
</bean
```

同样，可以使用c-命名空间，将ref改为value即可

```xml
<bean id="..." class="全限定类名" c-_0=... c-_1=.../> 
```

##### 传入集合

```xml
<bean id="..." class="全限定类名"> 
	<constructor-arg>
        <list>	<!-- <set>也可以 -->
            <value>...</value>
            <value>...</value>
            <!--
			对于对象
			<ref bean="{id}"/>
			<ref bean="{id}"/>		
			-->
        </list>
    </constructor-arg>
</bean>
```



#### 属性配置

对于强依赖使用构造器注入，可选依赖使用属性注入

```xml
<bean id="..." class="全限定类名"> 
	<property name="属性名" ref="{id }"/>
    <!-- 
	- 值传入 
  	<property name="属性名" value=.../>

	- 集合传入
	<property name="属性名">
		<value>...</value>
		或者
		<ref bean="{id}"/>
  	</property>
	-->
</bean>
<!-- name中的值要为属性名 -->
```

可以使用p-命名空间（同样不可实现传入集合）

```xml
<bean id="..." class="全限定类名"> 
    <!-- 对象传入 -->
	<property name="属性名" p:属性名-ref="{id }"/>
	<!-- 值传入 
  	<property name="属性名" p:ref=.../>
	-->
</bean>
<!-- name要与属性名匹配 -->
```



## 导入和配置的混合

- 配置类和配置类

  @Import(xx.class)

  @Import({xx.class,xxx.class})

- 配置类中导入xml

  @ImportResource("classpath:xxx.xml")

- xml和xml

  ```xml
  <import resource="xxx.xml"/>
  ```

- xml中导入java

  ```xml
  <bean class="全限定类名"/>
  ```