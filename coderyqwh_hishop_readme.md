                                                      hishop项目业务及部署

                                                      一、业务功能介绍：

     1）登录，注册及忘记密码模块（基于Cookie+Redis实现登录sso子系统）
     2）商品分类，详情，列表模块
     3）订单模块（基于Spring Schedule+Redis实现分布式定时关单功能）
     4）购物车及收货地址模块
     5）支付模块（1支付宝扫码支付  2支付宝APP支付）
                                                      二、核心知识点剖析

    1.maven环境隔离
      ftp服务器
      数据库配置
      分环境配置、打包
      mvn clean package -Dmaven.test.skip=true -Pdev (开发环境打包)
      mvn clean package -Dmaven.test.skip=true -Pbeta(测试环境打包)
      mvn clean package -Dmaven.test.skip=true -Pprod(生产环境打包)

    2.Nginx+tomcat集群(高可用，高并发，项目架构横向扩展能力)
        基础环境：nginx部署在slaver_2虚拟机上面，tomcat部署在3个虚拟机上面
        2.1 登录session共享问
        2.2 分布式锁问题（用redis实现）
        2.3 定时任务并发问题

    3.Redis基础强化（http://redis.cn/）
        背景：用c语言编写的高性能key-value非关系型内存数据库，且支持数据持久化
        版本：http://download.redis.io/releases/    (2.8.0)
        3.1 Redis基础命令
        3.2 Redis键命令
        3.3 Redis五种数据结构

    4.redis+cookie+jackson+filter实现单点登录(登录模块代码重构)
        多进程debug调试
        Jedis连接池及封装RedisPoolUtil
        在tomcat集群时session共享问题
        Jackson多泛型序列化和反序列
        Cookie封装及使用
        SessionExpireFilter重置sesion有效期
        Guava cache迁移Redis缓存
        序列化：将对象流转成String字符串
        反序列化：将String字符串转成对象流

     ##################网站安全问题###################
           CSRF（跨域请求伪造）原理：恶意网站发送网站请求，网站的cookie会自动发送过去。
           JWT(JSON WEB TOKEN)：服务端将jwt放到header里面返回，前端代码将jwt放到Local Storage里待用，或是
           服务端直接在cookie中保存HttpOnly=false的JWT。会导致跨站脚本攻击——XSS（Cross site script）
           XSS原理：脚本代码可以盗取cookie或是Local Storage中的数据
     ####################网站安全问题#################

     5.redis分布式
         redis分布式算法 ：取模，从0开始
         hash一致性算法:环形hash空间，32位
         hash倾斜性：对象顺时针方向存储在节点上，节点必须平均分布
         虚拟节点的引入
         命中率计算公式：（1-n/(n+m)）*100% n:原节点 m:新增节点
         封装Shard Redis分布式

     6.spring session框架集成（无侵入单点登录）
         JedisConnectionFactory
         DelegatingFilterProxy
         RedisHttpSessionConfiguration
         DefaultCookieSerializer
         JedisPoolConfig

      7.spring mvc全局异常
         Spring与SpringMVC扫描包隔离（重要！！！）
         未包装全局异常的项目暴露了包结构，类及类方法，sql异常，泄露机密信息
         Springmvc全局异常流程图（MappingJacksonJsonView）

      8.springmvc拦截器实现权限统一校验

      9.restful风格接口，资源定位符

      10.spring schedule实现定时任务
         spring schedule cron生成器
         spring schedule cron配置
         @Scheduled(cron="0 */1 * * * ?")

      11.mysql行锁、表锁
          悲观锁:select ...for update
          乐观锁:在表中加个vesion字段使用时间戳来判断是否更新
          有明确主键是行锁：select * from hishop_produt where id=26 for update
          无明确主键是表锁：select * from hishop_produt where id <> 26 for update
          存在的问题：集群环境中，多台应用服务器重复执行定时任务

       12.redis分布式锁原理
          Redis分布式锁命令：
            setnx(原子性：不存在才能设置值)
            getset（原子性:先get再设置值）
            expire（设置有效期）
            del(删除值)
         Redis分布式锁流程：
             1.setnx(lockkey，currenttime+timeout)
             2.返回1获取锁成功；返回0获取锁失败结束
             3.expire(lockkey)，执行任务
             4.del(lockkey),释放锁
          Redis分布式锁优化：针对死锁的优化
          主要是对2的返回0逻辑再判断：
           1.get(lockkey)的value1，当前value1不为null且当前时间大于value1
           2.getset(lockkey,currenttime+timeout)得到当前value2
           3.判断如果value2==null或者value2==value1则获取锁成功，重复以上步骤
      12.Redisson框架（基于nio的Netty框架，Redis框架）
           1.具有多机多线程并发系统的能力，降低了设计和研发大规模分布式系统的难度。
           2.Redisson实现分布式锁：RLock
           3.Redis主从配置：redis.conf设置slaveof;从库只读不能修改
       13.线上服务器部署（阿里云服务器）
             cp -r a.log  ../a1.log
             vim /etc/sysconfig/iptables //编辑防火墙
             service iptables restart //重启防火墙
             rm -rf  //删除文件
             less  access.log //分页显示文本内容
             tail -f access.log  //查看nginx的实时日志
             ps -ef|grep tomcat //查看应用的进程
             kill -9 21195 //杀死进程21195
----------------------------编写服务器脚本--------------------------
        ./deploy.sh v2.0 www..com
        deploy.sh详细







 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)