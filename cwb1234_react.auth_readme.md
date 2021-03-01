# react.auth

## 项目介绍
1. 本项目是带有完整权限系统的react管理后台
2. 本项目后台系统采用SpringDataJPA

## 项目开发
1. java项目使用eclipse maven导入
2. react项目使用桌面版ICEWorks2.6版本导入 或使用npm命令开启调试
3. 导入数据库

## 开发规范

### 路由配置
1. 路由配置为 router.js
2. 路由分为两层结构，第一层为全局页面，第二层为Layout页面
3. 路由页面需注意主题功能在前，举例：【/auth/index】主题功能为auth，具体实现为index
4. 新增数据页面，具体实现功能应为add 【/auth/add/:pid】
5. 修改数据页面,具体实现功能应为edit 【/auth/edit/:id】

### form表单应继承FormBase
举例：
``` javascript
        constructor(props) {
		super(props);
                //初始化数据
		this.state = this.initPropState()
	}

	componentDidMount = async () => {
                //若为编辑数据，则加载原始数据
		if(this.edit){
			let detail = await Auth.detail(this.id)
			this.setState({ value : detail })
		}
	}

	validateAllFormField = () => {
		this.refs.form.validateAll(async (errors, values) => {
			if (errors) { return; }
			//提交前校验数据
                        if(!this.validateAll(values)){ return }
			await Auth.save(values)
			Message.success('提交成功');
			this.props.history.push({ pathname : '/auth/index' });
		});
	};
```

## 权限
1. 路由和菜单权限已集成至框架中
2. 按钮权限可导入Auth组件进行校验
``` javascript
import { Auth } from '@/components/Auth'
...
 
     提交 
 
```
3. 代码校验权限规范
``` javascript
import { withAuth } from '@/components/Auth'
...
  this[key](item) }>
     新增 
     编辑 
     
     删除 
 
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)