   目前开源社区中有各种各样的快速开发平台，一般都包含了基础的菜单，角色，用户，日志，权限，字典，在加一个代码生成器，就算快速开发平台了，同质化很严重，实际在代码开发的时候，比自己公司搭建的框架省不了多少事，FHS 追求高效开发，更关注开发效率和质量，除了上述功能之外还包含以下特性：

- 1   mybatis jpa

     是mybatis 对于jpa注解的一种实现，可以不写一行代码实现crud + 批处理，一对一，一对多，数据权限，分页操作，如果你习惯了mybatis plus，他本身继承了mybatis plus，兼容mp所有注解，你可以用jpa注解，也可以用mp注解，复杂的查询交给mp，简单的用mpj。

- 2  数据权限

    通过几行配置即可完成数据权限接入，支持多重数据权限，比如通过资源  部门，和分类  做双重数据权限过滤

- 3 数据源路由

    支持分库分表读者分离，简单的配置下就好。
    分库支持不同的业务在不同的表中，或者相同的表在不同的库中，根据一个标志动态切换数据源，基于aop+自定义datasource

- 4  声明式事物

     add，update，del，save 开头的service方法，会默认开启事物，自定义部分请使用注解。
	 
- 5   美化版本的easyui+Jquery Validform

     论开发效率，easyui可以称王，谈到他每次大家都说他丑，于是我们花费了大量时间去美化essyui，定制出了一套类  layui的皮肤，解决easyui颜值问题，针对于easyui检验框架不好用，时间插件不够强大的问题，我们定制了my97 和Jquery Validform，使用更简单，一行代码搞定检验(我说他是现有的，最好用的校验框架，不服来辩)。

- 6   jsp+beetl 双模板引擎支持 + 标签封装
    
	fhs关注效率，前端copy代码很常见，但是copy完了有了bug可能会忘记改其他的地方，copy我代码的人不知道，我也不知道谁copy了我，自定义标签解决了这个问题，他把一个表单内容，封装简化到了极致，程序员不需要知道百度地图如何对接，省市区级联怎么做，um编辑器怎么做，上传怎么做，一行代码统统搞定（每个表单元素一行代码）。

- 7   放大招pagex 引擎，让java开发速度超过c#  php（java新玩法，专利设计）
    
	想到java，就想到重启，JREBEl，能做到大部分时候不重启，想用jfinal，又怕生态不是太好（生态可以，但是没办法和spring比），pagex，是把一张表通过一段js描述出来，来配置表名字，中文备注，列表有什么属性，每个字段宽度多少，是否需要关键查询，是否需要字典翻译，过滤条件有哪些是like  between 还是等于，自定义按钮名称和点击事件配置，表单元素配置，给h5 app 门户网站开的api 接收什么where条件参数，返回数据包含哪些字段，不包含哪些字段，表在哪个库中（一个项目连接多个库适用），一个js文件搞定，不需要写java，sql，都在运行时候根据js配置动态生成了（动态生成sql放到mybatis中，动态生成java代码并且编译为class并读取），js修改后自动刷新内存中的缓存，无需重启，你可以做到在项目运行阶段，直接加一个无多少业务的CRUD+API功能到你的系统中来。
	下面是我们的一个月租户CRUD的demo。
