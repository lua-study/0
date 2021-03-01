 :boom: [IOT DC3](https://gitee.com/pnoker/iot-dc3) Web UI, 项目已正式迁移到 Gitee 上，gitee clone url ： https://gitee.com/pnoker/dc3-web.git

 :seedling: 你的点赞是我们开发的动力！

 
      
       
	   	
	  DC3是基于Spring Cloud的开源可分布式物联网(IOT)平台,用于快速开发、部署物联设备接入项目,是一整套物联系统解决方案。 IOT DC3 is an open source, distributed Internet of Things (IOT) platform based on Spring Cloud. It is used for rapid development of IOT projects and management of IOT devices. It is a set of solutions for IOT system. 
 

------

![](./dc3/images/web-all.png)

### Run & Build 

```bash
git clone https://gitee.com/pnoker/dc3-web.git
cd dc3-web

#这步至关重要，请务必使用 cnpm 进行 install
npm install -g cnpm --registry=https://registry.npm.taobao.org
cnpm install

# run
npm run serve

# build 
npm run build

# docker build
cd dc3
docker-compose build

# docker run 
docker-compose up -d
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)