
# 健康助手

学生健康报备、员工防疫筛查、个人健康打卡、社区管理、政府汇总等

## 介绍

这是健康助手的说明文档，适用于任何的团体，如班级、部门、学校、公司、地区政府等，自由创建，自助建立从属关系，对学生、员工、个人进行健康登记、防疫排查等功能。

- 可以先建立班级，进行统计，之后再建立学校，进行汇总；
- 可以直接创建公司，再创建所属部门，人员分部门管理；
- 可以只创建部门，汇总之后再上报公司；
- 地方政府也可以创建团体，汇总各部门、所管辖地区企业的信息；
- 社区使用，按楼建立团体（如19栋），再做成社区。

创建好团体之后，开放成员注册，即可以自助录入部门员工信息、班级学生信息、楼层住户信息等，之后可以关闭成员注册，减少管理员的工作量。
管理员也可以录入成员，修改、删除成员。
在填写报备时，输入的个人信息可以和之前注册的信息对比，非团体成员不能提交报备。

项目来源于DCloud的“学生健康报备管理系统”项目，重新设计数据表、页面、云函数，便于扩展和迭代开发。

抗击肺炎，中国加油！

## 截图

 
  
 

 
  
 

## 软件架构

### 网页形式（一期实现）

 登录 

> 页面名称：user_login 
> 数据表：ha_user_account 
> 云函数：ha_check_account 
> END

 注册 

> 页面名称：user_register 
> 数据表：ha_user_account 
> 云函数：ha_add_account 
> END

 首页 

> 页面名称：index 
> 数据表：多个数据表 
> 云函数： 
>> 链接： 个人设置 
>
>> 分栏：我的团体
>>> 我管理的团体列表： 团体详情  
>>> 链接： 创建团体 
>
>> 链接： 我的模板 
>
> END

 个人设置 

> 页面名称：user_setting 
> 数据表：ha_user_account 
> 云函数：ha_update_account 
> 修改密码、手机号、Email等功能，为后期找回密码服务
>
> END

 创建团体 

> 页面名称：create_group 
> 数据表：ha_group_list 
> 云函数：ha_add_group 
> 参见ha_group_list
>
> END

 团体详情 

> 页面名称：group_detail 
> 数据表：ha_group_list、ha_report_list 
> 云函数：ha_get_group、ha_update_report
>> 链接： 成员管理  
>> 已建报备列表： 复制链接 、 查看统计 、 开启/关闭 、删除 
>> 链接： 新建报备  
>> 团体操作： 修改 、删除 
>> 修改、删除只能由本团体所有者操作 
>>  加入申请 
>
>> 分栏：下属团体
>>> 下属团体列表： 团体详情 、 断开关系（仅对第一层下属有效）  
>>> 需要记录进入下属团体的层级信息 
>>> 是否可以点击进入下属团体，受 团体作用域 影响 
>
> END

 新建报备 

> 页面名称：create_report 
> 数据表：ha_user_template、ha_template_list、ha_report_list 
> 云函数：ha_add_report
>> 单选框，选择自有的还是公共的模板 
>> 下拉菜单选择模板，并预览 
>>
>> 根据ha_group_person的人员信息，选择报备首页的验证信息 
>> 如勾选名字和身份证号，则在点开报备链接时，首先要输入名字和身份证，确认正确后，进行实际报备的填写 
>>
>> 选择是否激活，以及报备间隔时间，参见ha_report_list 
>>
>> 同时新建下属团体的报备，参见 作用域 。 
>
> END

 查看统计 

> 页面名称：report_detail 
> 数据表：ha_report_list、ha_report_record 
> 云函数：
>> 多种方式显示
>> 导出成excel功能
>
> END

 成员管理 

> 页面名称：member_manage 
> 数据表：ha_group_person 
> 云函数：ha_add_member、ha_update_member
>> 人员列表： 查看 、 修改 、删除 
>> 链接： 新增成员  
>> 是否开放成员注册？ 成员注册  
 > 上传人员名单文件 
>> 下载人员名单模板，信息参见ha_group_person -->
>
> END

 新增成员 

> 页面名称：create_member 
> 数据表：ha_group_person 
> 云函数：ha_add_member
> 参见ha_group_person
>
> END

 成员注册 

> 页面名称：member_register 
> 数据表：ha_group_person 
> 云函数：ha_add_member
> 参见ha_group_person
>
> END

 填写报备 

> 页面名称：do_report 
> 数据表：ha_report_record 
> 云函数：ha_check_member、ha_add_record
>> 首先填写成员信息，检查是否是本团体的成员 
>> 再填写报备信息，最后提交
>
> END

### 网页形式（续）

 我的模板 

> 页面名称：my_template 
> 数据表：ha_user_template 
> 云函数：ha_get_my_tpl
>> 分栏：模板列表(get_way != 2) 
>> 分栏：收到的模板(get_way == 2) 
>> 每个项： 查看模板 、删除 
>>
>>  查看公共模板 
>>
>>  导入模板 按钮（json格式），选择后进入预览模板页面，如格式错要提示并终止
>
> END

 预览模板 

