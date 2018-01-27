## 1. 设置Maven的默认编译级别，两种方式

### 1.1 设置属性
```xml
<properties>
    <maven.compiler.target>1.8</maven.compiler.target>
    <maven.compiler.source>1.8</maven.compiler.source>
</properties>
```
### 1.2 设置插件
```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId>
            <version>3.6.1</version>
            <configuration>
                <source>1.8</source>
                <target>1.8</target>
            </configuration>
        </plugin>
    </plugins>
</build>
```

## 2. Maven的依赖说明和介绍
> dependency中的scope

* compile
* test
* runtime
* provided
* system
* import

## 3. maven传递依赖

* 路径不同：路径最短优先
* 路径相同：先声明，先选择

## 4. 聚合和继承
> 避免重复，统一编译

* 聚合 - 相同编译过程
* 继承 - 使用相同的构建

多模块拆分示例：
* maven-db
* maven-file
* maven-commons
* maven-app

## 5. 项目打包问题
* lib包形式
* FatJar形式

## 6. 环境隔离问题
> 如何隔离不同环境的参数

使用profile，示例：
```xml
<profiles>
    <profile>
        <id>dev</id>
        <activation>
            <activeByDefault>true</activeByDefault>
        </activation>
        <properties>
            <deploy.type>dev</deploy.type>
        </properties>
    </profile>
</profiles>
```
编译命令
```shell
mvn clean package -Pdev
```
常用profile的名称：
* dev
* qa
* test
* prod

数据连接示例：
```
database.jdbc.driverClass=com.mysql.jdbc.Driver
database.jdbc.connectionURL=jdbc:mysql://localhost:3306/test
database.jdbc.username=dev
database.password=dev-pwd
```


