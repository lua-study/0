# JARVIS(贾维斯) V2019

**J·A·R·V·I·S** `(Just Another Rather Very Intelligent System)`
**贾维斯，钢铁侠托尼的AI助理，幻视的核心软件**。在日常生活中，贾维斯为他管理战甲，为他报天气，查资料，运算数学模型，制造新设备，拥有人类管家所不能及的超高效率。在战斗中，贾维斯更是钢铁侠的左膀右臂，帮他评估战局，提出建议，有时帮他转接电话......

### 该项目属于智能家居定制项目的一部分，该项目还包括:

- [**homehub 设备接入网关, 采用Go+C开发**](https://gitee.com/adaidesigner/homehub)
- [**homemaster-driver 网关硬件设备驱动, 由C编写的linux内核模块**](https://gitee.com/adaidesigner/homemaster-driver)
- [**zigbee3.0-coordinator 网关协调器部分, 芯片采用NXP的JN5169**](https://gitee.com/adaidesigner/zigbee3.0-coordinator)
- [**jarvis 家庭控制中枢服务端部分, 采用Go编写**](https://gitee.com/adaidesigner/jarvis)
`取名来源: JARVIS(贾维斯)钢铁侠托尼的AI助理，幻视的核心软件`
- [**home 家居ios端应用程序,兼容iphone和ipad, 由swift编写**](https://gitee.com/adaidesigner/home)

### 智能家居定制项目介绍网址: **https://adai.design/design**

## 智能家居定制-控制中枢(服务端)
- 自动化是智能家居的核心部分，因为我们将大部分的业务都移到云端处理，充分利用云端处理处理逻辑的优势。
- 服务端的架构模拟自然的家庭组成结构：

![img](doc/jarvis2019.png)

## 家庭的主要组成部分
- 家庭基本信息 (ID、名称、数据版本、位置信息)
- Members: 家庭成员
- Containers: 设备容器列表
- Rooms: 房间列表
- Service: 服务列表
- Scenes: 家庭场景列表
- Automations: 自动化列表

#### 通信示例
- 获取家庭基本信息
- `(当客户端登录后的第一步，获取家庭基本信息，来确认是否需要更新本地家庭数据库)`
- 请求数据:
```
{
    "path": "home/info",
    "home": "64e649c2-897c-4409-a778-d3d2611e7e24",
    "method": "get"
}
```
- 返回结果
```
{
    "path": "home/info",
    "home": "64e649c2-897c-4409-a778-d3d2611e7e24",
    "method": "get",
    "state": "ok",
    "data": {
        "id": "64e649c2-897c-4409-a778-d3d2611e7e24",
        "version": 4,
        "name": "云の家",
        "members": [
            {
                "id": "34c92c64-6d84-490f-8e25-e27e1c8bf58e",
                "role": "admin"
            }
        ]
    }
}
```
- 获取家庭数据
```
{
    "path": "home",
    "home": "64e649c2-897c-4409-a778-d3d2611e7e24",
    "method": "get",
    "state":"ok",
    "data": {
        "name": "云の家",
        "id": "64e649c2-897c-4409-a778-d3d2611e7e24",
        "version": 6,
        "members": [ ... ],
        "containers": [ ... ],
        "rooms": [ ... ],
        "services": [ ... ],
        "scenes": [ ... ],
        "automations": [ ... ]
    }
}
```

#### 历史版本
- 2019-11-10 工程改名jarvis(贾维斯)
- 2018-12-20 创建工程awakening(觉醒)

----
## 智能家居定制项目介绍网址: **https://adai.design/design**

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)