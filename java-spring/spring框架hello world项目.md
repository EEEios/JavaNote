# spring框架hello world项目

1. 在src文件下创建包**com.tutorialspoint**，并在包内创建 **HelloWorld.java** 和 **MainApp.java** 文件

   这里是 **HelloWorld.java** 文件的内容：

   ```java
   package com.tutorialspoint;
   public class HelloWorld {
      private String message;
      public void setMessage(String message){
         this.message  = message;
      }
      public void getMessage(){
         System.out.println("Your Message : " + message);
      }
   }
   ```

   下面是第二个文件 **MainApp.java** 的内容：

   ```java
   package com.tutorialspoint;
   import org.springframework.context.ApplicationContext;
   import org.springframework.context.support.ClassPathXmlApplicationContext;
   public class MainApp {
      public static void main(String[] args) {
         ApplicationContext context = 
                new ClassPathXmlApplicationContext("Beans.xml");
         HelloWorld obj = (HelloWorld) context.getBean("helloWorld");
         obj.getMessage();
      }
   }
   ```

## 第 4 步：创建 bean 的配置文件

你需要创建一个 Bean 的配置文件，该文件是一个 XML 文件，并且作为粘合 bean 的粘合剂即类。这个文件需要在 **src** 目录下创建，如下图所示：

![Spring Hello World 实例](https://atts.w3cschool.cn/attachments/image/wk/wkspring/hello5.jpg)

通常开发人员保存该文件的名称为 **Beans.xml** 文件，当然你也可以设置成任何你喜欢的名称。但是你必须确保这个文件在 CLASSPATH 中是可用的，并在主应用程序中使用相同的名称，而在 MainApp.java 文件中创建应用程序的上下文。

Beans.xml  用于给不同的 bean 分配唯一的 ID，并且控制不同值的对象的创建，而不会影响 Spring 的任何源文件。例如，使用下面的文件，你可以为  “message” 变量传递任何值，因此你就可以输出信息的不同值，而不会影响的 HelloWorld.java和MainApp.java  文件。让我们来看看它是如何工作的：

```
<?xml version="1.0" encoding="UTF-8"?>

<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
    http://www.springframework.org/schema/beans/spring-beans-3.0.xsd">

   <bean id="helloWorld" class="com.tutorialspoint.HelloWorld">
       <property name="message" value="Hello World!"/>
   </bean>

</beans>
```

当 Spring 应用程序被加载到内存中时，框架利用了上面的配置文件来创建所有已经定义的 beans，并且按照标签的定义为它们分配一个唯一的 ID。你可以使用标签来传递在创建对象时使用不同变量的值。

## 第 5 步：运行程序

一旦你完成了创建源代码和 bean 的配置文件后，就可以准备编译和运行你的程序了。为了做到这个，请保持 MainApp.Java 文件标签是**有效**的，并且在 Eclipse IDE 中使用可用的 Run 选项，或使用 **Ctrl + F11** 编译并运行你的应用程序 **MainApp**。如果你的应用程序一切都正常，将在 Eclipse IDE 控制台打印以下信息：

```
Your Message : Hello World!
```

恭喜你，你已经成功地创建了你的第一个 Spring 应用程序。通过更改 “message” 属性的值并且保持两个源文件不变，你可以看到上述 Spring 应用程序的灵活性。下一步，我们开始在接下来的几个章节中做一些更有趣的事情。