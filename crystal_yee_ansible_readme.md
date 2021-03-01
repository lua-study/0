#使用说明

###ansible环境配置
######1.配置ansible客户端需要和ansible服务器建立ssh免密钥通信
######2.ansible的/etc/ansible/hosts文件中添加客户端纳入管理
######3.配置完成之后示例:
  
[root@tiaoban ~]# ansible 192.168.1.32 -m command -a "hostname"
192.168.1.32 | success | rc=0 >>
ansible-centos
  
######如果这里返回内容中包含success，则说明主机可以被ansible管理

###ansible帮助文档
######[ansible官方帮助文档]（http://docs.ansible.com/ansible/intro.html）
######[ansible中文帮助文档]（http://www.ansible.com.cn）


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)