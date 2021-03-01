# GOSP = Giveda® Open Source Project   
for English, please refer to: https://gitee.com/giveda/GOSP/blob/master/README_en.md  

# 摘要  
Qt是欧洲人创始的一个优秀的c++开发框架，API简单易用，社区庞大，资源丰富；但Qt太重量级了（需要很多的RAM和ROM，非常复杂）。为了解决这个问题，我开发了GOSP这个框架。GOSP在不依赖Qt的前提下，提供了类似Qt的API接口，仅需要几百KB的硬件资源（比Qt小的多），能运行在Qt不支持的低性能领域（对Qt形成补充），适用于嵌入式开发。    
  **谨以此产品向Qt致敬，致敬Qt为世界做出的杰出贡献。**         

example效果演示：   
![在doc/images/目录下](docs/images/DVB_edit_chnl_768x432.gif)

![在doc/images/目录下](docs/images/DVB_mainMenu_768x432_png.gif)


# 一、简介和概述  
Qt是欧洲人创始的一个优秀的c++开发框架，API简单易用，社区庞大，资源丰富。2018年，Qt公司内部立项了一个将Qt移植到MCU的研发新项目，资源占用情况如下：  
*) ROM占用情况：从6MB到13MB  
*) RAM占用情况：从4MB到10MB  
 **综上，Qt太重量级了（需要很多的RAM和ROM）；我非常喜欢Qt，因此我开发了GOSP这个框架。GOSP在不依赖Qt的前提下，提供了类似Qt的API接口，仅需要几百KB的硬件资源（比Qt小的多），能运行在Qt不支持的低性能领域（对Qt形成补充），适用于嵌入式开发。**      
2019-06-03，发表v1.0，版本代号为：沉默的蓝色幽灵。    
I wish it can be a member of Qt's ecosystem in the future.    
  **谨以此产品向Qt致敬，致敬Qt为世界做出的杰出贡献。**         

参考文献：  
http://blog.qt.io/cn/2018/08/15/qt_on_microcontrollers_mcu/  
http://giveda.com/


# 二、主要特色

* 提供了类似Qt的API。  
* 100%使用图片来实现个性化的控件和界面。（见下文的截图）   
* 基于别具一格的Giveda信号槽技术，各个模块代码之间无耦合。  
* 非常简单，非常易用。   
* GOSP是码云GVP项目，其产权归全体贡献者共同所有，贡献者根据自身对项目的不同贡献而享有不等比例的产权。   


# 三、开源协作、授权许可  
## 3-1 开源协作模型  
在本项目中，参与者被划分为如下角色：   
*) 会员：凡为本项目提供资源支持和/或人力支持的个人或实体，皆为本项目会员。   
*) 常务理事：负责项目的演进、整体目标、组织架构、日常事务。常务理事暂由发起人担任，随着项目发展，要吸收其他会员共同作为常务理事。   
*) 普通参与者：除了会员和常务理事外的其他参与者，皆为普通参与者。   

会员可获得如下收益：   
*) 授权许可费的免除或优惠。   
*) 深度参与本项目开发过程，缩短自身产品的开发周期。   
*) 人才培养、社区荣誉。   
*) 会员间的知识产权共享。    
*) 本项目的知识产权归全体会员共有，会员根据自身对项目的不同贡献而享有不等比例的产权。    

## 3-2 授权许可协议（适用于普通参与者）  
 **本协议适用于未被列入《exceptions/black list》的普通参与者，被列入《exceptions/black list》的个人和实体不适用本协议。**  
