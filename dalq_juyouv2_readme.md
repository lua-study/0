##居游系统 v2.0
居游票务分销，景区管理，线路计调的前端项目。 

工具：angularjs, ui-router, angular-datatables, bootstrap, webpack, nginx, npm 3.10.3, node 6.7.0

测试地址：  

##安装
项目获取

	git clone https://git.oschina.net/dalq/juyouv2.git
	
进入项目文件夹

	npm install
	npm start
	
启动nginx（找相关人员获取nginx配置文件）。

##项目介绍

**app/index.js** ： 是程序的入口，包括文件导入，模块加载，配置文件加载和界面初始路由。

**模块** ： 若干模块组成了整个项目，每个模块由数字序号和模块名组成。每个模块包含了__app.js__,__router.js__,__service.js__,__controllers文件夹__,__views文件夹__。

* **app.js** 模块入口文件，声明该模块，为模块配置路由，控制器，服务，指令等一系列配置。
* **router.js** 路由文件，该模块的路由配置。

		//景区列表
		.state('app.view_list', {
        	url: "/view/viewlist.html",
        	views: {
          	'main@' : {
                template : require('../996tpl/views/table.html'),
                controller : 'viewlist',
          		}
        	},
        	resolve:{
            	tableconfig : function(tableservice){
                	return tableservice.tableconfig();
            	},
        	}
    	})
    	
	* **app.view_list** ： 该路由的唯一标识，不能重复。

	* **url: "/view/viewlist.html"**  ：该路由在地址栏里显示的信息。

	* **template : require('../996tpl/views/table.html')**  ： 该路由绑定的模板。

	* **controller : 'viewlist'** : 对应的控制器。该控制器在app.js中声明。

	* **resolve** : 该路由需要用的到服务。

* **service.js** : 模块的服务文件，该文件中会包括模块用到的模型和服务。
* **/controllers**: 控制器存放文件夹。
* **/views** : 视图存放文件夹。

##开发指南
#####快速创建表格
* 路由

		//景区列表
		.state('app.view_list', {
        	url: "/view/viewlist.html",
        	views: {
          	'main@' : {
                template : require('../996tpl/views/table.html'),
                controller : 'viewlist',
          		}
        	},
        	resolve:{
            	tableconfig : function(tableservice){
                	return tableservice.tableconfig();
            	},
        	}
    	})
* 控制器（viewlist）

		module.exports = function($scope, tableconfig, $state){

			tableconfig.start($scope, {
				'url' : '/api/ac/tc/placeView/list',
				'col' : [
					{'title' : '类型', 'col' : 'type'},
					{'title' : '名称', 'col' : 'name'},
					{'title' : '编号', 'col' : 'code'},
					{'title' : '城市', 'col' : 'city'},
					{'title' : '排序', 'col' : 'asort'},
					{'title' : '操作', 'col' : 'btn'},
				],
				'btn' : [
					{'title' : '查看详情', 'onclick' : 'info'},
					{'title' : '编辑', 'onclick' : 'edit'},
					{'title' : '删除', 'onclick' : 'delete'},
				],
				'search' : [
					{'title' : '名称', 'type' : 'txt', 'name' : 'name', 'show' : true},
					{'title' : '编号', 'type' : 'txt', 'name' : 'code', 'show' : true},
					{'title' : '城市', 'type' : 'txt', 'name' : 'city'},
					{'title' : '类型', 'type' : 'txt', 'name' : 'type'},
				],
				'title' : '景区列表',
				'info' : {
					'to' : 'app.view_info',
				},
				'delete' : {
					'url' : '/api/ac/tc/placeView/delete',
				},
				'edit' : {
					'to' : 'app.view_edit'
				}
			});
			$scope.table = tableconfig;
		
		};

	* url ： 数据接口，获取的数据项里必须包含id字段，约定用该字段对每条数据做唯一标识
	* para : 调用数据接口传入的参数
	* col : (array)
		* title : 表头
		* col : 字段名（数组：多行显示）'btn':表示按钮组。
		* default : 默认的显示文本，如果查不到数据的话就用这个作为默认显示。
		* click : 该列的点击事件。
	* btn : (array)表格最后一列按钮组里的按钮列表
		* title : 按钮名称
		* onclick : 点击事件
		* show : 某些列等于指定值，显示该按钮,例如('show' : {'system_sort' : '2', 'state' : '1'})
	* search : 搜索项目
		* title : 搜索标题
		* type : 搜索类型(txt:文本框，select:下拉框，date1:单个时间框，date2:时间段)
		* name : 字段名
		* show : true默认显示，（false或者默认不添）不显示
	* dataprop : 数据解析方式，默认是'data.results'。
	* page : 是否分页（yes/no），默认'yes'分页。
	* title : 页面标题。
	* btns : 表格上方的按钮。
		* name : 按钮名。
		* click : 点击事件。
	* info : 默认的详情方法。
		* para : 跳转详情页面传的参数。不添的话默认成id
		* to : 详情页面的路由。
	* del : 默认的删除方法。
		* para : 跳转详情页面传的参数。不添的话默认成id
		* url : 删除的接口。
	* edit : 默认的编辑方法。
		* para : 跳转详情页面传的参数。不添的话默认成id
		* to : 详情页面的路由。
	* btnstyle : 操作按钮显示类型，默认：下拉，btns:按钮平铺，

	
