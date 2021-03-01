# AnjukeSpider
### 简介
爬去安居客房源，筛选房源，微信提醒

### 环境搭建

1. 安装**python2.7**、**pip**、**setuptools**    
2. 安装requests   
```shell
pip2.7 install request
```

### 使用

#### 安居客相关
1. 访问安居客网站，选择城市和小区后，复制当前网址，替换**AnjukeUrl**后面的网址   
2. **SizeRange**为面积区间，既筛选**面积<SizeRange**的房源   
3. **PriceRange**为总价区间，既筛选**总价<=PriceRange**的房源     
4. **UnitPriceRange**为单间区间，既筛选**单价<=UnitPriceRange**的房源    
5. **NumEnd**为页码区间**1-NumEnd**   
6. **SizeRange**、**PriceRange**、**UnitPriceRange**、**NumEnd**值必须为**数字**     
   
#### 微信企业号相关   
1. [点击创建微信企业号](https://qy.weixin.qq.com/),并获取**CorpID**与**Secret**   
2. 在通讯录中创建**标签**，并记录标签ID，添加到**Totag**     
3. 创建**app**，并记录应用ID，添加到**AgentID**    
    
### 未完善  
1. 未对接redis，因此循环执行脚本时，房源会重复提醒  
2. 未使用代理模式，因此ip存在被封的可能，因此每次获取房源后会sleep 3秒  


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)