# Maven

## 目录解析：

- bin：mvn运行脚本
- boot：类加载器框架
- conf：配置文件
- lib：mvn所用的类库

- pox.xml ：用于管理包、模块的安装与挂载



## 常用构建命令

- -v 查看版本
- compile 编译
- test 测试
- package 打包
- clean 清除字节码文件
- install 安装jar包到本地仓库



## 目录创建

1. archetype:generate 按照提示进行选择
2. archetype:gennerate 
   	- -DgroupId= 组织名，公司网址的反写+项目名
      	- -DartifactId=项目名-模块名
         	- -Dversion=版本号
            	- -Dpackage=代码所存在的包名



## 仓库

- 中央仓库
- 本地仓库

### 操作

- 配置镜像仓库（settings.xml）
- 修改默认仓库位置（settings.xml）

## 生命周期

完整项目构建过程包括: 清理、编译、测试、打包、集成测试、验证、部署

maven生命周期：

- clean  清理站点
- default  构建站点
- site  生成项目站点



## pom.xml

用坐标指定约束条件

​	