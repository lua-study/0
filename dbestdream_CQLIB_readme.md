# CQNET

#### 介绍

CQ-Base是基础组件
    
    包含 高性能日志模块、各种加密算法，hash、AVL Tree、大数处理、线程池 等等，后续将加入redis、内存池等

CQ-Net是基于boost::asio基础网络库
    
    普通PC，万级并发；最高支持千万级并发，目前支持傻瓜式创建 tcp客户端、服务器，后续将加入http，udp以及音视频通信协议。

CQ-App是基于CQ-Net做的实验性tcp客户端/服务器demo
    
    后续将支撑客户端完成音视频通信，图片、语音、文件发送，好友管理，群组管理。

CQ-Chat是基于Base、Net、Qt框架的实际项目
    
    后续将加入文件传输、语音、视频聊天，添加好友，发送语音、图片消息。


CQ-Test是对以上库的功能性测试
    
    后续将继续完成基础组件、网络库的详细测试方案。

#### 软件架构
    基于消息KEY的分布式系统架构设计，多服多端，高并发。
    采用 VisualStudio 2019 + Boost 1.71 + Qt 5.13开发，UI绘制由 Qt Creator 4.9完成。
![架构](https://images.gitee.com/uploads/images/2020/0531/024527_e6fc7e7a_766467.png "架构.png")

#### CQ-Chat 相关截图
登录时，可以实时获取头像；登录后，生成托盘小图标，从服务器拉取好友列表。

![登录1](https://images.gitee.com/uploads/images/2019/0821/124204_51cea8e9_766467.png "login1.png")
![登录2](https://images.gitee.com/uploads/images/2019/0821/124214_3751864b_766467.png "login2.png")
![登录3](https://images.gitee.com/uploads/images/2019/0821/124224_27b4ad68_766467.png "login3.png")
![主面板1](https://images.gitee.com/uploads/images/2019/0821/124232_b331dea9_766467.png "main1.png")
![主面板2](https://images.gitee.com/uploads/images/2019/0821/124241_5b512e1f_766467.png "main2.png")
![主面板3](https://images.gitee.com/uploads/images/2019/0821/124253_0eeeb757_766467.png "main3.png")
![主面板4](https://images.gitee.com/uploads/images/2019/0821/124300_a85d3f4e_766467.png "main4.png")
![主面板5](https://images.gitee.com/uploads/images/2019/0821/124308_8d624b90_766467.png "main5.png")
![好友界面](https://images.gitee.com/uploads/images/2020/0112/154544_7aa7ff54_766467.png "屏幕截图.png")
![聊天界面](https://images.gitee.com/uploads/images/2020/0112/154620_90300822_766467.png "屏幕截图.png")
![发送消息](https://images.gitee.com/uploads/images/2020/0112/154646_0841cf4b_766467.png "屏幕截图.png")




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)