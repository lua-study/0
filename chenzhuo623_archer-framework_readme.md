
# 概述
archer-framework是一个旨在构建RESful风格WEB服务的轻量级框架。

# 主要特点
1.	采用面向服务的设计，服务端提供的API可以为PC WEB端、移动端、微信公众号等不同的客户端提供服务。
2.	易于构建前后端分离的应用，客户端和服务端通过服务端对外暴露的RESful API 进行交互，服务端开发人员可以专注于业务逻辑的开发，而客户端开发人员则可以采用自己熟悉的语言来做界面展现。
3.	第三方系统可以方便的调用服务端提供的API，服务端提供的API不仅可以为内部产品进行服务，还可以为第三方系统提供服务。
4.	多种安全策略保障服务的安全性。包括IP控制、UA控制、第三方系统接口调用频率、范围等多种安全策略。
5.	框架采用分模块的设计，扩展性良好，框架使用者可以根据具体的应用场景进行模块的组合以及自定义。
6.	框架内置多种服务，并且大部分都是可选和可配置的。如：安全服务、文件服务、缓存服务、EXCEL导出、短信发送服务、接口测试支持等。
7.	这是一个框架，不是一个所谓的包含用户管理、角色管理、任务调度、流程管理，包含界面的快速开发平台或者说后台管理系统。

# 相关项目
| 名称           | 说明            |
| ------------- |-------------|
| [archer-application-core](http://git.oschina.net/ArcherGroup/archer-application-core)        | 使用`archer-framework`做的服务工程演示，一个简单的用户角色权限管理系统，对外只提供API        | 
| [archer-application-manager](http://git.oschina.net/ArcherGroup/archer-application-manager)        | 使用`archer-framework`做的PC WEB端工程演示，只做界面展现。使用`archer-application-core`提供的API       |            

# 文档
- [core模块文档](/core)

# 主要技术
- 工具类：`jodd`
- web框架：`Spring MVC`
- 缓存：`ehcache` `redis`
- ORM：`ebean`  [点击此处了解更多关于ebean的知识](http://ebean-orm.github.io/docs/query/features)


# 模块列表
| 模块           | 说明            | 依赖的模块  |
| ------------- |-------------|-------------|
| [core](/core)        | 基础模块，一些工具类和数据结构定义        |            |
| [protocol](/protocol)    | 协议模块，定义了客户端和服务端接口交互的数据协议  |   `core` |
| [cache-core](/cache-core)  | 缓存接口定义                                |   `core` |
| [cache-ehcache](/cache-ehcache)| ehcache缓存实现                           |  `cache-core` `core` |
| [cache-redis](/cache-redis) | redis缓存实现                              |   `cache-core` `core` |
| [web](/web) 		| web特性支持，使用Spring MVC                  |    `core` |
| [ebean](/ebean)        | 针对ebean的扩展                            | `core` |
| [security](/security)    | 服务端API安全策略集合                        |  `web` `protocol` `core` |
| [common](/common)      | 用于构建RESful API的服务端                  |  `security` `web` `protocol` `core` |
| [groovy](/groovy)      | groovy支持，用于在项目中添加动态特性           |   `core` |
| [file](/file)        | 文件上传下载服务支持                         |    `web` `core`|
| [poi](/poi)         | excel等支持                         | `core` |
| [test-support](/test-support)| 测试支持                                   |  `protocol` `core` |
| [client](/client)      | 用于构建传统的PC WEB端                      |    `web` `protocol` `core` |


#	代码示例
- - -

###### Entity定义

```java
@Entity
public class User extends BaseEntity{

	public static final Find  find = new Find (User.class);

	@Id
	private String id;

	private String name;

	private Integer age;

    public String getId() {
        return id;
    }

    public User setId(String id) {
	    this.id=id;
	    return this;
    }

	...
}

```

###### 查询

```java
// Active Record方式查询
public ExecuteResult findList(String name , Integer age){

        return success(User.find.query()
                .where()
                .eq("name", name)
                .ge("age", age)
                .order("name")
                .findList()
        );
}

// 返回的JSON数据
{
  resultCode: "SUCCESS",
  resultMsg: "执行成功",
  resultCodeExt: null,
  resultData: [
    {
      name: "archer",
      age: 28
    },
    {
      name: "framework",
      age: 30
    }
  ]
}
```

###### 分页查询

```java
// Active Record方式查询
public ExecuteResult findPagedList(Integer pageIndex, Integer pageSize,String name ,Integer age){

        return success(
	        findPagedList(pageIndex, pageSize, User.find.query()
                .where()
                .eq("name", name)
                .ge("age", age)
                .order("name")
        );
}
```

###### 新增/保存

```java
public ExecuteResult store(String name , Integer age){
	return success(
		new User()
			.setName(name)
			.setAge(age)
			.store()
	);
}
```

###### 删除

```java
public ExecuteResult delete(String id){
	return success(
		new User()
			.setId(id)
			.logicalDelete()
	);
}

public ExecuteResult delete(User user){
	return success(
		user.logicalDelete()
	);
}
```

###### 接口测试用例

```java
static String BASE_URL = "/api/v1/internal/system/user/";

@Test
public void store() {
   post(BASE_URL + "store")
            .form("name", "archer")
            .form("age", 20)
            .sign()
            .send()
            .toString();
}
```

# Road Map
1.	新增`monitor`模块，用于对服务进行监控
2.	新增`job`模块，支持任务调度
3.	重构`common`模块，移除对`ebean`的直接依赖，新增`repository-core` `repository-ebean`模块
4.	`nodejs`版客户端开发
5.	提供更多的使用文档

# 常见FAQ

> 我可以使用`MyBatis`或者`Hibernate`作为ORM吗？
>> 可以，`archer-framework`可以兼容`MyBatis`和`Hibernate`，你甚至可以在一个方法里混合使用`ebean`，`MyBatis`完成整个业务，不用担心事务问题。


>`archer-framework`使用什么协议？
>>`archer-framework`使用[Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0) 协议

>我在使用中发现了bug，我要如何报告这个bug？
>> 你可以在git上提交issue，说明问题的现象，错误日志等，我们会在第一时间予以排查和修复。

>有没有其他的交流途径？
>> 你可以加入qq群 `473615503` 和大家一起交流。

#	特别鸣谢
- [ebean](https://github.com/ebean-orm/ebean)  有了ebean我已经很久没写过sql语句了

- [springside](https://www.oschina.net/p/springside) 大家都懂的~

- [jodd](https://www.oschina.net/p/jodd) 大爱不解释

enjoy :)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)