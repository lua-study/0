# 华悦假日酒店

## 使用说明

- **项目必须部署在服务器根路径下，不可添加项目名**
  tips:127.0.0.1:8080/desk/welcome

前台入口：127.0.0.1:8080/desk/welcome
后台入口：127.0.0.1:8080/background/views/user/login.html

后台常用账户：
    超级管理员：
        账号：15937124805
        密码：123123
    后勤部经理：
        账号：15638012025
        密码：123456
    进货员：
        账号：15139691465
        密码：123456
    清洁工：
        账号：17735553666
        密码：123123

- **还有很多角色/员工可用，可自行进入员工管理进行查询**    
   动态权限可用，可自行添加/编辑角色
- **角色权限设置建议使用火狐浏览器74.0 版本及以上，谷歌浏览器不支持**
- **项目中核心业务使用定时器，若项目停止运行后建议初始化数据库后再进行使用**
- 图片若存在丢失请自行到相应位置进行上传
- 项目代码托管在gitee上，传送门：https://gitee.com/HuaYueHotel/huayuehotel.git

## 初始化数据库

需要清空的数据表：

1. alipay 清空
2. housekeep_order_details
3. housekeep_order
4. room_predict_order_details
5. room_predict_order
6. room_deposit
7. room_real_order_details
8. room_real_order
9. room_status 所有status_id改为1  ，quit改为0，customer_id、in_time、out_time改为null
10. temp_order

## 配置环境

`Maven 3.3.9`

`Java 1.8`

`Mysql 5.6.46`


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)