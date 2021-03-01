#saltops

# [系统开发中～请不要用于生产系统] 

#目标
SaltOps是一个基于SaltStack和Django开发的运维平台，
平台的主要功能包括：CMDB、包发布管理、工具系统、最终作为包发布和工具系统的接色
与Jenkins、Zabbix等系统进行整合

#系统会具备什么功能

* CMDB：这个也是没办法的事情，资产信息还是要的。。而且Salt的Agent非常适合采集这些基础信息
最后，包发布的过程是需要用到CMDB信息的，所以CMDB是作为附属品存在的
* 包发布：程序包发布的功能，这块主要是用到salt的state.sls，通过编写好
sls文件，然后调用salt进行发布的动作，发布完后应用与主机的信息自然就对接起来了
* 工具平台：既然都接上了Salt，把工具平台做了也是很自然的事情啦～

#为什么使用DjangoAdmin
DjangoAdmin大多作为后台管理员使用的，这里用DjangoAdmin的原因是：没资源。。且每天写的时间也有限，用它的话大多数界面都不用自己做，还是挺省事的
配合着Django-jet的话也长得还不错

#一些图片
![输入图片说明](http://git.oschina.net/uploads/images/2017/0123/103726_0f841e0b_8819.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0123/103734_49fb795f_8819.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0123/103741_6e9bca49_8819.png "在这里输入图片标题")
![输入图片说明](http://git.oschina.net/uploads/images/2017/0123/103747_1cbe3394_8819.png "在这里输入图片标题")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)