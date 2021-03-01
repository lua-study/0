 

#  Archery 

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/94e8587e507f4565a1ea5ea21fd94c32)](https://app.codacy.com/app/hhyo/Archery?utm_source=github.com&utm_medium=referral&utm_content=hhyo/Archery&utm_campaign=Badge_Grade_Dashboard)
[![Build Status](https://travis-ci.org/hhyo/Archery.svg?branch=master)](https://travis-ci.org/hhyo/Archery)
[![Release](https://img.shields.io/github/release/hhyo/archery.svg)](https://gitee.com/rtttte/Archery/releases)
[![codecov](https://codecov.io/gh/hhyo/archery/branch/master/graph/badge.svg)](https://codecov.io/gh/hhyo/archery)
[![version](https://img.shields.io/badge/python-3.6.5-blue.svg)](https://www.python.org/downloads/release/python-365/)
[![version](https://img.shields.io/badge/django-2.2-brightgreen.svg)](https://docs.djangoproject.com/zh-hans/2.2/)
[![docker_pulls](https://img.shields.io/docker/pulls/hhyo/archery.svg)](https://hub.docker.com/r/hhyo/archery/)
[![HitCount](http://hits.dwyl.io/hhyo/hhyo/Archery.svg)](http://hits.dwyl.io/hhyo/hhyo/Archery)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://gitee.com/rtttte/Archery/blob/master/LICENSE)
[![996.icu](https://img.shields.io/badge/link-996.icu-red.svg)](https://996.icu)

[文档](https://archerydms.com/) | [FAQ](https://archerydms.com/FAQ/) | [Releases](https://gitee.com/rtttte/Archery/releases)

![](https://images.gitee.com/uploads/images/2019/1110/202317_32bd4a1c_1038040.png)

 


介绍
============
Archery定位于SQL审核查询平台，旨在提升DBA的工作效率，支持主流数据库的SQL上线和查询，同时支持丰富的MySQL运维功能，所有功能都兼容手机端操作

功能清单
====

|  | 查询 | 审核 | 执行 | 备份 | 数据字典 | 慢日志 | 会话管理 | 账号管理 | 参数管理 | 数据归档 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| MySQL | √ | √ | √ | √ | √ | √ | √ | √ | √ | √ |
| MsSQL | √ | × | √ | × | × | × | × | × | × | × |
| Redis | √ | × | √ | × | × | × | × | × | × | × |
| PgSQL | √ | × | √ | × | × | × | × | × | × | × |
| Oracle | √ | × | √ | × | × | × | × | × | × | × |
| MongoDB | √ | × | × | × | × | × | × | × | × | × |

  

快速开始
===============
### 系统体验
[在线体验](https://demo.archerydms.com)
  
| 账号 | 密码 |
| --- | --- |
| archer | archer |

### Docker
#### 准备运行配置
具体可参考：https://gitee.com/rtttte/Archery/blob/master/src/docker-compose

#### 启动
下载 [Releases](https://gitee.com/rtttte/Archery/releases)文件，解压后进入docker-compose文件夹

```bash
#启动
docker-compose -f docker-compose.yml up -d

#表结构初始化
docker exec -ti archery /bin/bash
cd /opt/archery
source /opt/venv4archery/bin/activate
python3 manage.py makemigrations sql  
python3 manage.py migrate

#数据初始化
python3 manage.py dbshell<sql/fixtures/auth_group.sql
python3 manage.py dbshell<src/init_sql/mysql_slow_query_review.sql

#创建管理用户
python3 manage.py createsuperuser

#重启服务
docker restart archery

#日志查看和问题排查
docker logs archery -f --tail=10
logs/archery.log
```

#### 访问
http://127.0.0.1:9123/

手动安装
===============
[部署说明](https://archerydms.com/installation/manual/)

运行测试
===============
```
python manage.py test -v 3
```

贡献者
===============
![](https://sourcerer.io/fame/hhyo/hhyo/archery/images/0)![](https://sourcerer.io/fame/hhyo/hhyo/archery/images/1)![](https://sourcerer.io/fame/hhyo/hhyo/archery/images/2)![](https://sourcerer.io/fame/hhyo/hhyo/archery/images/3)![](https://sourcerer.io/fame/hhyo/hhyo/archery/images/4)![](https://sourcerer.io/fame/hhyo/hhyo/archery/images/5)![](https://sourcerer.io/fame/hhyo/hhyo/archery/images/6)![](https://sourcerer.io/fame/hhyo/hhyo/archery/images/7)

贡献代码
===============
可查阅主页的开发计划以及依赖清单，在对应issues中回复认领，或者直接提交PR，感谢你对Archery的贡献  
贡献包括但不限于以下方式：
- Wiki文档（开放编辑）
- Bug修复
- 新功能提交
- 代码优化
- 测试用例完善

问题反馈
===============
项目没有交流群，如果在使用过程中遇到问题，请先查阅文档，如果仍无法解决，请查看相关日志，保存截图信息，提交Issue，感谢你对Archery的贡献


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)