> 页面名称：tpl_review 
> 数据表：ha_template_list 
> 云函数：ha_get_tpl 
> 查看现有的模板，则只有返回按钮 
> 由导入按钮进行的预览，有确定导入和返回按钮
>
> END

 公共模板列表 

> 页面名称：tpl_pub_list 
> 数据表：ha_template_list 
> 云函数：ha_get_pub_tpl 
> 下拉菜单选择，下面预览 
>  收藏 按钮
>
> END

 关于有从属关系的团体说明： 

* 下属团体 作用域 ：是往下三级，第四级将不受作用
* 当前团体->第一级->第二级->第三级，往下不受作用
* 如碰到下属团体is_split==true时，则往下的团体不受作用
* 报备与团体有关，参见ha_report_list，当一个团体有下属团体时，新建报备，将在所有作用域中的团体，新建相同的报备。

 加入申请 

> 页面名称：join_group 
> 数据表：ha_group_list 
> 云函数：ha_update_group 
> 这个页面包含group的ID 
> 分享这个页面给下属团体 
> 获得已登录用户账号的团体 
> 下拉菜单选择当前用户账号的团体 
>  申请加入 
>
> END


 > 分栏：我的人员
>>> 人员列表： 人员详情  
>>> 自己的信息，小孩的信息等 
>>> 包含名字、身份证等 
>>>
>>> 链接： 添加人员 
>
>> 链接： 健康打卡 
>
>> 其他待定：如报备通知 -->

 添加人员 

> 页面名称： 
> 数据表：ha_user_person、ha_relation_user 
> 云函数： 
>
> END -->

 健康打卡 

> 页面名称： 
> 数据表： 
> 云函数： 
>
> END -->

 人员详情 

> 页面名称： 
> 数据表： 
> 云函数： 
>
> END -->

软件架构说明

- 注册登录
- 团体管理
- 健康上报
- 数据查看

### 底部导航形式（二期实现）

```
- 底部导航
  |__ 主页（home）
  |__ xxx
  |__ xxx
  |__ 个人中心（user_nest）

- 主页（home）
  |__ xxx

- 个人中心（user_nest）
  |__ xxx
```

Tips：页面可以重建，请保持名称不变

## 参与贡献

参考DCloud提出的方式，请在文件开始处填写开发者名字、所处城市、邮箱等信息

开发QQ群：965617357

开发者报名要参与开发哪些文件。具体方式如下：
    
    - 首先要参与哪个项目，就把哪个项目git先fork，然后导入本地开发环境。注意不要fork xinguan2020 这个汇总项目，要fork具体的项目。
    - 注意不要直接导入git项目，要先fork，修改自己本地的git，然后提交pr。
    - 如果不了解提pr的方法，参考[码云教程](https://gitee.com/help/articles/4128#article-header0)
    - 然后打开你要编辑的文件，在开头以注释方式编写你的信息，声明你在做这个文件。比如
    ```javascript
    // 我在做这个文件，我的群昵称是xxx。（如果是vue文件，注释要用 )
    ```
    - 然后把这个修改提交pr。意思就是你报名要修改这个文件，且公知给其他人。
    - 项目负责人会合并这个报名的pr。
    - 等你开发文件完毕后，再把这个文件再次提交pr。项目负责人会合并pr。
    - 如果你是参与项目的核心开发者，也可以把你的码云账户发到项目负责人那里，申请直接加为项目组成员，就可以直接提交而不是通过pr方式提交了。

1.  Fork 本仓库
2.  新建 Feat_xxx 分支
3.  提交代码
4.  新建 Pull Request

## 发布方式

- Saas方式，不需要另外部署，直接多用户使用
- 基于uni-app的技术支撑，多端、多形态发布，H5、小程序、app等
- 所用端口，不同形态的接口，共享数据，同一账号在用不同的方式登录都可以

### 体验链接

[健康助手](http://ha.8-ip.com)

## 数据库设计

参考 [db.md](db.md)

### 空间与小程序appID设置
- 在`main.js`中设置空间的`spaceId`、`clientSecret`；
- 在`manifest.json`中设置微信小程序的`appID`，否则微信端获取的code为：`the code is a mock one`；
- 在`cloudfunctions-dev/src/utils/constants.js`中设置`AppId`、`AppSecret`、`passSecret`字段，否则不能获取`openid`;


### token获取详情
获取用户信息需要根据token获取，方法如下，成功后，`res.data`为详细信息，`res.data.userType`为用户类型，
`userType`的值为数字，对应信息如下。

```JS
validateToken() {
				uni.showLoading({
					title: '加载中...'
				});
				uniCloud.callFunction({
					name: 'validateToken',
					data: {
						token: uni.getStorageSync('token')
					}
				}).then((res) => {
					uni.hideLoading()
					uni.showModal({
						content: res.result.msg,
						showCancel: false
					})
				}).catch((err) => {
					uni.hideLoading()
					uni.showModal({
						content: '请求云函数发生错误，' + err.message,
						showCancel: false
					})
				})
			},
```

## 码云特技

1.  使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2.  码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3.  你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4.  [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5.  码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6.  码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)

## 捐赠说明

捐赠将用于加快项目开发、优化项目，以及其他开源公益项目。
桌面版可进行捐赠。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)