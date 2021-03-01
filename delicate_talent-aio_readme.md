 
  talent-aio: 让天下没有难开发的即时通讯
 

 
  talent-aio是什么？应用场景是什么？性能如何？稳定性如何？上手是否困难？
 
 
	  talent-aio是什么 ：talent-aio是基于java aio实现的即时通讯框架，功能类似netty，当然talent-aio的出现是要在性能和易用性方面实现对netty的超越 
	  应用场景 ：即时通讯场景皆可----实时聊天、TCP长连接(譬如mysql客户端、redis客户端等)、实时监控等 
	  性能 ：单机IM场景，可处理 73万条消息/秒 ，收发数据量 70M/秒 ，可同时稳定维护 10万级以上TCP长连接 (测试环境：i7 4790、8G内存、windows7) 
	  稳定性 ：talent-aio本身来源于经历严酷考验的talent-nio，稳定性方面有一个很好的基础。最近也做过稳定性测试，压过两个星期， 7万TCP长连接 ，妥妥地没有任何异常(测试环境：服务器i7 4790、8G内存、windows7；客户端为4台虚拟机和一台笔记本) 
	  上手是否困难 ：本项目提供了一个helloworld版的例子，如果已有bytebuffer知识基础， 30分钟就可以上手 。本项目还提供了一个用于压测的聊天版的例子，但涉及到了界面、性能测试和统计、类似QQ群聊等功能，所以上手会要一天左右的样子 
 


 
  talent-aio产生的背景
 
 
	 2011年本人有幸参与了中兴某刀片的网管系统，大领导亲点让我来改造原来的实时通讯模块，因为老系统每管理一个节点就需要两个线程，实测出来的数据是管理100个节点时，就会达到1000多个线程，稳定性和性能极差。在这样的背景下，开始学习nio，改造后的系统线程维持在100个左右，可管理上千个节点，消息收发速度极快，最近和中兴同事了解过，核心代码仍然在运行，足见稳定性，这就是后来talent-nio的雏形 
	 后来作为热波间(一个直播平台)的平台端架构师，持续优化和封装了talent-nio，使之可以支持4万TCP长连接，每秒可以收发10万条消息 
	 因为热波间架构师的角色，认识了不少业界朋友，很多朋友要求我开源talent-nio，但是talent-nio在API设计方面不是太好，开源出来无疑个砸牌子的事情 
	 一翻纠结后，写了talent-aio，线程池部分来源于并优化于talent-nio，其它部分一律重新设计，尤其是锁的优化和API的重新设计，为了折衷花费了大量精力。 
 


 
  netty和talent-aio两者，应该选谁？
 
 
	 如果您已经精通并有把握驾驭netty，选谁都不重要 
	 如果条件1不成立，建议花30分钟学习一下本项目提供的helloworld例子入下门，相信你会有惊喜发现 
	 对性能和稳定性要求极高，建议talent-aio。netty的性能也好，但talent-aio性能更好，对前者几乎形成碾压之势，本项目提供的im例子可以证实这一点，大家可以对比一下测试数据 
	 talent-aio已经提供了绑定群组、绑定用户id等功能，方便实际业务方面的开发 
	 talent-aio对开发者的唯一要求是会bytebuffer，这个不管你是用哪个aio或 nio框架都无法逃避的技能，因为自定义编码解码是必须要接触到这个的。当然不排除有框架不需要掌握这个，而只需要会byte[]，但必然这是要浪费一层性能损耗的 
 


 
  talent-aio如何快速上手？
 
本项目已经提供了一个helloworld版的例子，虽然有3个maven工程，6个java文件，但是有效代码只有区区100多行，结构清晰极易上手，位于:example\helloworld目录，可按如下步骤上手
 
	 先运行install.bat，用来安装本项目所有代码 
	 运行com.talent.aio.examples.helloworld.server.HelloServerStarter 
	 运行com.talent.aio.examples.helloworld.client.HelloClientStarter 
	 顺藤摸瓜，花20分钟仔细阅读这个例子的100多行代码 
	 恭喜您，你已经顺利上手了，后续遇到问题可以点击 
	 
   咨询 
 


 
  参与talent-aio将得到什么福利
 
 
	 java aio的驾驭需要有扎实的多线程基础，并且需要掌握很多多线程技巧，而talent-aio是将多线程技巧运用到极致的框架，所以一旦您参与到本项目，你将会从本项目中学到很多关于多线程的技巧。 
	 本项目会陆续提供一些业界案例作为例子供大家参考，譬如融云的IM 
	 本项目会提供一个技术交流群，与大家一起分解工作中遇到的困难 
 


 
  获取帮助
 
 
	 
	talent-aio官方交流群:
	 
     
	 
	 
	 邮箱: tywo45@163.com  
	 
	作者QQ(不能及时回复):
	 
	 
	 
	 
 


 
  帮助本项目
 
 
	 
	 
      提交Issue
	 
	为本项目出谋划策，或是指出项目BUG
	 

	 
	点击右上方的
	 
	 Star 
	 
	为本项目积攒人气
	 

	 
	碰到有需要即时通讯的朋友（譬如IM系统、实时监控系统等），请按如下方式推荐本项目
		 
			 
			告知本项目的地址: https://git.oschina.net/tywo45/talent-aio
			 
			 
			告知本项目的技术交流群: http://shang.qq.com/wpa/qunwpa?idkey=95588b929b2832f606f4deb74a423d61257f3c08b9790ac57c29aebd09364459
			 
		 
	 

	 
	如果以上都不想做，又想为开源项目出点力，那么请亲点击下方的
	 
	 捐赠 
	 按钮，为本项目积攒金币
	 
 


 
  基于talent-aio实现的用于压测的群聊系统
    (点击本链接可见性能图) 
 

 
	 
	先运行install.bat，用来安装本项目所有代码
	 
	 
	运行server examples: com.talent.aio.examples.im.server.ImServerStarter
	 
	 
	运行client examples: com.talent.aio.examples.im.client.ImClientStarter
	 
	 
	 
 



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)