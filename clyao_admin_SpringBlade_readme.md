#Spring-Blade java开发平台
## 平台简介
Spring-Blade是基于多个优秀的开源项目，高度整合封装而成的快速开发平台。
PS:因为喜欢刀锋战士所以取名了SpringBlade，当中有一个类也命名为Blade。
但是后来发现已经有了一个高人气的开源作品：Blade，作者是 王爵。感觉很巧合，所以在这儿声明一下。
特别感谢下[如梦技术](http://git.oschina.net/dreamlu), 分享产出了很多优质项目, 让我进步很大！

## 鸣谢
1.[JFinal](http://www.oschina.net/p/jfinal)
2.[eova](http://www.oschina.net/p/eova)
3.[hutool](http://www.oschina.net/p/hutool)
4.[beetl](http://www.oschina.net/p/beetl)
5.[beetlsql](http://www.oschina.net/p/beetlsql)
6.[dreamlu](http://www.oschina.net/p/dreamlu)
7.[kisso](http://www.oschina.net/p/kisso)
8.[spring-shiro-training](https://git.oschina.net/wangzhixuan/spring-shiro-training)

## 内置功能

1.	用户管理
2.	角色管理
3.	菜单管理
4.	字典管理
5.	部门管理
6.	附件管理
7.	参数管理
8.	连接池监视
9.	日志管理

## 技术选型

1、后端

* 核心框架：Spring Framework
* 安全框架：Apache Shiro
* 视图框架：Spring MVC
* 服务端验证：Blade Validator
* 任务调度：Spring Task
* 持久层框架：beetlsql
* 模板引擎：beetl
* 数据库连接池：Alibaba Druid
* 缓存框架：Ehcache
* 日志管理：SLF4J、LOGBACKUP
* 工具类：Apache Commons、FastJson、EASYPOI、BladeToolBox

2、前端

* JS框架：jQuery
* CSS框架：Twitter Bootstrap
* 客户端验证：JQuery-html5Validate
* 富文本：KindEcitor
* 数据表格：jqGrid
* 树结构控件：jQuery zTree
* 弹出层：Layer
* 日期控件： LayDate

## 后台界面
![后台界面](http://git.oschina.net/uploads/images/2016/0706/091736_144317b3_474499.png "后台界面")
![后台界面](http://git.oschina.net/uploads/images/2016/0706/092002_1dd317a7_474499.png "后台界面")
![后台界面](http://git.oschina.net/uploads/images/2016/0706/110441_d286b7c7_474499.png "后台界面")
![后台界面](http://git.oschina.net/uploads/images/2016/0706/110523_4a5256ff_474499.png "后台界面")
![后台界面](http://git.oschina.net/uploads/images/2016/0706/111014_9292e52f_474499.png "后台界面")
![后台界面](http://git.oschina.net/uploads/images/2016/0706/110631_bc667dc7_474499.png "后台界面")

## 代码示例
实体类
```
@Table(name = "notice")
@BindID(name = "id")
@SuppressWarnings("serial")
public class Notice extends BaseModel {
	private String id;
	private Integer creater;
	private String content;
	private String title;
	private Date createTime;

	@AutoID
	@SeqID(name = "SEQ_NOTICE")
	public String getId() {
		return id;
	}

	public void setId(String id) {
		this.id = id;
	}	
	.....................
		
}
```

 新增
```
	@ResponseBody
	@RequestMapping(KEY_SAVE)
	public AjaxResult save() {
		Notice notice = mapping(PREFIX, Notice.class);
		boolean temp = Blade.create(Notice.class).save(notice);
		if (temp) {
			return success(SAVE_SUCCESS_MSG);
		} else {
			return error(SAVE_FAIL_MSG);
		}
	}
```

 修改
```
	@ResponseBody
	@RequestMapping(KEY_UPDATE)
	public AjaxResult update() {
		Notice notice = mapping(PREFIX, Notice.class);
		boolean temp = Blade.create(Notice.class).update(notice);
		if (temp) {
			return success(UPDATE_SUCCESS_MSG);
		} else {
			return error(UPDATE_FAIL_MSG);
		}
	}
```

 删除
```
	@ResponseBody
	@RequestMapping(KEY_REMOVE)
	public AjaxResult remove(@RequestParam String ids) {
		int cnt = Blade.create(Notice.class).deleteByIds(ids);
		if (cnt > 0) {
			return success(DEL_SUCCESS_MSG);
		} else {
			return error(DEL_FAIL_MSG);
		}
	}
```

 自定义sql查询,返回map
```
	List  list = Db.selectList("select * form news where title = #{title}", Paras.create().set("title", "标题测试"));
```

 自定义sql查询,返回String(使用多数据源)
```
	String editor = Db.init("otherDb").queryStr("select editor form news where newsId = #{newsId}", Paras.create().set("newsId", 123));
```

 根据md文件的sql执行修改
```
	int cnt = Md.update("news.update", Paras.create().set("title", "标题测试").set("id", "1"));
```

 根据条件修改
```
	boolean temp = Blade.create(News.class).updateBy("editor = #{editor}", "title = #{title}", Paras.create().set("title", "测试标题").set("editor", "编辑一"));
```

 根据条件删除
```
	String ids = "1,2,3,4,5";
	String[] idArr = ids.split(",");
	int cnt = Blade.create(News.class).deleteBy("status in (#{join(ids)})", Paras.create().set("ids", idArr));
```

## 通用Service
```
	public interface NoticeService extends IService  {
	
	}
	
	
	@Service
	public class NoticeServiceImpl extends BaseService  implements NoticeService {
	
	}


	@Autowired
	NoticeService service;

	@ResponseBody
	@RequestMapping(KEY_SAVE)
	public AjaxResult save() {
		Notice notice = mapping(PREFIX, Notice.class);
		boolean temp = service.save(notice);
		if (temp) {
			return success(SAVE_SUCCESS_MSG);
		} else {
			return error(SAVE_FAIL_MSG);
		}
	}

```

## 分页
```
	@ResponseBody
	@RequestMapping(KEY_LIST)
	public Object list() {
		Object grid = paginate(LIST_SOURCE, new IQuery() {
			
			@Override
			public void queryBefore(AopContext ac) {
				if (ShiroKit.lacksRole(ConstShiro.ADMINISTRATOR)) {
					String condition = "and creater = #{creater}";
					ac.setCondition(condition);
					ac.getParam().put("creater", ShiroKit.getUser().getId());
				}
			}
			
			@Override
			public void queryAfter(AopContext ac) {
				@SuppressWarnings("unchecked")
				BladePage > page = (BladePage >) ac.getObject();
				List > list = page.getRows();
				for (Map  map : list) {
					map.put("createrName", SysCache.getDictName(102, map.get("creater")));
				}
			}
		});
		
		return grid;
	}
```

注：
=======

欢迎提出更好的意见, 大家共同进步  
SpringBlade主要用于交流学习, 开源协议署名为smallchill的代码也可以进行商用
但是如果因为商业用途引起的纠纷和造成的一切后果请自行承担
登陆名密码：两个 admin

SpringBlade交流群：`477853168`  主要给大家交流学习, 本人工作比较忙, 回复的少请见谅

SpringBlade不搞捐赠, 不打广告, 只做最单纯的开源项目

常见问题
=======
##1.linux下登陆报未知错误
发布在linux的小伙伴需要做如下操作：
`vi /etc/my.cnf`
在[mysqld]节点下增加`lower_case_table_names = 1`
`:wq`
`service mysqld restart`
取消大小写敏感，就可以正常运行了

##2.连接oracle报未知错误
到resource文件夹下config.properties修改oracle链接，然后到resource/spring/applicationContext.xml找到
```
 
      
 
```
将`MySqlStyle`改为`OracleStyle`

##3.创建model后有没有自动生成javabean字段和sql的办法？
有,访问如下两个地址：
`localhost:8080/blade/generate/pojo/tfw_menu`
`localhost:8080/blade/generate/sql/com.smallchill.system.model.Menu`
查看控制台打印结果,按自己需求复制粘贴到model和md文件中



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)