```javascript

    var modelConfig= {title:'月租户类型',pkey:'id',type:'uuid',orderBy:'update_time Desc',
        namespace:"parking_lease_type",table:'t_park_lease_type',trans:true,db:"park"};
    
    var listPage={
        listFieldSett:function(){
    	  return [
    		  {name:'lease_name',title:'类型名称',width:'20%',align:'center'},
              {name:'park_id',title:'停车场名称',width:'20%',isJoin:true,namespace:'parking',showField:'transMap.parkName',align:'center'},
              {name:'is_disable',title:'是否禁用',width:'10%',formart:'formatRowColor',align:'center',trans:'book',key:'is_disable',showField:'transMap.is_disableName'},
              {name:'create_user',title:'创建人',width:'8%',align:'center',trans:'user',showField:'transMap.create_userUserName'},
              {name:'create_time',title:'创建时间',width:'10%',align:'center'},
              {name:'update_user',title:'更新人',width:'8%',align:'center',trans:'user',showField:'transMap.create_userUserName'},
              {name:'update_time',title:'更新时间',width:'10%',align:'center'},
              {name:'is_sync',title:'是否已下发',width:'5%',align:'center',trans:'book',key:'yesOrNo',showField:'transMap.is_syncName'},
      ]},
      isColumnButton:function(){
    	  return  false;
      },
      filters:function(){
          return [
              {name:'park_id',type:'select',url:'${path.basePath}/ms/x/parking/findListData',
                  valuefield:'id',textfield:'parkName',title:'停车场'},
              {name:'lease_name',type:'input',title:'出入口名称',filterType:'like'},
    	  ];      
      }, 
      buttons:function(){
          return [
              //自定义按钮数组
          ];
      },
      disableButtons:function(){
    	    return [];//禁用掉默认提供的按钮 默认提供了增删改查 + 导出
      },
      otherFunctions:function(){
          return {}//其他的自定义方法
      }
    };
    
    var add={ 
    	formFields:function(){//表单内容
    	     return [
                 {name:'park_id',type:'select',url:'${path.basePath}/ms/x/parking/findListData',
                     valuefield:'id',textfield:'parkName',title:'停车场',required:true,},//一个下拉
                 {name:'lease_name',title:'名称',required:true,type:'input'},//一个input
                 {name:'is_disable',title:'是否禁用',type:'switch',dft:false},//一个开关滑块
                 {name:'is_sync',title:'是否下发',type:'hide'},//一个隐藏域
    		 ];
    	},
        otherFunctions:function(){
          return {
    	     ready:function(){
    	    },
    	    loadSuccess:function(info){//加载后台数据成功的事件
    
    	    },
    	    onSave:function(){//保存前执行方法
                $('#isSync').val(0);
    	    },
    		saveSucess:function(){//保存成功执行方法
    	    },
    		saveError:function(){//保存失败执行的方法
    		    
    	    },
    	  }		
       }
    }
```

- 8  翻译服务

    在项目中，我们很多列表中都可能要显示状态，数据创建人姓名，省市区 名字，难道都要关键查询吗？答案是否定的no！ 你可以通过翻译服务来把id翻译成给客户看的翻译结果，做翻译只需要一个注解，系统会自动把翻译结果放到对象中来，用于给客户显示，通过实现翻译接口，你可以实现自己的翻译类型。
	

- 9  c端支持

     支持微信，支付宝 用户自动登陆。
	 
- 10 支持分布式部署，又支持单机部署
	 
     项目集成了分布式模式和单机模式2种模式，分布式模式依赖比较多，需要安装apollo(分布式配置中心)，CAS，redis，启动文件服务jar包，静态文件jar包，eureka jar包。
	 单机模式，可以把文件服务的依赖，静态文件的依赖，都添加到自己项目的依赖中，可以关闭apollo，使用本地配置文件启动，当然，单机模式必须使用redis，因为翻译服务和spring session以及中间用到的一些分布式任务调度，分布式锁都用到了redis。
	 
	 
	 
      



#### 技术栈
- 前端:Easyui(美化过的Easyui),Layui(首页)，Validform，My 97(定制过主题)。
- 后端校验：hibernate vilidator。
- 后端：SpringBoot 1.5.13(后期升级2.x，先让别人踩坑) + Springcloud（可选）
- ORM：Mybatis(基础)+JPA(一对一&一对多查询，数据权限注解)+Plus(条件查询器)
- 模板引擎：beetl+JSP
- 无后端业务的快速开发引擎:PAGEX
- 分布式配置：Apollo

#### 安装教程

1. 单机版本
   导入 db_init.sql 到数据库
   直接checkout fhs_mini  然后在ylm文件中配置数据库，redis，直接跑即可。
   默认用户名admin 密码123456


#### 使用说明

1. 操作手册请访问  http://fhs-opensource.com/  (建设中)
2. 注意事项：pagex会在运行时动态生成java代码并且编译成class，在idea中，pagex生成java代码可直接编译通过，但是在线上环境，需要把tools.jar copy到jre的lib目录下，并且创建一个classpath的文件夹，存放编译java的时候的依赖。
2. 本快速开发平台还在开发阶段，很多bug还没修复，很多老代码还没改，不建议在正式项目中使用，等项目正式版发布在使用。我们欢迎您帮我们改几个bug，然后把代码反馈给我们。
3.clone 我们代码，然后把common，core，api,base_business,mini_admin，parent导入到idea中，配置mini_admin ylm文件中的redis信息和数据库信息，直接运行mini_admin 的 FhsMiniAdminApplication 即可。
4.如果你修改了默认端口号，请修改path.properties和js.properties中的内容。

#### 参与贡献获取技术支持
官方QQ 群：976278956

体验地址：http://114.116.20.119:8081/   admin  123456
         

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)