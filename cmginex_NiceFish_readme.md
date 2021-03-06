# NiceFish（美人鱼）
谢谢大家，过了1000个星儿了，我可以拿到一个开源奖杯了 :)

NiceFish是一个系列项目，所有前端代码全部采用最新版本的Angular技术栈。

- 【NiceFish】：这是一个微型Blog系统，基于Angular 4.0.0 + ng-Bootstrap，纯前端无后台。http://git.oschina.net/mumu-osc/NiceFish/

- 【NiceFish-Admin】：这是系统管理界面，基于Angular 4.0.0，纯前端无后台。 http://git.oschina.net/mumu-osc/NiceFish-Admin

- 【NiceFish-Admin-ng1】：这是一个基于Angular 1.6.4（最新版）的管理后台模板，用于演示Angular 1.x最新版本的用法，纯前端无后台。https://git.oschina.net/mumu-osc/NiceFish-Admin-ng1.git 。

这个项目需要特别说明一下，根据目前的统计数据，还有我在数十家企业实际看到的情况，国内还有大量的企业在使用Angular 1.x，而其中很多居然没有做任何AMD处理！我的天哪！前端开发发展到了今天这个状态，AMD是标配啊兄弟们。就算你还在用jQuery做项目，AMD也是必须的哦。把所有js全部压在一个大文件里面，然后在index里面一次性加载，不能再这样做了啊！所以我会很快做好这个项目，给你们一个示范，看看大型的业务项目应该如何切分目录、模块，如何做AMD加载。

- 【NiceFish-ionic】：这是一个移动端的demo，基于ionic，也就是最新版本的Angular移动端。http://git.oschina.net/mumu-osc/nicefish-ionic

- 【NiceFish-SpringMybatis】：这是一个Java版的后台服务，http://git.oschina.net/mumu-osc/NiceFish-SpringMybatis 

NiceFish系列项目可以用来帮助你快速搭建个人Blog、微型SNS站点、后台管理系统、移动端应用，或者用于学习Angular。其实我并不在乎你用来干嘛，那关我什么事呢对吧？ 

【注意】如果您希望获得功能更完善的定制版本，请私信联系我。但是请特别注意，功能定制是收费服务。


## 对应的视频教程

此项目对应的视频教程（超清），包括所有PPT，请点这里：https://my.oschina.net/mumu/blog/834254

这是全球第一个完整的“Angular中文视频教程”，由大漠穷秋老师录制。此视频是完全开源免费的，你可以随意使用、转发，但是不能对课程相关的内容进行任何编辑，尤其不能向观众收取任何形式的费用。

你见过哪一个开源项目会如此细致地配上视频教程？

你见过哪个讲师会如此无私地把所有PPT都分享出来？

所以你一定要仔细看啊！

有些人问的那些个问题啊，too simple! somtimes naive!

![视频教程截图](src/assets/imgs/10.png)

## 演示地址

阿里云上的演示地址：http://121.196.220.118:8081/

以下是效果图：

![效果图](src/assets/imgs/1.png)

![效果图](src/assets/imgs/2.png)

![效果图](src/assets/imgs/3.png)

![效果图](src/assets/imgs/4.png)

![效果图](src/assets/imgs/5.png)

我很欣喜地看到，有一些道友已经以NiceFish这个教学项目为蓝本快速搭建了一些自己的小系统，比如下面这个：

![效果图](src/assets/imgs/11.png)

链接在这里：http://www.fuzhutech.com

## 目录结构

![目录结构1](src/assets/imgs/6.png)

![目录结构2](src/assets/imgs/9.png)

## 用法

用git克隆本项目，从命令行进入进入项目根目录，依次执行以下命令：

	npm i -g cnpm
	cnpm i -g @angular/cli
	cnpm install
	ng serve

如果之前装过angular-cli需要先卸载：npm uninstall -g angular-cli
如果之前装过@angular/cli需要先卸载：npm uninstall -g @angular/cli
如果你之前已经尝试安装过node模块，请把NiceFish根目录下的node_moduels目录删掉
然后依次执行以下命令：

	npm cache clean
	npm i -g cnpm
	cnpm i -g @angular/cli
	cnpm install
	ng serve

打开你的浏览器，访问http://localhost:4200/

如果你想让加载的包更小，请使用以下方式启动angular-cli内置的轻量级http server

	ng serve --prod

如果你需要把项目发布到其它类型的Server上，例如Tomcat，需要对Server进行一些简单的配置才能支持HTML5下的PushState路由模式，我在这篇文章里面有详细的介绍https://my.oschina.net/mumu/blog/830696。

【注意】如果你发现ng serve起不来，或者起来有报错，请把NiceFish根目录下的node_modules目录删掉，然后重新执行cnpm install，全局的@angular/cli也需要重装。

## 更新

打开命令行，进入NiceFish根目录，依次执行以下命令：

	git pull
	cnpm update
	ng serve

噢对，如果你pull代码之后发现起不来了，请把你项目下的node_modules全部删掉，然后重新cnpm install。这里确实有点坑，但是我也不知道为什么。

## AOT&TreeShaking

开发状态打出来的bundle体积比较大，在发布到生产环境之前需要进行AOT操作，用法如下：

打开命令行，进入NiceFish根目录，执行以下命令：
	
	ng build --prod

加上--prod参数之后，angular-cli会自动启用TreeShaking（摇树）特性，简而言之，就是把用不到的包全部剔除掉，就像从树上把枯叶子摇下来一样，很形象吧？

angular-cli会在项目根目录下生成一个dist目录，里面就是编译、压缩好的文件了。仔细观察你会发现，这些文件的体积已经被大幅度压缩，加上gzip之后有一些文件只剩下1/4左右的大小。

![效果图](src/assets/imgs/7.png)

![效果图](src/assets/imgs/8.png)

关于Tomcat如何启动gzip，我专门写了一篇文章来介绍配置，请点这里：https://my.oschina.net/mumu/blog/830742

【请注意】最新版本的angular-cli已经内置了对AOT和TreeShaking的支持，只要像上面这样在build的时候加上--prod参数就可以了，不需要再做任何其它任何配置工作，官方网站上的那一篇文档没有及时更新。

## 注意（请仔细看）

如果你用原生的npm进行安装，可能需要采用科学的上网方式才能安装某些包！

所以强烈推荐采用cnpm来安装！

## 推荐项目
ng2整合各种插件的项目-Code Be
https://git.oschina.net/zt_zhong/CodeBe

## 开源许可证
 MIT

 你可以随意使用此项目，无需通知我，因为我可能很忙没空搭理你。

## 关于我
我是大漠穷秋，目前是Google Angular项目组在中国的开发者PM，负责Angular的推广工作，我会在各种渠道经常发布一些与Angular相关的技术文章，希望能给大家带来一点点帮助，请点这里：https://my.oschina.net/mumu/blog  。

如果您的企业或者组织需要Angular方面的技术支持，请填写这份申请单：https://gdgdocs.org/forms/d/e/1FAIpQLSfKA15nS0md58fR__tAV6gSEIPsVsLksT9knOgObq9IbVPuQg/viewform

【注意】我每天都会收到大量的求助消息，真的有点忙，所以请准确描述您的问题，最好能加上一些截图，非常感谢！


## 在线交流QQ群

    Angular 1区:286047042（满） 

    Angular 2区:139357161（满） 

    Angular 3区:473129930（满） 

    Angular 4区:483016484（将满） 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)