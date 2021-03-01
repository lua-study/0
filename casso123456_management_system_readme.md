# 后台管理系统

#### 介绍
后台管理系统 DRF webpack py3
超管：casso casso
#### 软件架构
1.   python -m pip install --upgrade pip   #　pip 升级到pip3

2.   pip3 freeze > requirements.txt  # 收集依赖  建议每次上传代码先收集一下，以免其他成员环境缺少新增依赖

3.   pip3 install -r requirements.txt  #　报依赖缺失时运行

4.   CREATE DATABASE `bms` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;

5.   python manage.py dumpdata > bms_data.json    # 导出数据库中的数据，木有指定app即导出所有app数据

6.   python manage.py loaddata bms_data.json      # 导入现有数据, 数据库迁移文件太多会可能会迁移出错 导出 删库 重建 导入
#### 参与贡献

1.  Fork 本仓库
2.  新建 Feat_xxx 分支
3.  提交代码
4.  新建 Pull Request

### 代码提交：
  1.  由于电脑还有另外一个码云账号，可能会提示码云权限提交：
  2.  打开git bash
  3.  输入ssh-keygen -t rsa -C "你的邮箱地址" 三次回车之后就可以生成密钥对
  4.  输入cat ~/.ssh/id_rsa.pub 查看你的 public key（公钥）复制粘贴到码云即可



#### 项目定位：云办公平台

### ############### 项目模块概述 #########################

#### 一：基础模块

1.  用户管理模块 
2.  菜单管理模块
3.  日志管理模块
4.  用户组管理模块
5.  权限管理模块
6.  图像素材管理模块
7.  部门管理模块
8.  系统黑名单模块

#### 二：基本功能模块

1.  企业通讯录管理功能模块
2.  考勤管理功能模块
3.  日程安排功能模块
4.  工作汇报功能模块
5.  审批/审批流程管理功能模块
6.  外勤人员定位轨迹功能模块
7.  公告/公告系统管理功能模块
8.  企业文化宣传/培养专栏功能模块




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)