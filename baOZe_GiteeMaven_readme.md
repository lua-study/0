# GiteeMaven
a gradle plugin to  publish your code to gitee  as  maven repo

将你的Android Library Module或者Java Library Module 打包发布到gitee上，作为Maven仓库可以使用maven、gradle引用。下面branch参数中的分支必须存在，暂时不能自动创建。
# Usage
### 1、config in your build.gradle file
```java
buildscript {
    repositories {
        ...
        maven { url "https://gitee.com/baOZe/testmaven/raw/master/releases" }
    }
    dependencies {
        ...
        classpath 'com.tzraeq:giteemaven:1.0.0'
    }
}
```


```java
apply plugin: 'maven'
apply plugin: 'giteemaven'
giteemavenGitRepo {
    organization = '码云的组织名称'
    repository = '作为maven仓库的项目名称'
    branch = 'master'
    type = 'releases'
}

giteemavenLibrary {
    group = 'com.tzraeq'
    artifactId = 'test_lib'
    version = '1.4.5'
    packaging = 'aar'
    description = "description"
}
```
### 2、run uploadToGit gradle task like "gradle uploadToGit"

### 3、use libray like this：
```java
repositories {
    maven { url "https://gitee.com/baOZe/maven/raw/maven/releases" }
}

dependencies {
    compile 'net.tzraeq:test_lib:1.4.5'
}
```

# dev
### 1、修改代码后，执行'gradle uploadArchives'，将自动上传插件打包到一个本地仓库目录

### 2、打开测试工程的plugin注释，执行'gradle uploadToGit'


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)