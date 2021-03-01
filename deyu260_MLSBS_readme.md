#[MLSBS](http://git.oschina.net/MickeyZZC/MLSBS "MLSBS")
---
###[MLSBS](http://git.oschina.net/MickeyZZC/MLSBS "MLSBS") is the abbreviation of "My linux's bash script"!
**[MLSBS](http://git.oschina.net/MickeyZZC/MLSBS "MLSBS")** 是“My linux's bash script”的缩写 。（经过在Centos6.5 和Ubuntu12.04下测试通过。）  

---
**运行方式：**  
下载项目后，进入项目根目录  
 >  # chmod +x ./myscript.sh  
 >  # ./myscript.sh  

运行前请根据自身系统情况更改配置文件config , 脚本统一使用utf-8编码。  

---
* **版本信息**：   
> [\MLSBS\doc\VERSION.md](http://git.oschina.net/MickeyZZC/MLSBS/blob/master/doc/VERSION.md)

* **项目帮助**：   
> [\MLSBS\doc\HELP.md](http://git.oschina.net/MickeyZZC/MLSBS/blob/master/doc/HELP.md)

* **二次开发教程**：   
> [\MLSBS\doc\DEV.md](http://git.oschina.net/MickeyZZC/MLSBS/blob/master/doc/DEV.md)  

---
##功能项:
* **系统设置**：  
	* **一键优化**；   
	（待完善）
	* **增加用户**；   
	可选择增加普通用户或管理员。
	* **时区设置**；  
	默认上海时区。
	* **生成任务**；   
	目前只有防SSH暴力破解脚本任务
	* **防火墙设置**。   
	交互式设置
* **系统报告**：
	* **生成系统配置简报**；   
	包括CPU架构，指令，物理内存和虚拟内存，分区大小和INODE总数，各个网卡的IPV4和IPV6地址等信息
	* **实时输出系统负载（CPU,内存，硬盘IO）**   
	CPU的1分钟，5分钟，15分钟的负载率，内存的使用率，硬盘IO等信息，每10秒取值一次。
	* **实时输出网络负载（除lo以往的所有网口流量IO）**   
	各个网卡的实时流量，每10秒取值一次。
* **软件安装**：  
	* NGINX编译安装；   
	* TOMCAT最新版下载解压绿色安装；
	* MYSQL编译安装；
	* PUPPET简易安装。
* **工具生成**：  
	* **python版本发邮件小工具**   
	支持管道，邮件密码加密，附件发送等功能。   

---

**目录结构：**

mlsbs/  
├── bashScript #独立使用的bash脚本    
├── Template #Bash脚本模板  
├── function #功能函数  
│	 /  ├─ install #软件安装函数  
│    /  └─ system  #系统设置函数  
│  
├── doc #版本说明和功能介绍  
└── mylib #公共库



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)