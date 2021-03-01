#Exam 考试系统
在大三上期完成的期末实训。一个简单在在线考试系统。分为管理出题和考试界面考试。
***
#鸣谢
***
我们团队开发所有人员。
#内置功能
***
- 后台
1. 试卷管理（增、删、改、查）
2. 题库管理（增、删、改、查）
3. 成绩查看(查)
4. 用户查看(查)
- 前台
1. 选择试题
2. 考试界面（考试完出成绩,考试完查看答案）。
3. 查看成绩
#技术选择
***
- 后端
1. Spring
2. Spring MVC
3. MyBatis
4. 阿里云 Druid 数据库连接池
5. FreeMarker 模板引擎
6. pagehelper分页插件
- 前端
1. Bootstrap
2. jQuery
3. Vue.js
4. Datatables
***
#界面展示
- 后台管理
1. 主页界面
![输入图片说明](http://git.oschina.net/uploads/images/2016/1231/012729_ce5e1523_734677.png "在这里输入图片标题")
2. 登陆界面    **使用了验证码**
![输入图片说明](http://git.oschina.net/uploads/images/2016/1231/012810_145864c7_734677.png "在这里输入图片标题")
3. 后台主页界面
![输入图片说明](http://git.oschina.net/uploads/images/2016/1231/013106_aad5384d_734677.png "在这里输入图片标题")
4. 试卷管理（增、删、改、查）    **使用 VUE 进行数据绑定 后台使用 pagehelper分页 **
![输入图片说明](http://git.oschina.net/uploads/images/2016/1231/013316_0049a203_734677.png "在这里输入图片标题")
5. 题库管理（增、删、改、查）    **使用 Datatables 进行前端分页 查询 排序**
![输入图片说明](http://git.oschina.net/uploads/images/2016/1231/013349_00b0a5b0_734677.png "在这里输入图片标题")
6. 成绩查看    **使用 Datatables 进行前端分页 查询 排序**
![输入图片说明](http://git.oschina.net/uploads/images/2016/1231/013516_389c4aa1_734677.png "在这里输入图片标题")
7. 用户查看    **使用 Datatables 进行前端分页 查询 排序**
![输入图片说明](http://git.oschina.net/uploads/images/2016/1231/013630_fd122202_734677.png "在这里输入图片标题")
- 考试界面
1. 选择试卷
![输入图片说明](http://git.oschina.net/uploads/images/2016/1231/013729_c23c8768_734677.png "在这里输入图片标题")
2. 试卷考试  **后台使用了一个Spring 的定时调度任务来控制考试时间每 60秒执行一次**
![输入图片说明](http://git.oschina.net/uploads/images/2016/1231/013752_28c6d815_734677.png "在这里输入图片标题")
3. 提交试卷返回成绩
![输入图片说明](http://git.oschina.net/uploads/images/2016/1231/013824_da32057f_734677.png "在这里输入图片标题")
4. 查看答案
![输入图片说明](http://git.oschina.net/uploads/images/2016/1231/013853_fdbee1be_734677.png "在这里输入图片标题")
5. 已考试界面
![输入图片说明](http://git.oschina.net/uploads/images/2016/1231/013921_53806a94_734677.png "在这里输入图片标题")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)