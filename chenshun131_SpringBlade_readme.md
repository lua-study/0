#Spring-Blade java开发平台
## 平台简介
Spring-Blade是基于多个优秀的开源项目，高度整合封装而成的快速开发平台。（主要用于交流学习）  
ps:因为喜欢刀锋战士所以取名了SpringBlade，当中有一个类也命名为Blade。
但是后来发现已经有了一个高人气的开源作品：Blade，作者是 王爵。
很尴尬，不过还是需要在这儿声明一下。

## 鸣谢
1.[JFinal](http://www.oschina.net/p/jfinal)
2.[eova](http://www.oschina.net/p/eova)
3.[hutool](http://www.oschina.net/p/hutool)
4.[beetl](http://www.oschina.net/p/beetl)
5.[dreamlu](http://www.oschina.net/p/dreamlu)

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
		Notice notice = mapping(PERFIX, Notice.class);
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
		Notice notice = mapping(PERFIX, Notice.class);
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
	List  list = Db.selectList("select * form news where title = #{title}", Record.create().set("title", "标题测试"));
```

 自定义sql查询,返回String(使用多数据源)
```
	String editor = Db.init("otherDb").queryStr("select editor form news where newsId = #{newsId}", Record.create().set("newsId", 123));
```

 根据条件修改
```
	boolean temp = Blade.create(News.class).updateBy("editor = #{editor}", "title = #{title}", Record.create().set("title", "测试标题").set("editor", "编辑一"));
```

 根据条件删除
```
	String ids = "1,2,3,4,5";
	String[] idArr = ids.split(",");
	int cnt = Blade.create(News.class).deleteBy("status in (#{join(ids)})}", Record.create().set("ids", idArr));
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
		Notice notice = mapping(PERFIX, Notice.class);
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
					map.put("createrName", Func.getDictName(102, map.get("creater")));
				}
			}
		});
		
		return grid;
	}
```

注：
=======

欢迎提出更好的意见，大家共同进步  
SpringBlade主要用于交流学习，开源协议署名为smallchill的代码可以随便商用，随便改。  
但是如果因为商业用途引起的纠纷和造成的一切后果请自行承担，谢谢。  
登陆名密码：两个 admin




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)