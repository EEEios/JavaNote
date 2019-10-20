# Mybatis

参考资料：

https://mybatis.org/mybatis-3/zh/sqlmap-xml.html

how2java

![](http://doze9097.top//1565774482155.png)

![](http://doze9097.top//1565774892756.png)

## 流程

1. 读取配置文件
2. 创建SqlSessionFactory工厂
3. 创建SqlSession
4. 创建Dao接口的代理对象
5. 执行dao中的方法
6. 释放资源

![](http://doze9097.top//1565969789259.png)

![1565970668540](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1565970668540.png)

## 操作

确定session已通过工厂开启，并在session操作完成后使用 `session.close()`关闭与数据库的连接操作

### select

#### 获取全部: 

```java
private static void listAll(SqlSession session) {
		List<Category> cs = session.selectList("listCategory");
		for(Category c : cs) {
			System.out.println(c.getName()+c.getId());
		}
	}
```

xml:

```xml
<select id="listCategory" resultType="Category">
    select * from   category_      
</select>
```

#### 获取指定目标：

```Java
private static void get(SqlSession session, int id) {
    Category c = session.selectOne("getCategory", id);
    System.out.println(c.getName());
}
```

xml:

```xml
<select id="getCategory" parameterType="_int" resultType="Category">
    select * from   category_  where id= #{id}   
</select>
```



### insert操作

1. 创建Dao代理对象，并设置对应字段值
2. 使用session对象中的`insert(xml_id, 创建的Dao代理对象)`

```java
private static void insert(SqlSession session) {
    Category c = new Category();
    c.setName("new Category");	//对新的对象的字段进行赋值
    session.insert("addCategory", c);	//插入操作
}
```

xml:

```xml
<insert id="addCategory" parameterType="Category" >
    insert into category_ ( name ) values (#{name})   
</insert>
```

### delete

1. 创建Dao代理对象，设置要操作的目标的主键字段值
2. 使用session方法操作

```Java
private static void delete(SqlSession session, int id) {
    Category c =new Category();
    c.setId(id);
    session.delete("deleteCategory", c);
}
```

xml：

```xml
<delete id="deleteCategory" parameterType="Category" >
    delete from category_ where id= #{id}  
</delete>
```

#### update

1. 获得数据库中的目标对象
2. 设置对象修改后的值
3. 使用session操作update更新

```Java
private static void update(SqlSession session, int id, String str) {//目标id和要修改成的str
    Category c = session.selectOne("getCategory", 5);
    c.setName(str);
    session.update("updateCategory", c);
}
```

xml：

```xml
<update id="updateCategory" parameterType="Category" >
    update category_ set name=#{name} where id=#{id}   
</update>
```

#### 模糊查询

匹配存在模糊pattern的字段值

```Java
private static void pattern(SqlSession session, String pattern) {
    List<Category> cs = session.selectList("patternCategory",pattern);
    for (Category c : cs) {
    System.out.println(c.getName());
    }
}	
```

xml:

```xml
<select id="patternCategory"  parameterType="string" resultType="Category">
    select * from   category_  where name like concat('%',#{0},'%')
</select>
```

concat('%',#{0},'%')为模糊匹配，mysql中为 %pattern%

### 多条件查找

1. 需要用**HashMap**存储xml中占位变量的值。
2. HashMap中的key必须与对应xml中的占位变量名通向

```Java
private static void muilt_condition(SqlSession session, int id, String pattern) {
    Map<String, Object> params=new HashMap<>();
    params.put("id", id);	//key对应xml中的占位变量名
    params.put("name", pattern);
    List<Category> cs = session.selectList("mutil_condition", params); //多参数传入
    for (Category c : cs) {	//遍历结果
        System.out.println(c.getName());
    }
}
```

xml:

```xml
<select id="mutil_condition" resultType="Category">
    select * from category_ where id> #{id} and name like concat('%',#{name},'%')
</select>
```



## 注解

参考：http://how2j.cn/k/mybatis/mybatis-annotation-crud/1093.html#nowhere

1. 创建代理接口，并实现注解

   ```Java
   import com.how2java.pojo.Category;
   public interface CategoryMapper {
   	@Insert("insert into category_ (name) values (#{name})")
   	public int add(Category category);
   	
   	@Delete(" delete from category_ where id= #{id} ") 
       public void delete(int id); 
           
       @Select("select * from category_ where id= #{id} ") 
       public Category get(int id); 
         
       @Update("update category_ set name=#{name} where id=#{id} ") 
       public int update(Category category);  
           
       @Select(" select * from category_ ") 
       public List<Category> list(); 
   }
   ```

2. 在配置文件中，导入注解接口

   ```java
     <mappers>
         <mapper resource="com/how2java/pojo/Category.xml" />   
         <mapper class="com.how2java.mapper/CategoryMapper" /> //这句为导入注解接口
     </mappers>
   ```

3. 在 执行类 中通过session导入注解接口

   ```Java
    CategoryMapper mapper = session.getMapper(CategoryMapper.class);
   ```

4. 创建对应方法，并传入代理接口进行数据操作

   ```java
   private static void add(CategoryMapper mapper) {
           Category c = new Category();
           c.setName("新增加的Category");
           mapper.add(c);
           listAll(mapper);
       }
   ```

   

