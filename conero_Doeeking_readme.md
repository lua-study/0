》》》》》购物模块
1.表 str_order 的status（状态） 00-购物车（等待付款），01-付款成功，10-买家确认订单，11-交易成功，LK-加入收藏库
个人商场身份：BR个人用户（买家），SR商城用户（买家）
sys_site表table_id 用于连接对应表的ID标识，达到为表（个别用户）附加字段的目的。

》》》》》数据库--20151003
PHP PDO 无法连接Oracle数据
所以换用Mysql数据库---由于两个数据库的区别。暂时停止这个计划



建立 
151013	管理账户：administrator[admin0123]

服务打开类型=〉CL 关闭,OP 开启
运行与否，2长度	YP允许， NP禁止
性别 M	F (男-女)
ajax数据返回	00 否，11 是
 151013	管理账户：admin[Hyang009]
	系统：sys[Joshua1992]
	本人用户：EllisConero[Ron&Brximl]



模块缩写名：Doeeking(dkn)、Clan(clan)、Conero(cnro)、Store(stor)、Tecener(tcr)

2015/10/28
--系统设置：
不采用Model，而是利用控制性写对应的模式


2015/11/8
财务系统
	数据统计、检索、分析、建议、提醒

2015/11/9
创建视图语法
1）查询指定数据库表
CREATE OR REPLACE view sysTable AS SELECT TABLE_NAME FROM INFORMATION_SCHEMA.TABLES WHERE TABLE_SCHEMA ="cro";
删除视图 DROP VIEW sysTable；
2）查询指定数据库视图
select * from information_schema.tables where table_schema="cro" and table_type="view";

2015/11/15
自昨天开始系统出现问题，进入【财务系统】后，会出现无限的等待时间（正在连接）。
-我觉得应该是代码逻辑问题出现问题

重新部署网站，将菜单导航栏的5各模块分别在Application文件下建立对应的模块名称。将对网站整体进行建设

2015/11/23
刷新卡死解决方法：在function.php头加上session_start();session_commit();即可
注意代码的效率问题，会写代码的人狠多，但出高效率的代码的人却很少。
？然而火狐浏览器依然出现这样的问题？
？？？测试依然有问题？


ajax->仅仅返回数据，html-PHP代码分离（原则）
ThinkPHP：【师长】☆風過無痕☆ 2015/11/23 23:33:14
关联视图 和关联模型也很方便强大
ajax返回仅仅数据(像API)

小兵】小白：我在写CRM+OA项目

2015/11/24
改写ajax返回数据格式

2015/12/2
Excel数据导出：功能清单--下载前预览（可修改/用户定制下载），可选pdf，excel文件等；预览修改如以外币计价下载（$等，利用API获取汇率），更灵活的设置。

2015/12/8
数据带入方式：csv和table,下载网站给定的固定格式
		文件名格式："表明.说明.后缀",finc_set.模板V151507.scv
2015/12/10
放弃数据导入（CSV/Excel），可能影响系统信息，如无法控制用户的恶意输入

2015/12/13
	php生成调试sql语句：echo  M()->getLastSql(); 

2015/12/17
[数据库]	finc_account  （财务登记）
id,center_id,flex_amt,mark_amt,futr_amt,nearest_dt

新增：
	no	编号（年:2015。季：20150001/一季度，20150002二季度。月：201512。）
		----系统计算数据
	

	type	类型：11,10,00（年，季度，月）
	createTm	创建时间
	flex_amt	可支配金额
	
		----用户主观编辑
	countBegin	计算开始时间
	countEnd	计算截止时间（用于系统自己计算-，不填则默认）
	grade		评分（百分之）
	evaluate	评价
	remark		备注


	*custom		习惯（添加用户-依次为据算对照依据）	-- 可以加载 （系统常量里面）

修改	fins_set 表（购物清单：清单--json格式文本	{n:{name:money,单价:'',合计:''},}）
	
151218:
     finc_account(财务账单)
acc_no,cur_figure,incount, outcount, max,listnum,innum, outnum,score,remark,from_date,to_date,editm
max=json{"收入":"inmax ","支出":"outmax"}；count =json {"listnum":"账单条数","innum":"x"}
字段表采用json类型数据，针对键值与值都不固定，但格式规定。对于键值固定的直接使用数据库值。

     finc_budget (财务预算)
bud_no,figure, infigure,listnum,innum,outnum, outfigure, remark, createtm
     finc_plan(财务计划～预算实现)
finc_no,bud_no,type,edittm

json(非固定型数据表):
json_no,lock_id, app_table, json_data, jd_name, plus_data,pd_name, remark,editor,edittm

算法:计划的外键——预算（2015-12-00,2015-00-01,2015-00-00）
:49+14+25（）+110（）
逻辑关系: 计划以预算为依据（数据库上不做严格限制，以编制提醒的方式实现），预算分为年预算以及极度预算和月预算，预算包括收入和支出，预算对财务总结结果进行比较分析。

