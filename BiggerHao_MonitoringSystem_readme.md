

# Multi-Channel Monitoring Management Website

This is the website that I built for my undergraduate thesis. It aims to provide a simple interface to the administrators of a multi-channel monitoring system to easily manage the collected data.

## Database Connection
* Modify the `username` and `password` in `src/applicationContext.xml`
* Modify the `user` and `pwd` in `src/com/monitor/util/MysqlDBConnector.java`
* See [MonitoringSystemDesign](http://git.oschina.net/BiggerHao/MonitoringSystemDesign) (This repository is not publicly available now due to some confidential data) for the documentation of the database design. Execute `Dump.sql` in MySQLWorkbench to create the database and tables. Please ensure that this is done before the program is run.

## Frequently Asked Questions

- [Host 'xxx.xx.xxx.xxx' is not allowed to connect to this MySQL server](http://stackoverflow.com/questions/1559955/host-xxx-xx-xxx-xxx-is-not-allowed-to-connect-to-this-mysql-server)

```sql
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost' WITH GRANT OPTION;
CREATE USER 'username'@'%' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON *.* TO 'username'@'%' WITH GRANT OPTION;
```

## Screenshots

Note that some parts are blurred due to privacy concerns.

![](screenshots/ui-latest-appearances.png)

![](screenshots/ui-black-and-white-management.png)

![](screenshots/ui-person-detail.png)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)