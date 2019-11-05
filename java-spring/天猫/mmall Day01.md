# 天猫超市 Day01

## mybatis-generator

1. 在pom.xml中导入相关插件
2. 在resources目录下创建generatorConfig.xml配置文件





## generatorConfig.xml解读

![](http://doze9097.top//1571673807750.png)

![](http://doze9097.top//1571673922133.png)

![](http://doze9097.top//1571674007965.png)

## mybatis逆向生成注意事项

#### 逆向生成的方法：

updateByPrimarykeySelective（选择型更新）：数据中哪个不为空更新哪个

updateByPrimaryKey：全更新