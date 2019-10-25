# Json

## Json包

1. 导入json包

2. 创建JSONObject对象

   > 方法：
   >
   > 1. put(key , value)；
   >
   > 2. 将hashMap当作参数传入构造方法也可	//hashMap实现
   > 3. java bean创建json，将bean传入构造函数



## Gson包

1. @SeruzakuzedName()

2. 构建GsonBuilder对象

   > ![](http://doze9097.top//1571980529765.png)
   >
   > setPrettyPrinting()；//美化输出格式

#### 技巧:

1. ![](http://doze9097.top//1571980720734.png)



2. 声明 transient 可以忽略掉空值![](http://doze9097.top//1571980812437.png)

3. 读取（可以生成指定的对象）

   ![](http://doze9097.top//1571981024112.png)

4. 带日期的解析

   ![](http://doze9097.top//1571981106046.png)

   设置日期模板

5. 支持list的解析