2015-12-21
[数据库操作]
powder design：导入sql语句模型-》文件/Reverse Enginner/Database
数据导出sql：数据库/generate Database/			参考URL（http://www.dedecms.com/knowledge/data-base/mysql/2012/0819/7325.html）

	(151224)
新建数据库：
	sys_site(网站系统数据库)
sys_id,name,company,url,logo,type,app_type,app_class,purpose,safe_calss,safe_key,is_login,uername,passw,bindE_m,e_mail_id,bindCell,remark,related_id,logintm,edittm,json_no,user_no
名称，公司全称，网址，login/url，类型，应用分类，应用类别，用途，安全级别，安全钥匙，是否注册，注册昵称，密码，绑定邮箱，邮箱id，备注，同表关联id，注册时间，编辑时间,附加数据,用户
type:基础账号(00)，select/input:text可选，自己加载自己


??未完成
用户注册时插入：finc_organ 第一条数据

2016/1/1
系统常量：选择控制，直接输入（常量描述-可以减少查询时的连接）

[2016/1/3]测试用户
	person[000000]	,family[000000]  =>个人用户和家庭用户

2016/1/6
sys_organs 表 ：去掉 safe_key(加密钥匙)-而所有密码使用-》名称为空公钥
：网页邮箱
：财务系统=》财务报表

2016/1/8
？？ 愚蠢的做法：利用js程序分别获取表单值，而不是使用form序列化或者整个表单的值。修正：js代码判断在用form序列化为object
=》加密
Hash 加密
mcrypt

密码可采用：crypt() => 安全性高

2016/2/22
m_infos 表
m_state	=》00 已发送，10 已读，20 回收箱。机制:不可删除已发送的信息、可删除已接受的信息（单表），单表矛盾 一方删除两发数据，删除机制矛盾。  可将单表变为双表：接受表信息，发送表信息,握手机制。

2016/2/27
增加-数据库表对应
强化日志系统：日志计划事件，
自系统功能。
--功能类型：新增，修改，模块
--页面采用模板

清空文件

2016/3/27
文档记录表 sys_bak   用于保存系统产生的文本。


2016/4/1
安全沙箱法js，页面内单独使用对象，对象方法等。便于维护

2016/4/4
？？ 首页采用网站地图导航，采用图片分区域连接
？？ 
2016/4/7
	数据修改采用相同的表单，后台做不同判断，类似公司框架
2016/4/10
	?? edge 登陆时出现卡的情况，引起站点卡
2016/4/11
js技术：闭包, 匿名函数

2016/4/19？ 计划 ~~ 财务登账？ 增加“时间备忘”机制
2016/5/14 星期六?
	数据库扩展
		财务机构：  添加“事务甲乙方标识”，扩展为财务登账时甲乙方可选
		set_mk varchar(2);  M 事务甲方,S 事务乙方,N 暂时未分[默认]
	功能新增
		数据性统计图形化
		以及机构间的内部数据流动情况(甲方)
2016/5/15 星期日
	代码编写的时候，注意尽量使用127.0.0.1，这样的测试效果就没有缓存干扰，(路径器实际编写的代码)
	echart3实列
		var myChart = echarts.init(document.getElementById(cid));
			var option = {
				 title: {
					text: '搜索财务分析图表',
					subtext: H.time()
				},
				toolbox:{							//工具箱
						show:true,
						orient:'horizontal',
						feature:{
							saveAsImage:{
								type:'png',
								name:'财务登账分析'+H.time(),
								show:true,
								title:'保存为图像'
							},
							magicType:{
								show:true,
								type:['line','bar'],
								title:'切换'
							}
						}
				},
				tooltip:{
					trigger: 'axis',
					axisPointer : {            // 坐标轴指示器，坐标轴触发有效
						type : 'shadow'        // 默认为直线，可选为：'line' | 'shadow'
					}
				},
				legend: {
					data:['柱形图', '折线图']
				},
				grid: {
					left: '3%',
					right: '4%',
					bottom: '3%',
					containLabel: true
				},
				xAxis : [
					{
						type:'category',
						data:xVal
					}
				],
				yAxis:[
					{
						type:'value'
					}
				],
				series:[
					{
						'name':'折线图',
						'type':'line',
						'data':yVal,
						markPoint : {
							data : [
								{type : 'max', name: '最大值'},
								{type : 'min', name: '最小值'}
							]
						},
						markLine : {
							data : [
								{type : 'average', name : '平均值'}
							]
						}
					},
					{
						'name':'柱形图',
						'type':'bar',
						'data':yVal,
						markPoint : {
							data : [
								{type : 'max', name: '最大值'},
								{type : 'min', name: '最小值'}
							]
						},
						markLine : {
							data : [
								{type : 'average', name : '平均值'}
							]
						}
					}
				]
			};
			H.log(option);
			myChart.setOption(option); 
		});
	日志：
		项目概率：
			bug1		无法获取PHP所传回的code值，造成系统无法登记日志
			bug2		节点转换"" 失效，无法获取到数据
		财务机构：数据化图像分析处理
		尽量将系统放到： git上。以及减少系统对决定根目录的依赖
