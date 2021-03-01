# mysqld

用于 JUnit 单元测试的、嵌入式 MySQL 服务器。

# 背景

做数据库相关的程序开发，单元测试通常会连接一个 MySQL 服务器。当涉及多人协同开发时，要么建立一个所有人都能访问的 MySQL 测试服务器；要么每个人在自己的开发环境中搭建一个实例。两种方案在后期维护上都不是很方便，最好能像 SQLite3 或 H2 一样提供内存中临时的数据库，执行单元测试时自动从零搭建数据库、添加测试数据，完成后自动清空。

# 原理

`me.zzp/mysqld` 通过 `mysql/mysql-connector-mxj` 来实现嵌入的 MySQL 服务器。`mysql-connector-mxj` 是将整个 MySQL 的可执行文件打包进 jar 中（因此文件很大），执行时解压到指定目录，再通过调用外部程序来启动临时的 MySQL 服务器。

# 使用方法

## 一、在 maven 中添加如下依赖：

```xml
 
    ...
     
         
             zzp-mvn-repo 
             http://10.0.40.218 
         
     

     
        ...
         
             junit 
             junit 
             4.12 
             test 
         
         
             me.zzp 
             mysqld 
             1.0.0 
             test 
         
         
             ch.qos.logback 
             logback-classic 
             1.1.7 
             test 
         
     
 
```

因为 `me.zzp/mysqld` 依赖 `slf4j-api`，所以需要提供 `slf4j` 的任意一个实现。

## 二、编写测试用例

```java
package me.zzp.mysql.file;

import me.zzp.mysqld.Mysqld;
import org.junit.AfterClass;
import org.junit.BeforeClass;

public class FooTest {

    private static Mysqld mysql;

    @BeforeClass
    public static void setUpClass() {
        mysql = Mysqld.start();
    }

    @AfterClass
    public static void tearDownClass() {
        mysql.close();
    }
}
```

通过 Mysqld.start() 启动 MySQL 实例；Mysqld::close() 关闭数据库，进程退出。其中 start 方法提供了三种形式：

* start(String root, int port)
  * root：MySQL的可执行文件和数据文件存放路径
  * port：数据库端口
* start(int port)：
  * root：如果设置了系统属性 zzp.mysqld.root，则使用其值；否则使用默认的 mysqld
  * port：使用参数指定的端口
* start()
  * root：如果设置了系统属性 zzp.mysqld.root，则使用其值；否则使用默认的 mysqld
  * port：如果设置了系统属性 zzp.mysqld.port，则使用其值；否则使用默认的 3306

root 对应的路径必须是一个文件夹，如果不存在会自动创建，因此必须有写入的权限；
port 对应的端口如果被其他进程占用，则启动失败。

# 结合 maven-surefire-plugin

JUnit 默认会为每一个 TestCase 启动一个 MySQL 服务器，结束时关闭。因此 MySQL 服务器会不断地启动、关闭，效率非常低。

使用 maven-surefire-plugin 插件可避免反复地重启，而是在所有单元测试执行前启动一个全局共享的 MySQL 实例，并在所有单元测试执行完毕后自动关闭。配置方法如下：

```xml
 
    ...
     
         
             
                 org.apache.maven.plugins 
                 maven-surefire-plugin 
                 2.19.1 
                 
                     
                         
                             listener 
                             me.zzp.mysqld.MysqldRunListener 
                         
                     
                     
                         mysqld 
                         3306 
                     
                 
             
         
     
 
```

其中 `zzp.mysqld.root` 与 `zzp.mysqld.port` 两个系统属性为可选属性。意义与上文的 `root` 和 `port` 相同。

配置完成后测试代码无需调整，执行 `mvn test` 就能自动执行所有的测试用例。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)