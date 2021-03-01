Flasher分布式缓存框架
---

 Flasher基于Redis Cluster 3.0集群服务器（5.0版本关注公众号获取）开发的一套Java客户端
### 技术交流 关注公众号福利赠送

## Flasher特点
* 1、基于Jedis Cluster开发的客户端支持Redis Cluster集群。
* 2、对被调用方（客户端）侵入极少，上手极快。
* 3、支持动态增加节点，客户端自动感知。（zk）
* 4、支持客户端验证与拦截。 token
* 5、异步监控调用数据，支持异步上报。
* 6、方便管理有效的区分业务系统。会员（memmber） 商品（goods）
* 7、支持Falcon协议. 监控系统
* 8、国内一线互联网公司上线项目

## 架构图
![shop](https://gitee.com/ym-monkey/flasher/raw/master/img/4.png "4.png")
![shop](https://gitee.com/ym-monkey/flasher/raw/master/img/0.png "1.png")
![shop](https://gitee.com/ym-monkey/flasher/raw/master/img/1.png "1.png")
![shop](https://gitee.com/ym-monkey/flasher/raw/master/img/2.png "2.png")
![shop](https://gitee.com/ym-monkey/flasher/raw/master/img/5.png "5.png")
![shop](https://gitee.com/ym-monkey/flasher/raw/master/img/6.png "6.png")

### 示例代码
* 1、maven依赖

```
   
       com.tl.flasher 
       flasher 
       0.0.5-snapshots 
     
```

* 2、配置

```
  
         
         
         
         
         
     
     
          
         
     
     
         
     
```
* 3、监控数据上报
```
 
     
         
         
     
     
         
     
```

* 4、Java测试

```
@RunWith(SpringJUnit4ClassRunner.class)
@ContextConfiguration(locations = {"/application-tlcache.xml"})
public class TlCache {
   @Autowired
   IRedis iredis;
   @Test
   public void testKey(){
      iredis.set("trade", "monkey" , "2019");
      iredis.get("trade","monkey"));
   }
}
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)