2016/5/22 星期日[哈市]
	sys_textTpl mechanism	table.id 文件模板生成机制
	use_tpl(code,id) => js/php  code sys_textTpl 代码，id 数据id
## 2016年8月15日 星期一
	等帐频率统计：  
		SELECT DATE_FORMAT(set_date,'%Y-%m-%d') FROM `finc_set` order by `set_date` desc;
		SELECT DATE_FORMAT(set_date,'%Y-%m-%d') as date,count(DATE_FORMAT(set_date,'%Y-%m-%d')) as count FROM `finc_set` group by DATE_FORMAT(set_date,'%Y-%m-%d') order by `set_date` desc; 
	//## 2016年8月18日 星期四
		select min(DATE_FORMAT(use_date,'%Y')) as "minyear" from finc_set where use_date not like '0000%' and center_id="963106BpbP";

##	2016年8月19日 星期五
	财务登账按照：类型统计
		select plus_value as utype,count(plus_value) as ctt from `finc_setview` group by plus_value;	
## 2016年8月31日 星期三
	1.模块分类
	SELECT * FROM `sys_site` WHERE `group`="sys_module" and `user_name`="CONST" order by `gover_name`	
##	2016年9月1日 星期四
	1.sys_site 主键加长  20160901214201/14.rand(100000,999999)/6=20
	ALTER TABLE `sys_site` CHANGE `sys_id` `sys_id` VARCHAR(20) CHARACTER SET utf8 COLLATE utf8_bin NOT NULL;
##	2016年9月2日 星期五
	1.	/Doeeking/index.php/Conero/Admin.html		BUG> $this->ajaxReturn($data), $.post()无法再获取到数据数据，异步回调无效
		>>原因未明  暂时用die(string)代替

##	2016年9月4日 星期日	
	1.thinkphp $_GET['m'] 午安分获取到，而$_GER['sajsa']却可以		
##	2016年9月6日 星期二
	1. 新建财务财务走势图
		按使用日期统计:  金额总数，数据条数
			select count(a.figure) as nums,sum(a.figure) as amont,a.use_date,
			(select ifnull(sum(b.figure),0) from finc_set b where b.type="IN" and b.use_date=a.use_date) as incount
			from finc_set a group by a.use_date	

##	2016年9月7日 星期三
	1. 项目中本地计算机转移到公司计算机(-), 由于本地计算机出现烦人的粘滞键，关闭后却依然存在。由此注意准备重装本机的系统，也许换位原装的 Ubuntu(Linux)系统
	通知注意系统的数据导入/到处模块，也许设计一种加密方式，保护到处的数据			
		以上情况导致系统的进展缓慢
		1) 系统的数据导入/到处模块
		2) 系统数据日志记录
##	2016年9月9日 星期五
    1.财务走势图(根据登账记录) ~ 见 log.sql
    >> substr(col,start.length) 列名,起始位置（1开始），长度
        a. 统计年份
            select substr(use_date,1,4) as `year` from finc_set where use_date not like "0000-%" group by substr(use_date,1,4);
        b. 统计月总数
            select count(a.figure) as nums,sum(a.figure) as amont,a.use_date,
            (select ifnull(sum(b.figure),0) from finc_set b where b.type="IN" and b.use_date=a.use_date) as incount
            from finc_set a where a.use_date like "2016-%" group by group by a.use_date
    2.span,label 设置 width无效,需要设置css display:block/inline-block;       
## 2016年9月12日 星期一
	1.财务登账流水线计算法

## 2016年9月19日 星期一
	tp5 重写URL无效

		 
			Options +FollowSymlinks -Multiviews
			RewriteEngine On

			RewriteCond %{REQUEST_FILENAME} !-d
			RewriteCond %{REQUEST_FILENAME} !-f
			-- 无效
			RewriteRule ^/TeCenter/(.*)$ /TeCenter/index.php?s=/$1 [QSA,PT,L]
			-- 无效
			RewriteRule ^/TeCenter/(.*)$ /TeCenter/index.php?/$1 [QSA,PT,L]
			-- 虚拟主机有效
			RewriteRule ^(.*)$ index.php?/$1 [QSA,PT,L]
			RewriteRule ^(.*)$ index.php?s=/$1 [QSA,PT,L]
		 
## 2016年10月30日 星期日
	1.函数与存储过程
		>> 来着都是函数的集合
		* 函数相对于存储过程更简单	

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)