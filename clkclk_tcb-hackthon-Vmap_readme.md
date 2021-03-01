# 小区疫情监控地图

#### 产品描述

 由于新冠病毒目前无有效药，最好的措施就是早发现早隔离，尤其是开春返工在即，人传人后果会非常严重。
而目前的疫情地图是以省市为单位，对个人实际意义不大，很多人，尤其是老年人在不知情情况下出入感染的小区，导致被感染的危险。
基于深圳，珠海，济南等城市卫建委发布的新冠病毒感染者的小区分布信息，为出现疫情小区附近的人提供实时提醒，帮助尽早预防和及时隔离。


#### 产品特性

1. 云端自动获取全国最新各小区疫情
2. 对用户自定义的关注小区位置，根据最新疫情，在附近出现疫情时，主动发送危险通知

#### 依赖
1. 小程序云开发
2. 高德地图API


#### 安装及配置
1. 下载到本地:
    - 通过命令行: ```git clone https://gitee.com/Zheng_jinli/tcb-hackthon-Vmap.git```
    - 或者，下载项目zip文件并解压

2. 导入微信小程序开发工具
3. 导入时，如果提示需要AppID，请输入：wxb8ff319dcee619df
4. 确认miniprogram/utils/config.js文件中：
    - 云函数设置: ```Config.cloud = { env: 'xiaotiti-zazc2'};```
    - 消息订阅ID: ```Config.lessonTmplIds = new Array('lQ4P6kuON0riu90bMqdtQoeuAju3bc1l4uvHxa6Ywyw');```
6. 选中cloudfunctions目录，点击右键选择当前环境为"小提提"
8. 将cloudfunctions目录下的五个云函数(目录): geocode, inputtips, mySubscribe, send和subscribe，分别右键点击后，在弹出菜单选择选择"上传并部署: 云端安装依赖(不上传 node_modules)"
7. 点击微信小程序开发工具的云开发按钮进入云开发管理页面，再点击云函数进入云函数配置页面，对geocode云函数增加环境变量:
    - key: MAPKEY， value: 72932302ec093dc68265763da36ecf41
8. 完成

#### Bug反馈
    - 请在>>[Issues](https://gitee.com/Zheng_jinli/tcb-hackthon-Vmap/issues/new?)页面直接提交

#### 贡献方式
    - 请参考文档[CONTRIBUTING.md](https://gitee.com/Zheng_jinli/tcb-hackthon-Vmap/blob/master/CONTRIBUTING.md)


#### 联系方式
    - Wechat ID: zheng_jinli

#### License
    - [Apache-2.0](https://gitee.com/tysb7/tcb-hackthon-YT/blob/master/LICENSE)

#### 产品预览图片
![附近疫情小区地图](https://images.gitee.com/uploads/images/2020/0220/084118_a62f2a82_5661443.jpeg "1.jpeg")
![搜索与订阅监控地点](https://images.gitee.com/uploads/images/2020/0220/084159_8445e1ec_5661443.jpeg "2.jpeg")
![管理监控地点](https://images.gitee.com/uploads/images/2020/0220/084215_ef8cae42_5661443.jpeg "3.jpeg")
![收到疫情监控信息](https://images.gitee.com/uploads/images/2020/0220/084231_941e80e3_5661443.jpeg "4.jpeg")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)