#####快速创建表单
* 路由

		//创建渠道
		.state('app.channelTemp_create', {
		    url: "/channelTemp/create.html",
		    views: {
		        'main@' : {
		            template : require('../996tpl/views/form.html'),
		            controller : 'channelTempcreate',
		        }
		    },
		    resolve:{
		        formconfig : function(formservice){
		            return formservice.formconfig();
		        },
		        model : function(channelTempservice){
		            return channelTempservice.model;
		        }
		    }
		})
		
* 模型

	    var model = [
	        {
	            'title' : '渠道模板名称',
	            'id' : 'templete_name',
	            'type' : 'text',
	            'required' : true,
	            'placeholder' : '必填',
	        },
	        {
	            'title' : '渠道模板图片',
	            'id' : 'templete_img',
	            'type' : 'image',
	        },
	        {
	            'title' : '商品模板锁定模型',
	            'id' : 'templete_lock_data_json',
	            'type' : 'static',
	        },
	        {
	            'title' : '校验模型',
	            'id' : 'templete_check_data_json',
	            'type' : 'static',
	        },
	    ];
	    
	* title : 表单元素名。
	* id : 字段名。
	* type : 类型
		* text : 文本框
		* number : 数字
		* static : 文本
		* checkbox : 多选按钮
			* info : (array)
				* name : 文本
				* value : 值
		* radiobutton : 单选按钮
			* info : (array)
				* name : 文本
				* value : 值
		* select : 下拉框
			* info : (array)
				* name : 文本
				* value : 值
			* url : 下拉信息接口，默认用 name做显示名，value做值。
			* n : 要做显示的信息字段
			* v : 要做值的信息字段
		* date1 : 日期选择
		* switch : 开关
			* open : 开启状态的值
			* close : 关闭状态的值
		* textarea : 文本域
			* state : normal普通的文本域，不填是富文本域
		* image : 图片
			* tip : 图片提示
		* button : 按钮
			* info : 数组
				* label : 按钮文字
				* btnclick : 点击事件
		* table : 表格
			* title : 列名
			* col : 字段名
			* clickname : 按钮名
			* click : 点击事件
	* value : 值
	* required : 必填
	* placeholder : 文本框默认提示。

* 控制器

		module.exports = function($scope, formconfig, $stateParams, model){
		
			var id = $stateParams.id;
		
			formconfig.start({
				'title' : '渠道模板详情',
				'formtitle' : '渠道模板基本信息',
				'elements' : model(),
				'info' : {
					'url' : '/api/ac/tc/channelTemplete/info',
					'para' : {'id' : id}
				},
				'save' : {
					'url' : '/api/ac/tc/channelTemplete/update',
					'to' : 'app.channelTemp_list',
					'para' : {'id' : id}
				}
			}, $scope);
		
			$scope.form = formconfig;
		
		};
		
	* title : 页面标题
	* formtitle : 表单标题
	* elements : 数据模型
	* info : 表单数据
		* url : 获取数据接口
		* para : 调用接口的参数
	* save : 保存。设置了这个属性，页面将会有保存按钮。
		* url : 保存接口地址
		* to : 保存成功后跳转的路由
		* para : 调用保存接口除了表单数据额外传的参数。

##自定义指令
####价格日历
	  

可以针对价格日历设置样式，包括宽度。

data的数据模式。

	$scope.data = [
		{'d' : '20170303', 'market_price' : '132', 'count' : '80'},
		{'d' : '20170305', 'market_price' : '23', 'count' : '100'},
		{'d' : '20170308', 'market_price' : '42', 'count' : '32'},
	];
* d : 日期（必传）。yyyymmdd
* 其他属性

属性显示顺序

	$scope.showattrarr = [
		{
			'key' : 'market_price',
			'position' : 'right',
			'before' : '¥'
		},
		{
			'key' : 'count',
			'position' : 'left',
			'before' : '库存',
			'after' : '个',
		}
	];

* key : data中的属性名
* position : 位置。(left/center/right)
* before : 在值前面添加的信息。
* after : 在值后面添加的信息。

点击事件

clickday :  点击方法，参数是点击日期的信息。

参数：

	{
		'd' : '20170303',
		'data' : 数据对象,
		'label' : 显示的日期,
		'labelarr' : 实际显示的信息
	}


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)