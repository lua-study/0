#O2O

## 模块介绍

* **core模块**作为核心模块，包括了主要的业务流程
* **server模块**作为HTTP连接层服务，用来将HTTP协议与core核心模块进行连接
* **server/RESTAPI模块**作为server模块的核心功能子模块，在这个文件夹下，任何以`.rest.js`作为后缀结尾的文件将自动转化为RESTFUL风格的API接口

### 编写REST风格的API
`.rest.js`的文件规范是。返回的对象使用以下结构：
```js
{
	prefix:"PATHNAME",// 比如"/z/z/z"，匹配的时候就是匹配到http://localhost:3000/z/z/z.....
	get:{// get 方法
		"/:xxx":function *(next){// 将匹配GET方法的URL：http://localhost:3000/z/z/z/任意
			// TODO:.....
			this.params.xxx === "任意";
			return next;		
		}
	},
	//...其它HTTP方法，比如POST，PUT，DELETE
}
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)