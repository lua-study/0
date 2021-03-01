# 基于角色的权限控制RBAC

## 1 开发环境

### 1.1 开发工具

- PhpStorm 2016.3.3
- Sublime Text 3

### 1.2 运行环境

- Thinkphp5.0.12
- MySQL 5.5.53
- php 5.6
- apache

## 2 数据库介绍

- 用户表

```sql
CREATE TABLE `ng_admin` (
  `id` int(11) unsigned NOT NULL AUTO_INCREMENT COMMENT 'id',
  `user_name` varchar(60) NOT NULL DEFAULT '' COMMENT '用户名',
  `email` varchar(60) NOT NULL DEFAULT '' COMMENT '邮箱',
  `password` varchar(32) NOT NULL DEFAULT '' COMMENT '密码',
  `salt` varchar(10) DEFAULT NULL COMMENT '秘钥',
  `last_login_time` int(11) NOT NULL DEFAULT 0 COMMENT '最近登录时间',
  `last_login_ip` varchar(15) NOT NULL DEFAULT 0 COMMENT '最近登录IP',
  `role_id` int(11) DEFAULT '0' COMMENT '角色id',
  `create_time` int(11) unsigned DEFAULT NULL COMMENT '创建时间',
  `update_time` int(11) unsigned DEFAULT NULL COMMENT '更新时间',
  `delete_time` int(11) unsigned DEFAULT NULL COMMENT '删除时间',
  PRIMARY KEY (`id`),
  KEY `user_name` (`user_name`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

- 角色

```sql
CREATE TABLE `ng_role` (
  `id` smallint(6) unsigned NOT NULL AUTO_INCREMENT COMMENT '角色ID',
  `role_name` varchar(30) DEFAULT NULL COMMENT '角色名称',
  `act_list` text COMMENT '权限列表',
  `role_desc` varchar(255) DEFAULT NULL COMMENT '角色描述',
  `create_time` int(11) unsigned DEFAULT NULL COMMENT '创建时间',
  `update_time` int(11) unsigned DEFAULT NULL COMMENT '更新时间',
  `delete_time` int(11) unsigned DEFAULT NULL COMMENT '删除时间',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

- 菜单

```sql
CREATE TABLE `ng_system_menu` (
  `id` int(11) unsigned NOT NULL AUTO_INCREMENT COMMENT 'ID',
  `name` varchar(50) DEFAULT NULL COMMENT '权限名称',
  `group` varchar(20) DEFAULT NULL COMMENT '所属分组',
  `right` text COMMENT '权限码(控制器+动作)',
  `create_time` int(11) unsigned DEFAULT NULL COMMENT '创建时间',
  `update_time` int(11) unsigned DEFAULT NULL COMMENT '更新时间',
  `delete_time` int(11) unsigned DEFAULT NULL COMMENT '删除时间',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

- 管理员日志

```sql
CREATE TABLE `ng_admin_log` (
  `id` bigint(16) unsigned NOT NULL AUTO_INCREMENT,
  `admin_id` int(11) DEFAULT NULL,
  `log_info` varchar(255) DEFAULT NULL,
  `log_ip` varchar(30) DEFAULT NULL,
  `log_url` varchar(255) DEFAULT NULL,
  `log_type` tinyint(2) DEFAULT '0' COMMENT '0默认1操作店铺2审核活动3处理投诉4其他',
  `create_time` int(11) unsigned DEFAULT NULL COMMENT '创建时间',
  `update_time` int(11) unsigned DEFAULT NULL COMMENT '更新时间',
  `delete_time` int(11) unsigned DEFAULT NULL COMMENT '删除时间',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

GRANT ALL PRIVILEGES ON `ng_auth_rbac`.* TO 'guo'@'%' IDENTIFIED BY 'sn_123456' WITH GRANT OPTION;

flush privalige;


update

201701126

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)