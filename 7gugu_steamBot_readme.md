    简介:   
 目前已提供完整的函数库,各位dalao可直接通过二次开发成Bot便可投入使用,本项目严格遵守  Apache License V2   
 以下为目前已实现的API
 
 
 	   接受/拒绝/取消/发起交易   
 	   支持二步验证的登录   
 	   获取单笔交易状态   
	    获取steamID SessionID   
 	   获取玩家游戏列表   
 	   获取API秘钥   
 	   获取玩家库存   
 	   支持自动过二步验证[需要提供shared_sersect,方法详参我的博客]   
 	   支持面对象 
       支持代理服务器   
  
 	   支持遍历未确认的交易请求   
 	   确认/取消发回饰品的交易   
 

 
 

  可用方法:  
 
 
 
 setSteamID 
 设定SteamID 
 
 
 setDeviceID 
 设定DeviceID 
 
 
 setSharedSecret 
 设定SharedSecert 
 
 
 setIdentitySecret 
 设定IdentitySecret 
 
 
 setProxyServer 
 设定代理服务器信息 
 
 
 getApiKey 
 获取API-KEY 
 
 
 getgamelist 
 获取用户游戏列表 
 
 
 getinventory 
 获取用户库存 
 
 
 send 
 发起一笔饰品交易 
 
 
 login 
 登录Steam账户 
 
 
 acceptoffer 
 接受交易报价 
 
 
 canceloffer 
 取消交易报价 
 
 
 declineoffer 
 拒绝交易报价 
 
 
 GenerateSteamGuardCode 
 生成2FA验证码 
 
 
 fetchConfirmations 
 遍历确认列表 
 
 
 getConfirmationTradeOfferId 
 获取交易确认页的TradeOfferId 
 
 
 acceptConfirmation 
 接受确认请求 
 
 
 cancelConfirmation 
 取消确认请求 
 
 
 
   
   
   交易字符串样例:   
 
 
{"newversion":true,"version":1,"me":[{"assets":{"appid":"游戏AppID","contextid":"2","amount":1,"assetid":"游戏饰品的ID"}],"currency":[],"ready":true},"them":{"assets":[],"currency":[],"ready":false}}
 
 
   开发文档:   
 
 https://www.yuque.com/books/share/8f76ee1e-917e-4656-82d2-cebec314829c?# 
 
   注意事项:   
这些是使用Umarket试运营后得出的一些注意事项,请注意!
 
 	 机器人账户一定要有超过5USD的交易记录,不然作为受限账户是无法发起发回交易的 
 	 机器人一定要有消费记录,不然可能会受限,暂挂住商品 
 	 Steamcommunity极其不稳定,有时候login返回Null或者Empty Response都是因为无法正常访问Steam的服务造成的 
 	 Steam的交易确认页面有时候会抽搐,需要多加载几次,才能刷新出来 
 	 解决无法访问Steam服务的方法有两个一是使用各家的加速器,二是使用科学手段来修复网络不可用,三是把机器人放到国外去 
 
   
   
   联系方式:    
  邮箱:gz7gugu@qq.com 

   [有问题邮箱留言,我看得见的]   
 
 

   更新日志:   
 2019/06/15: 
 时隔一年时间,加入了遍历确认的功能。 
 Umarket也弃坑了[项目太大了,一个人无法carry,以后再考虑用框架重写] 
 不过这个SteamBot终于可以用于实际的项目中了,已形成一个交易闭环了,接下去就交由各位dalao做下去吧OWO 
 还有就是,欢迎大家常到我的Blog看看呀,就写到这了,Peace 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)