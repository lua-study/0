#agilefant项目使用说明：

##配置主机映射
/etc/hosts 增加 10.173.55.190 reg.csphere.cn
 
## 系统环境初始化

### JDK  
http://reg.csphere.cn/jenkins-ci/jdk-7u79-linux-x64.tar.gz

###MAVEN 
http://reg.csphere.cn/jenkins-ci/apache-maven-3.3.3-bin.tar.gz

https://git.oschina.net/csphere/scripts.git 仓库中的
scripts/maven/install-mvn-repository.sh

### 导入mvn repository数据
git clone https://git.oschina.net/2839543/training-agilefant.git

/data/training-agilefant/install-mvn-repository.sh


###docker
https://docs.docker.com/
###docker-compose
https://docs.docker.com/
###其它
apt-get install -y git mysql-client-core-5.6 
####jenkins 
http://reg.csphere.cn/jenkins-ci/jenkins.war
####jenkins-备份文件

##导入项目第一种方式通过
cd /data/
git clone https://github.com/Agilefant/agilefant.git


##导入项目第二种方式通过
/data/training-agilefant/get-git-agilefant.sh


#项目构建
修改配置文件
/data/agilefant-master/webapp/src/main/webapp/WEB-INF/agilefant.conf


jdbc:mysql://localhost/agilefant 改为 jdbc:mysql:// /agilefant




/data/agilefant-master/ mvn clean install -Dmaven.test.skip=true (测试非常耗费时间跳过)
构建 完成的war包在 /data/agilefant-master/webapp/target/agilefant.war




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)