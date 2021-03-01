# hchart_springboot

#### 项目介绍
highchart插件  

#### 软件架构
springboot

#### 使用说明

- 1、数据库配置：\webapps\springboot\WEB-INF\classes\application.yml 
- 2、可绘制项：sql查询结果中的第一列为项名，第二列为数量 
- 3、填写查询设置信息后点击保存按钮进入统计绘制页面，点击开始查询按钮即可开始绘制 
- 4、除查询时间间隔外其余参数均存储于缓存中，如当天不需要调整sql可直接访问show.html 
- 5、刷新页面可清空当前统计图形，返回上级页面可通过浏览器回退操作
##### SQL示例：
> ①A表中m字段值实时变化，需统计m字段各值实时数据量 
select deal_state,count(*) from se_batch where bat_no like 'EGTEST%' group by deal_state  
②B表中总数一直在变化，需要统计B表数量实时值，以SUM命名总数变化曲线 
select 'batch',count(*) from se_batch where bat_no like 'EGTEST%'  
③C、D表总数一直在变化，需同时统计两张表的实时数据库 
select 'batch',count(*) from se_batch where bat_no like 'EGTEST%' union all select 'bd',count(*) from se_bd where bat_no like 'EGTEST%'

#### 测试数据
```
SQL:
select t.DEAL_STATE,count(bat_no) from se_batch  t 
where ENT_NUM ='AS330106' and bat_no like 'EGTEST1127%' 
group by deal_state order by deal_state

状态:
A00,B00,F00,G00,E01,S08,T00,T06,Z00,Z01
```
#### 参与贡献

1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request

#### 联系作者
785041502@qq.com
Clove丶
     
#### 说明文档
https://mp.weixin.qq.com/s/-J9aUcCLW6tUlK7zHsf0bQ 
https://mp.weixin.qq.com/s/F_v22lhPd-z2TDMUABmi9Q

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)