对于那些不涉及任何商业目的或商业行为的个人学习用途，在没有分发的情况下，使用者遵守 **GNU AGPL v3.0** 即可。  
如果涉及任何商业行为或商业目的，那么大家在商言商，采用如下商业许可协议，以保护开源生态中各方的合法权益：  
*) 这是一个开源软件，我们希望它有用，但不提供质量保证（哪怕是隐含的或显而易见的质量保证）。虽然不提供质量保证，但并不意味着你能利用此点去侵害我们的商誉；如果需要质量保证，你可以购买商业版本。作为著作权人（以下简称我们），我们已经尽到了告知义务。一旦发现有人侵犯或者试图侵犯我们商誉，我们必将利用行政和法律手段死磕到底。   
*) 除了法律允许免费使用的情形，任何用到本软件全部或部分代码的行为，都需要向我们付费购买许可；禁止未经许可将本软件全部或部分翻译成其它编程语言；分发权不能免费获得，禁止在未经许可的情况下以任何形式（包括但不限于源码形式、二进制形式等）私下或公开向别人分发本软件全部或部分代码。   
*) 除非交易双方在《许可合同》中另有约定，否则的话，对本软件的任何修改、任何基于本软件全部或部分代码的衍生品、任何基于本软件全部或部分代码开发得到的作品、（通过任何形式）引用了本软件全部或部分代码的作品等都需要及时向我们定向开源，并同时向我们授权，允许我们以此相同协议对外公开以上软件代码和/或作品，允许我们自由使用以上软件代码和/或作品，允许我们将其授权给我们的客户进行自由使用。基于我们并不知道是谁在使用本开源软件，为了保护你的权益，你应当及时与我方商谈、签订《许可合同》。及时主动联系我方商谈签订《许可合同》是你的义务。   
*)  **商业许可实行按年对公司（老板）收费。主动联系我们并付费的价格为市场价格。被人举报的被动付费价格为惩罚性价格（市场价格的10倍）。举报情形包括但不限于：违反本授权协议等。**     
*)  **举报者可获得不低于成交额30%的现金奖励。**       
*) 中国的出口法律和法规适用于我们的发行版，并且随着产品和技术再出口到其它地区依旧保持有效。我们保留禁止任一用户使用以上开源软件的权利。  
*) 解释权归我方所有。因你方违反本协议造成我方损失的，你方负完全责任。  
 **只有完全同意以上协议，你才可以使用本软件。**  
 **如果不同意以上协议，不要使用本软件。**    

## 3-3 筹划
  **视情况而定。**   


# 四、如何使用
查看如下《简易指导文档》： https://gitee.com/giveda/GOSP/blob/master/HowTo.md  
《HTML文档》： http://giveda.com/gui_engine/html/index.html    
欢迎加入QQ交流群：914464844    


# 五、效果演示  

![Giveda](docs/images/configureResult1.jpeg)

![Giveda](docs/images/gCtrlButton.jpeg)

![Giveda](docs/images/gCtrlIconView.jpeg)

![Giveda](docs/images/gCtrlItem.jpeg)

![Giveda](docs/images/gCtrlLineEdit.jpeg)

![Giveda](docs/images/gCtrlListBox.jpeg)

![Giveda](docs/images/gCtrlMsgBox.jpeg)

![Giveda](docs/images/gCtrlProgressBar.jpeg)

![Giveda](docs/images/gCtrlRadioButton.jpeg)

![Giveda](docs/images/debugInfo.jpeg)

![在docs/images/目录下](docs/images/DVB_768x432.gif)

![在doc/images/目录下](docs/images/DVB_edit_chnl_768x432.gif)

![在doc/images/目录下](docs/images/DVB_mainMenu_768x432_png.gif)

https://gitee.com/giveda/GOSP/tree/master/docs/images/DVB_768x432.gif  
https://gitee.com/giveda/GOSP/tree/master/docs/images/DVB_768x432_large.gif  
https://gitee.com/giveda/GOSP/tree/master/docs/images/DVB_edit_chnl_768x432.gif  
https://gitee.com/giveda/GOSP/tree/master/docs/images/DVB_mainMenu_768x432_png.gif  


# 六、写在最后  
  **这是一个处于筹划过程中的项目，我只是在有兴趣的时候，做一点自己感兴趣的事情。如果你觉得本软件有用，你可以按照上述第三章节的指引，加入本软件的开源协作模型，支持本项目向你期望的方向发展。**   
GOSP是码云GVP项目，其产权归全体贡献者共同所有，贡献者根据自身对项目的不同贡献而享有不等比例的产权。   
  **邮箱: lei@giveda.com**   


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)