- 成员变量和局部变量
- 静态变量：用于一个类中的属性，使得其能够被其他对象共享访问
- 静态方法：静态方法可以直接调用
  - 静态方法中可以直接调用**同类**中的静态成员，调用非静态成员需要创建类的对象，然后通过对象来访问非静态变量。
  - **普通成员方法**（没有static）则可以直接访问非静态变量和静态变量

- 初始化块：可以通过该块对变量进行初始化，比构造方法优先执行（静态初始化块>初始化块>初始化构造方法）

  - 静态初始化块在类加载的时候执行，且只执行一次。且仅能给**静态变量**赋值

  > 复习：
  >
  > 初始化构造方法的方法名和类名一样，可以对对象进行初始化。

## 访问修饰符

![1562479520415](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1562479520415.png)

## this关键字：当前对象

由于在封装中，参数名字往往与属性名字相同，为了区分参数和属性，使用this关键字。

## super关键字

代指当前子类的父类

## Java中的包

作用：

- 管理Java文件

			- 解决同名文件的冲突

定义：使用  `package 包名`，且必须放在源代码的第一行。

​				包名中间可以用 . 来隔开，类似文件中 pan/a/b.txt 中的/。

使用：使用 `impoort 包名`，包名必须用小写字母。

## 内部类

类中定义类，分为外部类和内部类。

- 内部类定义 `内部类 对象名 = 外部类对象.new 内部类( );`

- 外部类不能直接访问内部类的成员和方法。

- 内部类分为：
  - 成员内部类

    > 成员同名时，内部类默认访问自己的成员，若要访问外部类成员，可以使用this。
    >
    > - `外部类名.this. 变量名`，其中`外部类名.this`是为了将this切换为外部类对象

  - 静态内部类

    > 静态内部类不能直接访问外部非静态成员，但可以通过 **new 外部类().成员** 的方式访问 。
    >
    > 静态内部类可以直接创建，不用先创建外部类对象。
    >
    > 外部静态成员和内部类成员同名时，可以通过 **外部类名.静态成员**访问，若不同名，可以通过成员名直接访问。

  - 方法内部类

  - 匿名内部类

    - 常与接口的使用配合
    - 匿名内部类就是没有名字的内部类，多用于关注实现而不关注实现类的名称

## Object类

顶级父类

![1562504119601](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1562504119601.png)

### toString()方法（掌握子类的toString()方法的重写）

若`System.out.println(某类名)`则会输出该对象的对象地址字符串。

## equals()方法

比对对象的引用是否只想同一块内存地址。

## 面向对象的三大特性

### 封装：

外部不能直接访问类内的信息，而是通过该类提供的方法来实现对隐藏信息的访问

方法：1. 修改**属性**的修饰符，改为（添加） private

​			2. 创建getter/setter方法（为通常命名，为public，用于属性读写），并在方法中加入属性控制语句

### 继承：

子类拥有父类的所有属性和方法（不为private的）[代码复用]

继承使用：class 子类 extends 父类{}

方法重写：重写父类方法，且返回值类型、方法名、参数类型及个数都与从父类继承的方法相同。

final关键字：使用该关键字修饰，该类不允许被继承、方法不能被重写、属性不会

### 多态：

![1562504737741](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1562504737741.png)

- 引用多态

​	![1562504696993](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1562504696993.png)

- 方法多态

![1562504836609](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1562504836609.png)

### 引用类型转换

![1562504965304](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1562504965304.png)

![1562505289288](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1562505289288.png)

### 抽象类

abstract关键字修饰。

![1562505601619](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1562505601619.png)

![1562505613360](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1562505613360.png)

![1562505681810](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1562505681810.png)

## 接口（命名时前面通常加I）

接口可以理解为一种特殊的类，由全局常量和公共的抽象方法所组成。

规定了某些类必须提供某些方法。

### 定义

使用 interface 关键字代替 class

![1562506106076](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1562506106076.png)

其中修饰符后面会有abstract关键字，没有系统会默认添加

[父接口]是可选，可以选择是否继承父接口。

![1562506181459](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1562506181459.png)

![1562506188969](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1562506188969.png)

### 使用implements继承父类实现接口：

![1562506335570](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1562506335570.png)

### 配合匿名内部类

![1562507114230](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1562507114230.png)

或者

![1562507084424](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1562507084424.png)