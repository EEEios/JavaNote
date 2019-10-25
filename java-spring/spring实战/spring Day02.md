 # spring Day02 AOP



### 第三章被跳过



### 第四章 面向切面的Spring

术语：通知（advice）、切点（pointcut）、连接点（join point）

通知类型（P103）
通知：什么、何时
连接点：能够应用通知的所有点
切点：何处，定义了通知被应用的具体位置
切面：通知和切点的结合
织入：将切面应用于目标对象

spring仅支持AspectJ切点指示器的一个子集

切点编写：P108

### 注解 P111

@Aspect 标注该类是一个切面
@Pointcut 定义一个可重用的切点 P112，最好提供一个标示
@Before
@AfterReturning
@AfterThrowing

### 启用AspectJ注解的自动代理
JavaConfig：@EnableAspectJAutoProxy
xml：\<aop:aspect-autoproxy/\>

### 环绕通知
让所编写的逻辑在被通知的目标方法完全包装起来。
就好像在一个通知方法中实现了前置通知和后置通知。

编写逻辑中：
	⁃	接受 ProceddingJoinPoint 作为参数
	⁃	使用 上述参数的proceed()将控制权转入目标中。（可多次或者不调用）



#### 为切面方法提供参数（P116）



#### 通过**引入**为bean添加新的方法（p119）

即为目标对象提供新接口

 @DeclareParents(value=... , defaultImpl=...)



### xml中切面的配置	p121

```xml
<aop:config>
    <aop:aspect ref="切面类">
    	<aop:before
         	pointcut="excution(......)"
            method="切面类中的方法名"/>
    </aop:aspect>
</aop:config>
```

pointcut重用的方式

```xml
<aop:config>
    <aop:aspect ref="切面类">
    <aop:pointcut
        id="..."
        expression="execution(....)"/> <!-- 在此声明了切点 -->
    	<aop:before
         	pointcut-ref="切点id"	<!-- 对切点进行引用 -->
            method="切面类中的方法名"/>
    </aop:aspect>
</aop:config>
```



环绕通知：在方法中同样要使用ProceddingJoinPoint参数和proceed()方法

```xml
<aop:config>
    <aop:aspect ref="切面类">
    <aop:pointcut
        id="..."
        expression="execution(....)"/>
    	<aop:around
         	pointcut-ref="切点id"
            method="切面类中的方法名"/>
    </aop:aspect>
</aop:config>
```



未通知传递参数

```xml
<!-- 其他元素和上相同，故省略 -->
<aop:pointcut
        id="..."
        expression="execution(....) and args(...)"/>
<!-- args()中的参数名需和形参相同 -->
```



通过切面引入新功能

```xml
<aop:aspect>
    <aop:declare-parents
        types-matching="需要注入新方法的类/类集"
        implement-interface="新方法"
        delegate-ref="存在新方法的bean"/>
    <!-- delegate-ref也可以替换为default-impl="全限定类名"指定 -->
</aop:aspect>
```





### 4.5被跳过（AspectJ待了解）



