# 3TMS/CTMS第三方接口文档

------

 

- [TMS/CTMS第三方接口文档](#tmsctms第三方接口文档)
    - [接口简介(请仔细阅读!)](#接口简介请仔细阅读)
    - [接口说明](#接口说明)
    - [常见问题](#常见问题)
- [接口凭证](#接口凭证)
    - [获取登陆凭证接口](#获取登陆凭证接口)
    - [更新登陆凭证接口](#更新登陆凭证接口)
- [运单类接口](#运单类接口)
    - [创建订单接口](#创建订单接口)
    - [查询订单接口](#查询订单接口)
    - [批量查询订单接口](#批量查询订单接口)
    - [修改订单接口](#修改订单接口)
    - [撤销订单接口](#撤销订单接口)
    - [订单货物类接口](#订单货物类接口)
        - [追加订单货物接口](#追加订单货物接口)
        - [修改订单货物接口](#修改订单货物接口)
        - [删除订单货物接口](#删除订单货物接口)
- [车次类接口](#车次类接口)
    - [创建车次接口](#创建车次接口)
- [订阅类接口](#订阅类接口)
    - [订单订阅接口](#订单订阅接口)
    - [取消订单订阅接口](#取消订单订阅接口)
    - [车次订阅接口](#车次订阅接口)
    - [取消车次订阅接口](#取消车次订阅接口)
    - [受理单订阅接口](#受理单订阅接口)
    - [取消受理单订阅接口](#取消受理单订阅接口)
- [受理单类接口](#受理单类接口)
    - [创建受理单接口](#创建受理单接口)
    - [更新受理单接口](#更新受理单接口)
    - [批量查询受理单接口](#批量查询受理单接口)
    - [撤销受理单接口](#撤销受理单接口)
    - [批量解绑受理单设备](#批量解绑受理单设备)
- [其他接口](#其他接口)
    - [获取组织机构列表接口](#获取组织机构列表接口)
    - [添加客户接口](#添加客户接口)
- [部分参数说明](#部分参数说明)
    - [运单参数说明](#运单参数说明)
    - [修改运单参数说明](#修改运单参数说明)
    - [受理单参数说明](#受理单参数说明)

 

## 接口简介(请仔细阅读!)

本文档为3TMS/CTMS第三方开放接口文档，操作流程为：
1. 注册并开通TMS账号（正式环境账号联系实施，应该已经开通过了）；
2. 获取接口访问令牌（token令牌只需获取一次即可，**有效期为一年！**）；
3. 调用TMS提供的接口（需要先获取令牌（access_token））；
4. 所有接口需要使用主账号调用，类似创建订单之类的接口需要使用主账号调用以后系统中才能看到！ 
**请使用主账号获取对应的token再调用其他接口!!!**

- **什么是主账号**：即贵公司在我们系统中创建的第一个账号，其后所有的贵公司系统中的账号都是子账号。如果不知道自己是否使用的主账号或者主账号具体是哪个请联系相关负责人。

- **接口统一URL地址**：测试环境=http://api.test.56ctms.com ，正式环境=http://api.56ctms.com
- **测试环境系统地址**：3TMS=http://go3tms.test.56ctms.com ，cTMS=http://test.56ctms.com
- **测试环境账号**：账号=19012345678 ，密码=123456  账号并不互通，此账号对应的是测试环境的域名，正式环境无法使用！
- **获取接口访问令牌**： /login.html?redirectUri=你们的回调地址（获取令牌（access_token））  (PS：输入申请到的CTMS账号密码)
此外，也可以通过调用[获取登陆凭证接口](#获取登陆凭证接口)生成令牌
- **调用接口方式**：url + ?access_token=生成的token，参数传递使用JSON格式，例：http://api.test.56ctms.com/customer_order/create_customer_order?access_token=fe12047e-52b1-418c-848c-d08a885095a5
**请勿将请求参数拼接在URL中传递！**
- **调试地址**： /swagger-ui.html
- **Demo**：提供了Java和Python的Demo，代码参考本项目下的[JavaDemo](https://gitee.com/kuaihuoyun_ctms/ctms-sdk-demo/tree/master/JavaDemo/src.main/java/demo)和[Python3Demo](https://gitee.com/kuaihuoyun_ctms/ctms-sdk-demo/tree/master/Python3Demo)目录


## 接口说明

所有接口支持RESTful的方式访问，返回结果首先判断http状态码，有如下几种情况：

1. 404表示接口不存在，请检查调用的接口地址，协议的格式是否正确
2. 401表示授权失败，需要重新登陆获取access_token
3. 200，201，20*表示调用接口成功，返回body中调用结果，是http JSON格式的，包含以下字段

- **code**：状态码，取值有 200，非200；200 表示接口调用成功， 非200 表示接口调用失败
- **message**：错误信息，当接口调用失败（状态码为 非200）时，返回的错误信息
- **data**：返回数据，接口调用成功（状态码为 200）之后返回的数据

**接口中所有时间均使用时间戳，精确到秒**


## 常见问题
[有问题先看这里！](PROBLEMS.md)

# 接口凭证

## 获取登陆凭证接口

**简要描述：** 获取登陆凭证

**请求 URL：** `/user/generate_access_token/v2`

**请求方式：** POST

**需要认证：** 是

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|
| `userName` | 是 | `String` | `账号` |
| `password` | 是 | `String` | `密码` |

**返回示例**

- 调用成功示例

```java
{
    "code": 200,
    "message": null,
    "data": {
        "accessToken": "9d0dfe02-2349-421c-90ec-4b9ea174701b",
        "refreshToken": "9f8326bc-c29f-4a28-a512-26caa1a9850a"
    }
}
```
- 调用失败示例

```java
{
    "status": 500,
    "message": "账号或密码不正确"
}
```


## 更新登陆凭证接口

**简要描述：** 更新登陆凭证

**请求 URL：** `/user/refresh_access_token/v2`

**请求方式：** POST

**需要认证：** 是

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|
| `userName` | 是 | `String` | `账号` |
| `refreshToken` | 是 | `String` | `刷新凭证` |

**返回示例**

- 调用成功示例

```java
{
    "code": 200,
    "message": null,
    "data": {
        "accessToken": "9d0dfe02-2349-421c-90ec-4b9ea174701b",
        "refreshToken": "9f8326bc-c29f-4a28-a512-26caa1a9850a"
    }
}
```
- 调用失败示例

```java
{
    "status": 500,
    "message": "账号或刷新凭证不正确"
}
```

# 运单类接口

## 创建订单接口

**简要描述：** 开单

**请求 URL：** `/order/create_order`

**请求方式：** POST

**需要认证：** 是

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|
| `orderList` | 是 | Array[[OrderEntity](#运单参数说明)] | 运单列表，具体内容点击类型进行查看 |

**返回示例**

- 调用成功示例

调用成功但是系统中查看不到时请先阅读 常见问题 
```java
{
    "code": 200,
    "data": ["1712051703640558"],
    "message": null
}
```
- 调用失败示例

```java
{
    "status": 500,
    "message": "订单创建失败"
}
```


## 查询订单接口

**简要描述：** 查询订单，包含详细的货物信息

**请求 URL：** `/order/find_order/v2`

**请求方式：** POST

**需要认证：** 是

**调用频率限制：** 一小时内最多调用一万次，超过会提示操作频繁

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|
| `orderNumber` | 否 | `String` | TMS系统生成的订单号，多个单号用英文“,”隔开，中间不要有空格，最多20个 |
| `phoneNumber` | 否 | `String` | 发货人手机号 |
| `customerNumber` | 否 | `String` | 客户单号，对应TMS系统中的客户单号 |

**返回示例**

- 调用成功示例

```java
{
    "code": 200,
    "message": null,
    "data": [
        {
            "id": "5c4ad2619c023a001044079a", //订单id
            "uid": "5bc725b6e4b07d20a861600f", //主账号uid
            "number": "1901251709800228", //运单号
            "wmsNumber": null, //wmsNumber，即创建订单时的orderNumber
            "wmsLocation": null, //集货位
            "operator": "5bc725b6e4b07d20a861600f", //操作人uid
            "createUserId": "15161181167", //创建人手机号
            "createUsername": "gmw", //创建人姓名
            "deliveryTime": 1548669600, //提货时间，秒为单位的时间戳
            "deliveryType": null, //提送类型 1, "自提"  2, "送货"
            "appointArriveTime": 1548980160, //预约送达时间，秒为单位的时间戳
            "customerOrderNumber": "JSOUT1234567", //客户单号
            "startAddress": "杭州", //起始地址
            "endAddress": "千岛湖", //目的地址
            "consigner": { //发货方信息
                "name": "发货方", //发货人姓名
                "phone": "15161151543", //发货人手机
                "address": { //发货人地址相关信息
                    "province": "浙江省", //省
                    "cityCode": "", //城市代码
                    "city": "温州市", //城市
                    "district": "鹿城区", //区
                    "name": "浙江省温州市鹿城区浙江温州化工总厂",
                    "address": "浙江省温州市鹿城区浙江温州化工总厂", //地址
                    "lng": 120.579412, //经度
                    "lat": 28.024421 //纬度
                }
            },
            "consignees": [ //收货方信息
                {
                    "name": "收货方",
                    "phone": "15161128126",
                    "address": {
                        "province": "浙江省",
                        "cityCode": "",
                        "city": "杭州市",
                        "district": "淳安县",
                        "name": "浙江省杭州市淳安县绿城千岛湖喜来登度假酒店",
                        "address": "浙江省杭州市淳安县绿城千岛湖喜来登度假酒店",
                        "lng": 119.039414,
                        "lat": 29.608042
                    }
                }
            ],
            "cargo": {
                "name": "货物1", //货物名字，取第一个货物的名字
                "quantity": 3.0, //货物总数量
                "weight": 5.0, //货物总重量
                "volume": 7.0, //货物总体积
                "productModel": "货物1备注", //货物备注
                "note1": "货物1备注1", //货物自定义备注1
                "note2": "货物1备注2", //货物自定义备注2
                "note3": "货物1备注3", //货物自定义备注3
                "note4": "", //货物自定义备注4
                "note5": "", //货物自定义备注5
                "note6": "", //货物自定义备注6
                "value": 9.0, //货值
            },
            "totalCargoes": 2, //货物总数量
            "settlementParty": 1, //结算方 1:发货方 2:收货方
            "freightIn": { //上游运费
                "payType": 1, //上游费用支付方式， 1现付，2到付，3回付，4周结，5月结
                "amount": 11 //上游费用
            },
            "freightOut": { //司机运费
                "payType": 5, //上游费用支付方式， 1现付，2到付，3回付，4周结，5月结
                "amount": 12 //司机费用
            },
            "totalFreightIn": 11.0, //总上游费用
            "freightReceived": null, //已收费用
            "freightUnreceived": 11.0, //未收费用
            "freightCollect": null, //代收运费
            "freightCollectReceived": null, //已收代收运费
            "freightCollectUnReceived": 0.0, //未收代收运费
            "paymentCollect": null, //代收货款
            "paymentCollectReceived": null, //已收代收货款
            "paymentCollectUnReceived": 0.0, //未收代收货款
            "needReceipt": 1, //是否需要回单
            "receiptCount": 1, //回单数量
            "note": "运单备注", //运单备注
            "extraFields": {
                "uppay1": "", // 上游自定义运费1
                "uppay2": "", // 上游自定义运费2
                "uppay3": "", // 上游自定义运费3
                "uppay4": "", // 上游自定义运费4
                "uppay5": "", // 上游自定义运费5
                "uppay6": "", // 上游自定义运费6
                "pay1": "", // 司机自定义运费1
                "pay2": "", // 司机自定义运费2
                "pay3": "", // 司机自定义运费3
                "pay4": "", // 司机自定义运费4
                "pay5": "", // 司机自定义运费5
                "pay6": "", // 司机自定义运费6
                "note1": "", // 自定义备注1
                "note2": "", // 自定义备注2
                "note3": "", // 自定义备注3
                "note4": "", // 自定义备注4
                "note5": "", // 自定义备注5
                "note6": "", // 自定义备注6
                "note7": "", // 自定义备注7
                "note8": "", // 自定义备注8
                "note9": "", // 自定义备注9
                "note10": "", // 自定义备注10
                "note11": "", // 自定义备注11
                "note12": "" // 自定义备注12
            },
            "option1": null, //自定义选项1
            "option2": null, //自定义选项2
            "option3": null, //自定义选项3
            "organizationPath": "0", //所属组织机构的path字段(不是名字)，具体请参考常见问题指南
            "dispatchInfo": { //调度信息
                "driverPhone": null, //司机电话
                "driverUids": [], //司机列表
                "gids": [], //车队列表
                "carMode": null, //车型
                "orderCount": 1, //生成订单数量
                "shouldNotifyDriver": false, //是否给司机发动提醒
                "needDriverAgree": false, //是否需要司机同意，默认否(只有一个订单时有效)
                "driverTags": null, //司机标签
                "vehicleTagIds": null //车辆标签
            },
            "batchId": null, //批量导入的批次id
            "createUid": "5bc725b6e4b07d20a861600f", //开单人
            "source": 1, //订单来源，1手工录入，2标准导入，4接口导入
            "state": 2000, //状态  0:"已撤销" 1000:"待处理" 2000:"已发布"
            "parentOrderId": null, //父订单id
            "splitOrderId": null, //拆分源订单
            "planNumber": null, //任务计划的编号
            "omsNumber": null, //受理单号
            "packNumber": "P1901255BCE400F0001", //车次号
            "waybillState": 2, //运单状态，state为2000时才会有值，1已下单，2已接单，3已装货，4已签收
            "dispatchDriver": { //司机信息
                "uid": "5c4a7f86e4b0f2d798da543e", //司机账号的id
                "username": "司机姓名", //名字
                "phoneNumber": "13872897189", //电话
                "carNumber": "浙A92874", //车牌号
                "carMode": 1, //车型
                "carDetailMode": 0, //详细车型
                "passType": 0, //通行证类型 0:未指定 1:邮政通 2:绿通 3:全市通 4:三环通 5:江南通 6:江北通
                "passTypeValue": "" //通行证
            },
            "evaluate": null, //评价
            "miles": 342, //预估里程
            "openTime": null, //开单时间
            "publishTime": 1548407457, //发布时间
            "receiveTime": 1548407457, //接收时间
            "shipmentTime": 1548407457, //装货时间
            "signedTime": 1548407457, //签收时间
            "receiptCallbackTime": 1548407457, //回单回收时间
            "receiptSendOutTime": 1548407457, //回单发放时间
            "evaluateTime": 1548407457, //评价时间
            "receiptStatus": null, //回单状态  回单已回收,回单已发放
            "receiptUploaded": null, //回单是否已上传
            "settlementStatus": null, //运费状态 
            "freightCollectStatus": null, //代收运费状态 0:未收取 1:已收取 2:已核销 3:部分收取 99:所有
            "collectionAmountStatus": null, //代收货款状态 0:未收取 1:已收取 2:已核销 3:部分收取 99:所有
            "orderSendType": 1, //订单指派方式 1：指派 2：抢单P
            "orderPrintStatus": null, //订单打印状态 1：已打印
            "tipsPrintStatus": null, //订单标签打印状态 1：已打印
            "segmentNumber": null, //分段number
            "segmentType": null, //分段类型 0:提货,5:提货到外转方,1:中转,2:直送,3:外转直送,4:外转中继
            "segmentReceiveOrganizeidPath": null, //分段收货方组织机构
            "freezeDeliveryTime": null, //继承提货时间
            "freezeAppointArriveTime": null, //继承预约到达时间
            "freezeStartAddress": null, //继承起始地
            "freezeEndAddress": null, //继承目的地
            "freezePaymentCollect": null, //继承代收货款
            "abnormal": null, //异常标记，布尔值，为空则没有异常
            "abnormal_dispose_status": null, //异常处理标记，布尔值，为空则没有异常
            "deliveryAddress": null, //装货地址
            "signAddress": null, //签收地址
            "onlinePayState": null, //在线支付状态 1支付中，2支付成功
            "onlinePayment": null, //在线支付金额
            "transactionId": null, //交易流水号
            "isDelete": null, //是否删除 1为删除
            "created": 1548407393, //订单创建时间
            "updated": 1548407458, //订单更新时间
            "startAddressLng": null, //起点经度
            "startAddressLat": null, //起点纬度
            "endAddressLng": null, //终点经度
            "endAddressLat": null, //终点纬度
            "financeCollectFixedTime": null, //代收货款核销时间
            "freightCollectFixedTime": null, //代收运费核销时间
            "apportionFee": null, //车次分摊费用
            "checkPickUpAlarm": null, //提货超时是否检查：1：检查过
            "checkDeliverAlarm": null, //送货超时是否检查：1：检查过
            "onlinePay": false, //是否在线支付
            "cargoes": [
                {
                    "id": "5d2c3616b16e6300102d3b3e",
                    "uid": "5d2bd68ae4b0dc3282ebe13e",//主账号id
                    "ttmsOrderId": "5d2c3616b16e6300102d3ab8",//运单id
                    "name": "MacBook Pro", //货物名称
                    "quantity": 8.0, //数量
                    "weight": 2.0, //质量
                    "volume": 3.0, //体积
                    "value": 468.89, //货物价值
                    "productModel": "", //备注
                    "note1": "", //自定义备注1
                    "note2": "", //自定义备注2
                    "note3": "", //自定义备注3
                    "note4": "", //自定义备注4
                    "note5": "", //自定义备注5
                    "note6": "", //自定义备注6
                    "created": 1563178517 //创建时间
                }
            ]
        }
    ]
}
```

- 调用失败示例

```java
{
	"status": 500,
	"message": ""
}
```

## 批量查询订单接口

**简要描述：** 批量查询订单，不包含详细的货物信息

**请求 URL：** `/order/query_orders`

**请求方式：** POST, GET

**需要认证：** 是

**调用频率限制：** 一小时内最多调用一万次，超过会提示操作频繁

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|
| `page` | 是 | `int` | 页码，1开始 |
| `size` | 是 | `int` | 单页最大订单数 |
| `state` | 否 | `int` | 订单状态，0已撤销，1已下单，2已接单，3已装货，4已签收，1000待处理，无法查看全部状态，不传则默认0已撤销|
| `timeType` | 否 | `string` | 查询时间类型，created录入时间，deliveryed提货时间，appointArrived预约提货时间，signed签收时间 |
| `startDate` | 否 | `string` | 起始时间，格式"yyyy-MM-dd HH:mm:ss" |
| `endDate` | 否 | `string` | 结束时间，格式"yyyy-MM-dd HH:mm:ss" |
| `orderNumber` | 否 | `string` | TMS运单号 |
| `customerOrderNumber` | 否 | `string` | 客户单号 |
| `packNumber` | 否 | `string` | 车次号 |
| `consignerName` | 否 | `string` | 发货人姓名，模糊搜索 |
| `consignerPhone` | 否 | `string` | 发货人电话，模糊搜索 |
| `consigneeName` | 否 | `string` | 收货人姓名，模糊搜索 |
| `consigneePhone` | 否 | `string` | 收货人电话，模糊搜索 |
| `driverName` | 否 | `string` | 司机姓名，模糊搜索 |
| `driverPhone` | 否 | `string` | 司机电话，模糊搜索 |
| `carNumber` | 否 | `string` | 司机车牌号码，模糊搜索 |

**返回示例**

- 调用成功示例

```java
{
    "code": 200,
    "message": null,
    "data": {
        "page": 1,
        "size": 50,
        "total": 100,
        "elements": [
            {
                "id": "5c4ad2619c023a001044079a", //订单id
                "uid": "5bc725b6e4b07d20a861600f", //主账号uid
                "number": "1901251709800228", //运单号
                "wmsNumber": null, //wmsNumber，即创建订单时的orderNumber
                "wmsLocation": null, //集货位
                "operator": "5bc725b6e4b07d20a861600f", //操作人uid
                "createUserId": "15161181167", //创建人手机号
                "createUsername": "gmw", //创建人姓名
                "deliveryTime": 1548669600, //提货时间，秒为单位的时间戳
                "deliveryType": null, //提送类型 1, "自提"  2, "送货"
                "appointArriveTime": 1548980160, //预约送达时间，秒为单位的时间戳
                "customerOrderNumber": "JSOUT1234567", //客户单号
                "startAddress": "杭州", //起始地址
                "endAddress": "千岛湖", //目的地址
                "consigner": { //发货方信息
                    "name": "发货方", //发货人姓名
                    "phone": "15161151543", //发货人手机
                    "address": { //发货人地址相关信息
                        "province": null, //省
                        "cityCode": null, //城市代码
                        "city": null, //城市
                        "district": null, //区
                        "name": "浙江省温州市鹿城区浙江温州化工总厂",
                        "address": "浙江省温州市鹿城区浙江温州化工总厂", //地址
                        "lng": 120.579412, //经度
                        "lat": 28.024421 //纬度
                    }
                },
                "consignees": [ //收货方信息
                    {
                        "name": "收货方",
                        "phone": "15161128126",
                        "address": {
                            "province": null,
                            "cityCode": null,
                            "city": null,
                            "district": null,
                            "name": "浙江省杭州市淳安县绿城千岛湖喜来登度假酒店",
                            "address": "浙江省杭州市淳安县绿城千岛湖喜来登度假酒店",
                            "lng": 119.039414,
                            "lat": 29.608042
                        }
                    }
                ],
                "cargo": {
                    "id": null, //货物id
                    "uid": null, //创建人id
                    "name": "货物1", //货物名字，取第一个货物的名字
                    "quantity": 3.0, //货物总数量
                    "weight": 5.0, //货物总重量
                    "volume": 7.0, //货物总体积
                    "productModel": "货物1备注", //货物备注
                    "note1": "货物1备注1", //货物自定义备注1
                    "note2": "货物1备注2", //货物自定义备注2
                    "note3": "货物1备注3", //货物自定义备注3
                    "note4": "", //货物自定义备注4
                    "note5": "", //货物自定义备注5
                    "note6": "", //货物自定义备注6
                    "value": null, //货值
                    "consignerPhone": null, //发货人手机号
                    "consigneePhones": null, //收货人手机号
                    "created": null, //创建货物时间
                    "updated": null //更新货物数据时间
                },
                "totalCargoes": 2, //货物总数量
                "settlementParty": 1, //结算方 1:发货方 2:收货方
                "freightIn": { //上游运费
                    "payType": 1, //上游费用支付方式， 1现付，2到付，3回付，4周结，5月结
                    "amount": 11 //上游费用
                },
                "freightOut": { //司机运费
                    "payType": 5, //上游费用支付方式， 1现付，2到付，3回付，4周结，5月结
                    "amount": 12 //司机费用
                },
                "totalFreightIn": 11, //总上游费用
                "freightReceived": null, //已收费用
                "freightUnreceived": 11, //未收费用
                "freightCollect": null, //代收运费
                "freightCollectReceived": null, //已收代收运费
                "freightCollectUnReceived": 0, //未收代收运费
                "paymentCollect": null, //代收货款
                "paymentCollectReceived": null, //已收代收货款
                "paymentCollectUnReceived": 0, //未收代收货款
                "needReceipt": 1, //是否需要回单
                "receiptCount": 1, //回单数量
                "note": "运单备注", //运单备注
                "extraFields": {
                    "uppay1": "", // 上游自定义运费1
                    "uppay2": "", // 上游自定义运费2
                    "uppay3": "", // 上游自定义运费3
                    "uppay4": "", // 上游自定义运费4
                    "uppay5": "", // 上游自定义运费5
                    "uppay6": "", // 上游自定义运费6
                    "pay1": "", // 司机自定义运费1
                    "pay2": "", // 司机自定义运费2
                    "pay3": "", // 司机自定义运费3
                    "pay4": "", // 司机自定义运费4
                    "pay5": "", // 司机自定义运费5
                    "pay6": "", // 司机自定义运费6
                    "note1": "", // 自定义备注1
                    "note2": "", // 自定义备注2
                    "note3": "", // 自定义备注3
                    "note4": "", // 自定义备注4
                    "note5": "", // 自定义备注5
                    "note6": "", // 自定义备注6
                    "note7": "", // 自定义备注7
                    "note8": "", // 自定义备注8
                    "note9": "", // 自定义备注9
                    "note10": "", // 自定义备注10
                    "note11": "", // 自定义备注11
                    "note12": "" // 自定义备注12
                },
                "option1": null, //自定义选项1
                "option2": null, //自定义选项2
                "option3": null, //自定义选项3
                "organizationPath": "0", //所属组织机构的path字段(不是名字)，具体请参考常见问题指南
                "dispatchInfo": { //调度信息
                    "driverPhone": null, //司机电话
                    "driverUids": [], //司机列表
                    "gids": [], //车队列表
                    "carMode": null, //车型
                    "orderCount": 1, //生成订单数量
                    "shouldNotifyDriver": false, //是否给司机发动提醒
                    "needDriverAgree": false, //是否需要司机同意，默认否(只有一个订单时有效)
                    "driverTags": null, //司机标签
                    "vehicleTagIds": null //车辆标签
                },
                "batchId": null, //批量导入的批次id
                "createUid": "5bc725b6e4b07d20a861600f", //开单人
                "source": 1, //订单来源，1手工录入，2标准导入，4接口导入
                "state": 2000, //状态  0:"已撤销" 1000:"待处理" 2000:"已发布"
                "parentOrderId": null, //父订单id
                "splitOrderId": null, //拆分源订单
                "planNumber": null, //任务计划的编号
                "omsNumber": null, //受理单号
                "packNumber": "P1901255BCE400F0001", //车次号
                "waybillState": 2, //运单状态，state为2000时才会有值，1已下单，2已接单，3已装货，4已签收
                "dispatchDriver": { //司机信息
                    "uid": "5c4a7f86e4b0f2d798da543e", //司机账号的id
                    "username": "司机姓名", //名字
                    "phoneNumber": "13872897189", //电话
                    "carNumber": "浙A92874", //车牌号
                    "carMode": 1, //车型
                    "carDetailMode": 0, //详细车型
                    "passType": 0, //通行证类型 0:未指定 1:邮政通 2:绿通 3:全市通 4:三环通 5:江南通 6:江北通
                    "passTypeValue": "" //通行证
                },
                "evaluate": null, //评价
                "miles": 342, //预估里程
                "openTime": 1548407457, //开单时间
                "publishTime": 1548407457, //发布时间
                "receiveTime": 1548407457, //接收时间
                "shipmentTime": null, //装货时间
                "signedTime": null, //签收时间
                "receiptCallbackTime": null, //回单回收时间
                "receiptSendOutTime": null, //回单发放时间
                "evaluateTime": null, //评价时间
                "receiptStatus": null, //回单状态  回单已回收,回单已发放
                "receiptUploaded": null, //回单是否已上传
                "settlementStatus": null, //运费状态 
                "freightCollectStatus": null, //代收运费状态 0:未收取 1:已收取 2:已核销 3:部分收取 99:所有
                "collectionAmountStatus": null, //代收货款状态 0:未收取 1:已收取 2:已核销 3:部分收取 99:所有
                "orderSendType": 1, //订单指派方式 1：指派 2：抢单P
                "orderPrintStatus": null, //订单打印状态 1：已打印
                "tipsPrintStatus": null, //订单标签打印状态 1：已打印
                "segmentNumber": null, //分段number
                "segmentType": null, //分段类型 0:提货,5:提货到外转方,1:中转,2:直送,3:外转直送,4:外转中继
                "segmentReceiveOrganizeidPath": null, //分段收货方组织机构
                "freezeDeliveryTime": null, //继承提货时间
                "freezeAppointArriveTime": null, //继承预约到达时间
                "freezeStartAddress": null, //继承起始地
                "freezeEndAddress": null, //继承目的地
                "freezePaymentCollect": null, //继承代收货款
                "abnormal": null, //异常标记
                "abnormal_dispose_status": null, //异常处理标记
                "deliveryAddress": null, //装货地址
                "signAddress": null, //签收地址
                "onlinePayState": null, //在线支付状态 1 支付中，2支付成功
                "onlinePayment": null, //在线支付金额
                "transactionId": null, //交易流水号
                "isDelete": null, //是否删除 1为删除
                "created": 1548407393, //订单创建时间
                "updated": 1548407458, //订单更新时间
                "startAddressLng": null, //起点经度
                "startAddressLat": null, //起点纬度
                "endAddressLng": null, //终点经度
                "endAddressLat": null, //终点纬度
                "financeCollectFixedTime": null, //代收货款核销时间
                "freightCollectFixedTime": null, //代收运费核销时间
                "apportionFee": null, //车次分摊费用
                "checkPickUpAlarm": null, //提货超时是否检查：1：检查过
                "checkDeliverAlarm": null, //送货超时是否检查：1：检查过
                "onlinePay": false //是否在线支付
            }
        ]
    }
}
```

- 调用失败示例

```java
{
	"status": 500,
	"message": ""
}
```

## 修改订单接口

**简要描述：** 修改订单，未传递的字段以及值为null的值不进行修改；收货人信息以及货物信息为List类型，修改时会覆盖原本的信息，所以需要将原本的信息和修改的信息合并后进行传递，如果不修改此信息请传递null，如果传递空List会将该信息清空。受理单分段管理中的运单信息继承自受理单，请使用[更新受理单接口](#更新受理单接口)修改

**请求 URL：** `/order/modify_order`

**请求方式：** POST

**需要认证：** 是

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|
| `orderNumber` | 是 | String | 订单号 |
| `order` | 是 | [ModifyOrderEntity](#修改运单参数说明) | 修改运单参数，具体内容点击类型进行查看 |

**返回示例**

- 调用成功示例

```java
{
    "code": 200,
    "message": null,
    "data": true
}
```
- 调用失败示例

```java
{
    "message": "订单号必填",
    "status": 500
}
{
    "message": "订单xxx不存在",
    "status": 500
}
```

## 撤销订单接口

**简要描述：** 批量撤销订单，撤销的订单会进入回收站中。只有状态为：待处理，已下单，已接单的运单可以撤销

**请求 URL：** `/order/cancel_orders/v2`

**请求方式：** POST, GET

**需要认证：** 是

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|
| `numbers` | 是 | `string` | 订单number列表，多个订单用','隔开 |

**返回示例**

```java
{
    "code": 200,
    "message": null
}
```
- 调用失败示例

```java
{
    "status": 500,
    "message": "撤销订单失败原因"
}
```

## 订单货物类接口

### 追加订单货物接口

**简要描述：** 追加订单货物，请使用[修改订单接口](#修改订单接口)

**请求 URL：** `/cargo/add`

**请求方式：** POST

**需要认证：** 是

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|
| `orderNumber` | 是 | `String` | 订单号，客户单号或wms单号  |
| `cargoNumber` | 是 | `String` | 货物号  |
| `weight` | 否 | `String` | 重量  |
| `volume` | 否 | `String` | 体积  |
| `quantity` | 否 | `String` | 件数  |
| `value` | 否 | `String` | 货值  |
| `name` | 否 | `String` | 货物名称  |
| `productModel` | 否 | `String` | 货物备注  |

**返回示例**

- 调用成功示例

```java
{
    "code": 200,
    "message": null
}
```
- 调用失败示例

```java
{
    "status": 500,
    "message": "创建失败"
}
```

### 修改订单货物接口

**简要描述：** 修改订单货物，请使用[修改订单接口](#修改订单接口)

**请求 URL：** `/cargo/update`

**请求方式：** POST

**需要认证：** 是

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|
| `cargoNumber` | 是 | `String` | 货物号  |
| `weight` | 否 | `String` | 重量  |
| `volume` | 否 | `String` | 体积  |
| `quantity` | 否 | `String` | 件数  |
| `value` | 否 | `String` | 货值  |
| `name` | 否 | `String` | 货物名称  |
| `productModel` | 否 | `String` | 货物备注  |

**返回示例**

- 调用成功示例

```java
{
    "code": 200,
    "message": null
}
```
- 调用失败示例

```java
{
    "status": 500,
    "message": "创建失败"
}
```


### 删除订单货物接口

**简要描述：** 删除订单货物，请使用[修改订单接口](#修改订单接口)

**请求 URL：** `/cargo/remove`

**请求方式：** POST

**需要认证：** 是

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|
| `cargoNumber` | 是 | `String` | 货物号  |

**返回示例**

- 调用成功示例

```java
{
    "code": 200,
    "message": "true"
}
```
- 调用失败示例

```java
{
    "status": 500,
    "message": "false"
}
```

# 车次类接口

## 创建车次接口

**简要描述：** 开单并创建车次

**请求 URL：** `/order/create_order_pack`

**请求方式：** POST

**需要认证：** 是

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|
| `orderList` | 是 | Array[[OrderEntity](#运单参数说明)] | 运单列表，具体内容点击类型进行查看 |
| `driverPhone` | 否 | `string` | 司机电话 |

**返回示例**

- 调用成功示例

```java
{
    "code":200,
    "data": {
        "numbers":["1712051703640558"], // 创建运单号
        "ids":["5a2660f3d109770010026df9"], // 运单id
        "packNumber":"P171205558E431E0001" // 车次号
    }
}
```
- 调用失败示例

```java
{
    "status": 500,
    "message": "订单车次失败"
}
```

# 订阅类接口

## 订单订阅接口

**简要描述：** 订单订阅，请先阅读 常见问题 !!!

**请求 URL：** `/order/subscribe/v2`

**请求方式：** POST

**需要认证：** 是

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|
| `states` | 是 | `String` | 需要订阅的订单状态，0：已撤销(对应TMS系统中的操作为已下单、已接单状态时的撤销运单)，1：已下单，2：已接单，3：已装货，4：已签收，210：重新指派，8000：运单打印，8001：运单标签打印，8002：异常上报；支持多选，多个状态之间用','隔开  |
| `callbackUrl` | 是 | `String` | 回调地址，以http://或https://开头，支持每个用户使用不同的回调地址 |
| `version` | 是 | `String` | v1，暂无其他版本 |


**返回示例**

- 调用成功示例

```java
{
    "code": 200,
    "message": null
}
```
- 调用失败示例

```java
{
    "status": 500,
    "message": ""
}
```

- 订单订阅返回报文：
```java
{
    "number ": "1609171412804505", /*订单号*/
    "wmsNumber": "wmsNumber", /*出库单号，值为创建订单时的orderNumber*/
    "customerOrderNumber": "111111", /*客户单号*/
    "packNumber": "P20170805094004f32c20dd", /*车次号*/
    "remark": "xx 订单已签收", /*订单日志*/
    "state": 1, /*订单状态*/
    "subscribeState": 1, /*订阅的状态*/
    "driver": "某司机", /*司机名称*/
    "deliveryType": 1, /*提送类型，null：未指定，1：自提，2：送货*/
    "carNumber": "浙A12345", /*车牌号码*/
    "phoneNumber": "13812345678", /*司机电话*/
    "groupName": "xx运输队", /*车队*/
    "receiptUrls": ["http://oss.kuaihuoyun.com/1.png", "http://oss.kuaihuoyun.com/2.png"], /*回单照片*/
    "signer": "xxx", /*签收人，该字段订单签收时才会有*/
    "messageTimeStamp": 1565595441, /*消息生成时的时间戳，精确到秒*/
    /*运单异常信息，该信息仅在订阅8002时返回*/
    "orderAbnormalInfo": {
        "info": "异常内容：详细描述",
        "orderId": "5d2586f8e21f65001158106e", //运单id
        "orderNumber": "1907101434753075", //运单号
        "orderType": 1, //1 - 运单
        "profile": "异常类型：简述",
        "source": 2, //1 - 人工创建, 2 - 司机上报, 3 - 系统自动
        "type": "装货异常", //异常阶段：装货异常，签收异常，在途异常
        "imageUrls": ["http://oss.kuaihuoyun.com/driverXXXXX.jpg"], //司机上报图片地址
        "address": { //上报位置信息
            "address": "浙江省杭州市西湖区古荡巷220靠近浙江省国家大学科技园中国计量学院分园",
            "lng": 120.125546,
            "name": "浙江省杭州市西湖区古荡巷220靠近浙江省国家大学科技园中国计量学院分园",
            "lat": 30.27815
        }
    }
}

/*订阅8000时的回调结果*/
{
    "orderNumbers": [
        "1906281634405579",
        "1906281634405921",
        .....
    ],
    "printType": "运单打印"
}

/*订阅8001时的回调结果*/
{
    "orderNumbers": [
        "1906281634405579",
        .....
    ],
    "printType": "运单标签打印"
}
```

## 取消订单订阅接口

**简要描述：** 取消订单订阅

**请求 URL：** `/order/unsubscribe`

**请求方式：** POST

**需要认证：** 是

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|

**返回示例**

- 调用成功示例

```java
{
    "code": 200,
    "message": null
}
```
- 调用失败示例

```java
{
    "status": 500,
    "message": ""
}
```

## 车次订阅接口

**简要描述：** 车次订阅，请先阅读 常见问题 !!!

**请求 URL：** `/order/orderPack/subscribe`

**请求方式：** POST

**需要认证：** 是

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|
| `states` | 是 | `String` | 需要订阅的车次状态，19000：删除/撤销车次，40000：指派车次，40001：更新车次；支持多选，多个状态之间用','隔开  |
| `callbackUrl` | 是 | `String` | 回调地址，以http://或https://开头，支持每个用户使用不同的回调地址 |


**返回示例**

- 调用成功示例

```java
{
    "code": 200,
    "message": null
}
```
- 调用失败示例

```java
{
    "status": 500,
    "message": ""
}    
```

- 车次订阅返回报文：

```java
{
    "carNumber": "浙WL9987", /*车牌号码*/
    "groupName": "白云仓车队", /*车队*/
    "orderNumbers": ["1903281059996382"], /*tms车次订单集合*/
    "wmsNumbers": ["D19010300015"], /*出库单号集合，值为创建订单时的orderNumber*/
    "driver": "浮夸", /*司机名称*/
    "createTime": "2019-03-28 11:08:32", /*tms车次创建时间*/
    "remark": "", /*备注*/
    "driverPhone": "19011111111", /*司机电话*/
    "state": 40000, /*19000：删除/撤销车次，40000：指派车次，40001：更新车次*/
    "subscribeState": 19000, /*订阅的状态*/
    "messageTimeStamp": 1565595441, /*消息生成时的时间戳，精确到秒*/
    "packNumber": "P190328563E48420011", /*tms车次号*/
    "customerOrderNumbers": ["D19010300015"] /*客户单号集合*/
}
```

## 取消车次订阅接口

**简要描述：** 取消车次订阅

**请求 URL：** `/order/orderPack/unsubscribe`

**请求方式：** POST

**需要认证：** 是

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|

**返回示例**

- 调用成功示例

```java
{
    "code": 200,
    "message": null
}
```
- 调用失败示例

```java
{
    "status": 500,
    "message": ""
}
```

## 受理单订阅接口

**简要描述：** 受理单订阅，请先阅读 常见问题 !!!

**请求 URL：** `/customer_order/subscribe`

**请求方式：** POST

**需要认证：** 是

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|
| `states` | 是 | `String` | 600:货物追踪；601:受理单签收；602(需要`xhkID`):受理单绑定的小黑卡轨迹点上报。多个状态之间用','隔开  |
| `callbackUrl` | 是 | `String` | 回调地址，以http://或https://开头，支持每个用户使用不同的回调地址 |
| `xhkID` | 是 | `String` | 小黑卡公司id，由我方提供，部分订阅状态需要传递此参数 |


**返回示例**

- 调用成功示例

```java
{
    "code": 200,
    "message": null
}
```
- 调用失败示例

```java
{
    "status": 500,
    "message": "xxx"
}    
```

- 受理单订阅返回报文：

```java
/*订阅600时的回调结果*/
{
    "messageTimeStamp": 1573699009, /*消息生成时的时间戳，精确到秒*/
    "trackContent": "已办理外转", /*货物追踪内容*/
    "transferOrderNumber": "W1911145D9E467C0006", /*外传单号*/
    "originalOrderNumber": "0809496759", /*客户单号*/
    "subscribeState": 600, /*订阅的状态*/
    "customerOrderNumber": "S1911141034952066", /*受理单号*/
    "orderState": 2000 /*受理单状态，0:已撤销 1000:待处理 2000:进行中 3000:已完成*/
}

/*订阅601时的回调结果*/
{
    "customerOrderNumber": "S1910111512348435", /*受理单号*/
    "isFinished": true, /*受理单是否完成*/
    "arrivedTime": 1571971794, /*到达时间，时间戳，精确到秒*/
    "lastSignTime": 1571971794, /*最后一个分段的签收时间，时间戳，精确到秒*/
    "orderState": 3000, /*受理单状态*/
    "subscribeState": 601, /*订阅的状态*/
    "messageTimeStamp": 1571971799 /*消息生成时的时间戳，精确到秒*/
}

/*订阅602时的回调结果*/
{
    "customerOrderNumbers": ["S1910181834038713"], /*受理单号列表*/
    "messageTimeStamp": 1572329191, /*消息时间戳，单位：秒*/
    "subscribeState": 602, /*订阅的状态*/
    /*定位信息*/
    "gpsInfo": {
        "device": "868120223404879", /*设备号*/
        "direction": 0, /*方向*/
        "gpsTime": 1572329163, /*定位时间*/
        "humidity": 58, /*湿度*/
        "temperature": 23, /*温度*/
        "lat": 22.5739258, /*纬度*/
        "lng": 113.9215763, /*经度*/
        "locateType": 2, /*轨迹上报类型：(0：未知，1：GPS，2：基站定位，4：北斗定位，5：GPS 和北斗定位)*/
        "location": "广东省 深圳市 宝安区 留仙一路", /*定位地址*/
        "powerRate": 0, /*电池电量*/
        "chargerState": 0, /*充电状态，0：未充电，1：充电中*/
        "province": "广东省", /*省*/
        "city": "深圳市", /*市*/
        "district": "宝安区", /*区*/
        "roadName": "广东省 深圳市 宝安区 留仙一路", /*街道地址*/
        "runStatus": 1, /*设备运行状态（1:行驶，2:停止，3:离线）*/
        "speed": 0 /*速度*/
    }
}
```

## 取消受理单订阅接口

**简要描述：** 取消受理单订阅

**请求 URL：** `/customer_order/unsubscribe`

**请求方式：** POST

**需要认证：** 是

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|

**返回示例**

- 调用成功示例

```java
{
    "code": 200,
    "message": null
}
```
- 调用失败示例

```java
{
    "status": 500,
    "message": ""
}
```

# 受理单类接口

## 创建受理单接口

**简要描述：** 受理开单

**请求 URL：** `/customer_order/create_customer_order`

**请求方式：** POST

**需要认证：** 是

**调用限制：** 批量创建受理单数一次性不得大于100

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|
| `orders` | 是 | Array[[CustomerOrderEntity](#受理单参数说明)] | 受理单列表，具体内容点击类型进行查看 |

**返回示例**

- 调用成功示例

调用成功但是系统中查看不到时请先阅读 常见问题 
```java
{
    "code": 200,
    "data": ["S1711151843619482"],
    "message": null
}
```
- 调用失败示例

```java
{
    "status": 500,
    "message": "受理单创建失败"
}
```

## 更新受理单接口

**简要描述：** 修改受理单接口，没有传递的参数值将被清空

**请求 URL：** `/customer_order/update_customer_order`

**请求方式：** POST

**需要认证：** 是

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|
| `number` | 是 | `string` | 受理单号 |
| `order` | 是 | [CustomerOrderEntity](#受理单参数说明) | 受理单，具体内容点击类型进行查看 |

**返回示例**

- 调用成功示例

```java
{
    "code": 200,
    "data": null,
    "message": null
}
```
- 调用失败示例

```java
{
    "status": 500,
    "message": "受理单创建失败"
}
```


## 批量查询受理单接口

**简要描述：** 批量查询受理单

**请求 URL：** `/customer_order/query_customer_orders`

**请求方式：** POST, GET

**需要认证：** 是

**调用频率限制：** 一小时内最多调用一万次，超过会提示操作频繁

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|
| `page` | 是 | `int` | 页码，1开始 |
| `size` | 是 | `int` | 单页最大订单数 |
| `state` | 否 | `int` | 受理单状态，0已撤销，1000待处理，2000进行中，3000已完成，不传则查询全部状态|
| `number` | 否 | `string` | 受理单号 |
| `originalOrderNumber` | 否 | `string` | 客户单号 |
| `timeType` | 否 | `string` | 查询时间类型，created录入时间，deliveryed提货时间，appointArrived预约提货时间，signed签收时间 |
| `startDate` | 否 | `string` | 起始时间，格式"yyyy-MM-dd HH:mm:ss" |
| `endDate` | 否 | `string` | 结束时间，格式"yyyy-MM-dd HH:mm:ss" |
| `deviceNumber` | 否 | `string` | 设备号 |
| `consignerName` | 否 | `string` | 发货人姓名，模糊搜索 |
| `consignerPhone` | 否 | `string` | 发货人电话，模糊搜索 |
| `consignerAddress` | 否 | `string` | 发货人地址，模糊搜索 |
| `consigneeName` | 否 | `string` | 收货人姓名，模糊搜索 |
| `consigneePhone` | 否 | `string` | 收货人电话，模糊搜索 |
| `consigneeAddress` | 否 | `string` | 收货人地址，模糊搜索 |
| `organizationPaths` | 否 | `list` | 组织机构 |

**返回示例**

- 调用成功示例

```java
{
    "code": 200,
    "message": null,
    "data": {
        "page": 1,
        "size": 10,
        "total": 11,
        "elements": [
            {
                "order": {
                    "id": "5ab88c0d4b67620010302f58",
                    "uid": "558a2084e4b0ddab858a031e", // 用户id
                    "createUid": "558a2084e4b0ddab858a031e", // 制单人id
                    "createUserId": "15657103156", // 制单人账号
                    "createUsername": "冉涛12222221", // 制单人名称
                    "number": "S1803261358607938", // 受理单号
                    "originalOrderNumber": "112222", // 原始单号
                    "openTime": 1520377500, //开单时间
                    "deliveryTime": 1520377500, // 提货时间
                    "deliveryType": null, // 提送类型，1提货，2送货
                    "appointArriveTime": 1520283960, // 预约送达时间
                    "startAddress": "洛阳", // 起始地址
                    "endAddress": "郑州", // 目的地址
                    "consigner": { // 发货人
                        "name": "发货方",
                        "phone": "123456789",
                        "address": {
                            "province": null,
                            "cityCode": null,
                            "city": null,
                            "district": null,
                            "name": "浙江省杭州市西湖区计量大厦",
                            "address": "浙江省杭州市西湖区计量大厦",
                            "lng": 120.12564,
                            "lat": 30.277438
                        }
                    },
                    "consignee": { // 收货人
                        "name": "收货方",
                        "phone": "123456789",
                        "address": {
                            "province": null,
                            "cityCode": null,
                            "city": null,
                            "district": null,
                            "name": "江苏省无锡市滨湖区太湖鼋头渚风景区",
                            "address": "江苏省无锡市滨湖区太湖鼋头渚风景区",
                            "lng": 120.226687,
                            "lat": 31.52324
                        }
                    }, 
                    "cargo": { // 货物总计
                        "name": "MacBook Air", //货物名称
                        "quantity": 2.0, //件数
                        "weight": 3.0, //重量
                        "volume": 4.0, //体积
                        "value": 5.0, //货值
                        "remarks": "xxx", //备注
                        "note1": "7", // 货物自定义备注1
                        "note2": "8", // 货物自定义备注2
                        "note3": "", // 货物自定义备注3
                        "note4": "", // 货物自定义备注4
                        "note5": "", // 货物自定义备注5
                        "note6": "", // 货物自定义备注6
                    },
                    "freightIn": { // 上游运费
                        "payType": 7, //支付方式，1:"现付", 2:"到付", 3:"回付", 4:"周结", 
                                      //5:"月结", 6:"货款扣", 7:"季度结", 8:"在线支付", 9:"到付月结"
                        "amount": 10.2 //金额
                    },
                    "uppay1": null, // 上游自定义费用1
                    "uppay2": null, // 上游自定义费用2
                    "uppay3": null, // 上游自定义费用3
                    "uppay4": null, // 上游自定义费用4
                    "uppay5": null, // 上游自定义费用5
                    "uppay6": null, // 上游自定义费用6
                    "uppay7": null, // 上游自定义费用7
                    "uppay8": null, // 上游自定义费用8
                    "uppay9": null, // 上游自定义费用9
                    "uppay10": null, // 上游自定义费用10
                    "uppay11": null, // 上游自定义费用11
                    "uppay12": null, // 上游自定义费用12
                    "paymentCollect": 111, // 代收货款
                    "receiptCount": 1, // 回单数
                    "remarks": "备注", // 备注
                    "note1": null, // 自定义备注1
                    "note2": null, // 自定义备注2
                    "note3": null, // 自定义备注3
                    "note4": null, // 自定义备注4
                    "note5": null, // 自定义备注5
                    "note6": null, // 自定义备注6
                    "note7": null, // 自定义备注7
                    "note8": null, // 自定义备注8
                    "note9": null, // 自定义备注9
                    "note10": null, // 自定义备注10
                    "note11": null, // 自定义备注11
                    "note12": null, // 自定义备注12
                    "option1": null, // 自定义选项1
                    "option2": null, // 自定义选项2
                    "option3": null, // 自定义选项3
                    "createOrganizationPath": "0", // 开单组织机构
                    "ownerOrganizationPath": null, // 当前拥有者者组织机构
                    "assignOrganizationPaths": null, // 指派组织机构
                    "receiveOrganizationPath": null, // 接收方组织机构
                    "source": 1, // 来源 1手工录入，2批量导入，3客户下单，4接口导入
                    "batchNumber": null, // 导入批次号
                    "state": 1000, // 状态，1000待处理，2000进行中，3000已完成
                    "settlementParty": 1, // 上游运费结算方，1 发货人，2收货人
                    "settlementName": "发货方",//结算方名称
                    "settlementPhone": "18293819285",//结算方电话
                    "totalFreightIn": 111, // 上游总运费
                    "freightInReceived": null, //已收上游费用
                    "freightInUnreceived": 111, //未收费用
                    "freightInState": null, //上游运费收取状态
                    "freightInTime": null, //上游运费收取时间
                    "paymentCollectState": null, //代收货款状态
                    "paymentCollectReceived": null, //已收代收费用
                    "paymentCollectTime": null, //代收收取时间
                    "paymentCollectWriteoffTime": null, //代收核销时间
                    "customerOrderPrintStatus": null, //受理单打印状态 1：已打印，0：未打印
                    "customerOrderTipsPrintStatus": null, //受理单打印状态 1：已打印，0：未打印
                    "receiptState": null, //回单状态
                    "receiptCallbacker": null,//回单回收人
                    "receiptCallbackTime": null,//回单回收时间
                    "receiptSender": null,//回单发放人
                    "receiptSentTime": null,//回单发放时间
                    "publishTime": null, //下发时间
                    "firstSignTime": null, //第一段签收时间
                    "lastSignTime": null, //最后一段签收时间
                    "segmentOrderNumber": null, //分段运单/外转单号
                    "carrier": null, //当前承运人
                    "currentSegmentType": null, //0: 提货,1: 中转,2: 直送,3: 外转直送,4: 外转中继,5: 提货到外转方
                    "reachStation": null, //已到达站
                    "nextStation": null, //下一站
                    "mileage": null, //行驶里程
                    "mileageEstimated": 11, //预估里程
                    "lastUploadAddress": null, //上一次上传坐标信息
                    "lastUploadTime": null, //上一次上传时间
                    "bindDevices": [], //绑定过的设备
                    "currentBindDevice": null, //当前绑定设备
                    "settlementNumber": null, //结算单号
                    "writeoffSettlementNumber": null, //核销单号
                    "duration": null, //高德计算行驶时间(秒)
                    "durationEstimated": null, //高德计算预估时间(秒)
                    "estimatedArriveTime": null, //预计到达时间
                    "estimatedLeftMiles": null, //剩余里程
                    "departureTime": null, //出发时间
                    "departureTimeStatus": null, //提货时效，1:"提前", 2:"准时", 3:"延迟"
                    "arrivedTime": null, //到达围栏时间
                    "arrived": false, //是否达到
                    "arrivedTimeStatus": null, //到达时效，1:"提前", 2:"准时", 3:"延迟"
                    "bindStatusName": "未绑定", //绑定状态名称
                    "created": 1522043917, //创建时间
                    "updated": 1522043917, //更新时间
                    "salesman": "", //业务员
                    "salesmanPhone": null, //业务员电话
                    "finished": false, //是否已完成
                    "upPayTotal": 0, //自定义费用总和
                    "departured": false, //是否已出发
                    "bindStatusName": "未绑定" //绑定状态名称
                },
                "cargoes": [
                    {
                        "id": "5ab88c0d4b67620010302f59",
                        "uid": "558a2084e4b0ddab858a031e",
                        "customerOrderNumber": "S1803261358607938", //受理单号
                        "transferOrderNumber": null, //外转单号
                        "name": "MacBook Air", // 货物名称
                        "quantity": 2.0, // 数量
                        "weight": 3.0, // 重量
                        "volume": 4.0, // 体积
                        "value": 5.0, // 货值
                        "remarks": "xxx", // 备注
                        "note1": "7", // 货物自定义备注1
                        "note2": "8", // 货物自定义备注2
                        "note3": "", // 货物自定义备注3
                        "note4": "", // 货物自定义备注4
                        "note5": "", // 货物自定义备注5
                        "note6": "", // 货物自定义备注6
                        "created": 1522043917
                    }
                ]
            }
        ]
    }
}
```
- 调用失败示例

```java
{
    "status": 500,
    "message": ""
}
```


## 撤销受理单接口

**简要描述：** 批量撤销受理单

**请求 URL：** `/customer_order/cancel_customer_orders`

**请求方式：** POST, GET

**需要认证：** 是

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|
| `numbers` | 是 | `string` | 订单number列表，多个订单用','隔开 |

**返回示例**

```java
{
    "code": 200,
    "message": null
}
```
- 调用失败示例

```java
{
    "status": 500,
    "message": "撤销受理单失败原因"
}
```


## 批量解绑受理单设备

**简要描述：** 批量解绑受理单设备，

**请求 URL：** `/customer_order/batch_unbind_devices`

**请求方式：** POST, GET

**需要认证：** 是

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|
| `orders` | 是 | `Array ` | 受理单号列表 |

**返回示例**

```java
{
    "code": 200,
    "message": null,
    "data": {}
}
```
- 调用失败示例

1.受理单号列表中存在未绑定设备的受理单：
```java
{
    "message": "受理单S1811011025811886未绑定设备！",
    "status": 500
}
```

2.受理单查询不到，请确认受理单是否存在，或者是否使用主账号调用的接口：
```java
{
    "message": "受理单不存在！",
    "status": 500
}
```

# 其他接口

## 获取组织机构列表接口

**简要描述：** 获取组织机构列表

**请求 URL：** `/organization/list`

**请求方式：** POST

**需要认证：** 是

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|

**返回示例**

- 调用成功示例

```java
{
    "code": 200,
    "message": null,
    "data": [
        {
            "nodeId": 0, //机构节点id
            "name": "总部", //机构名
            "path": "0-0" //节点路径,如无特殊说明，其他接口中的组织机构字段均使用此字段值
        },
        {
            "nodeId": 11,
            "name": "网点1",
            "path": "0-11"
        },
        {
            "nodeId": 12,
            "name": "杭州网点2",
            "path": "0-12"
        }
    ]
}
```
- 调用失败示例

```java
{
    "status": 500,
    "message": ""
}
```


## 添加客户接口

**简要描述：** 在同一种客户类型中：如果客户电话已存在，则进行更新，否则进行创建。

**请求 URL：** `/customer/add_customers`

**请求方式：** POST

**需要认证：** 是

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
|:----:|:---:|:-----:|:-----:|
| `customers` | 是 | `Array[CustomerEntity]` | 客户列表 |

其中CustomerEntity结构如下:
```java
{
    "name": "", //客户名称:必填
    "phone": "", //客户电话:必填
    "address": "", //客户地址:必填
    "type": 1, //客户类型:必填 1)发货人，2)收货人
    "paymentType": 1, //支付方式:必填, 1)现付, 2)到付, 3)回付, 4)周结, 5)月结, 6)货款扣, 7)季度结, 8)在线支付, 9)到付月结
    "remark1": "", //备注1:非必填
    "remark2": "", //备注2:非必填
    "remark3": "" //备注3:非必填
}
```

**返回示例**

- 调用成功示例

```java
{
    "code":200,
    "message":null,
    "data": true
}
```
- 调用失败示例

```java
{
    "status": 500,
    "message": ""
}
```


# 部分参数说明

## 运单参数说明
OrderEntity结构如下:
```java
{
    "orderNumber": "", //用于唯一性检测，此字段不在系统中展示:必填
    "consignerAddress": "", //发货人地址:必填
    "consignerName": "", //发货人姓名:必填
    "consignerPhone": "", //发货人电话:必填
    "deliveryTime": 1573180245, //提货时间:时间戳,精确到秒:必填
    "deliveryType": 1, //提送类型:选填, 1)自提，2)送货
    "customerOrderNumber": "", //客户单号:选填
    "appointArriveTime": 1573180245, //预约送到时间:时间戳,精确到秒:选填
    "consigneeAddress": "", //收货人地址:可不填
    "consigneeCity": "", //收货人所在城市:可不填
    "consigneeDistrict": "", //收货人所在地区:可不填
    "consigneeName": "", //收货人姓名:可不填
    "consigneePhone": "", //收货人电话:可不填
    "consigneeProvince": "", //收货人所在省份:可不填
    "consignerCity": "", //发货人所在城市
    "consignerDistrict": "", //发货人所在地区:可不填
    "consignerProvince": "", //发货人所在省份:可不填
    "driverPay": 12.0, //司机运费:可不填
    "driverPayType": 1, //司机运费支付方式:可不填, 1)现付, 2)到付, 3)回付, 4)周结, 5)月结, 6)货款扣, 7)季度结, 8)在线支付, 9)到付月结
    "startAddress": "", //起始地:选填
    "endAddress": "", //目的地:选填
    "freightCollect": 12.0, //代收运费:可不填
    //发货方经纬度
    "consignerLocation": {
        "lng": "", //经度
        "lat": "" //纬度
    },
    //收货方经纬度
    "consigneeLocation": {
        "lng": "", //经度
        "lat": "" //纬度
    },
    "note": "", //备注:可不填
    "organizationPath": "0-11", //组织机构:可不填，具体请看常见问题中的组织机构相关内容
    "paymentCollect": 12.0, //代收货款:可不填
    "receiptCount": 1, //回单数量
    "shipperPay": 12.0, //上游运费:可不填
    "shipperPayType": 1, //上游运费支付方式:可不填, 1)现付, 2)到付, 3)回付, 4)周结, 5)月结, 6)货款扣, 7)季度结, 8)在线支付, 9)到付月结
    "wmsLocation": "", //集货位:可不填
    "extraFields": { //扩展字端:可不填,根据需要使用
        "note1": "", //自定义备注1
        "note2": "", //自定义备注2
        "note3": "", //自定义备注3
        "note4": "", //自定义备注4
        "note5": "", //自定义备注5
        "note6": "", //自定义备注6
        "note7": "", //自定义备注7
        "note8": "", //自定义备注8
        "note9": "", //自定义备注9
        "note10": "", //自定义备注10
        "note11": "", //自定义备注11
        "note12": "" //自定义备注12
    },
    //货物列表
    "cargoList": [
        {
            "name": "", //货物名称
            "note1": "", //自定义备注1
            "note2": "", //自定义备注2
            "note3": "", //自定义备注3
            "note4": "", //自定义备注4
            "note5": "", //自定义备注5
            "note6": "", //自定义备注6
            "productModel": "", //货物备注
            "quantity": 1.0, //件数
            "value": 2.0, //货值
            "volume": 3.0, //体积
            "weight": 4.0 //重量
        }
    ]
}
```

## 修改运单参数说明
ModifyOrderEntity结构如下:
```java
{
    "appointArriveTime": 1561627095, //预约送达时间，精确到秒的时间戳
    "customerOrderNumber": "", //客户单号
    "deliveryTime": 1561627095, //提货时间，精确到秒的时间戳
    "deliveryType": 1, //提送类型, 1自提，2送货
    "startAddress": "", //起始地
    "endAddress": "", //目的地
    "note": "", //备注
    "organizationPath": "", //组织机构path，此字段请参考TMS三方接口文档常见问题的组织机构相关问题
    "receiptCount": 2, //回单数量
    //发货人信息
    "consigner": {
        "name": "", //姓名
        "phone": "", //手机号
        "address": {
            "province": "", //省
            "city": "", //市
            "district": "", //区
            "address": "", //详细地址
            "streetNumber": "", //街道名称
            "lat": 0.0, //纬度
            "lng": 0.0 //精度
        }
    },
    //收货方信息，consignees=null或不传递此字段则不修改，否则会覆盖原本的收货方信息
    "consignees": [
        {
            "name": "", //姓名
            "phone": "", //手机号
            "address": {
                "province": "", //省
                "city": "", //市
                "district": "", //区
                "address": "", //详细地址
                "streetNumber": "", //街道名称
                "lat": 0.0, //纬度
                "lng": 0.0 //精度
            }
        }
    ],
    /*运单自定义备注，只需传递需要修改的备注即可，值为null或者未传递的不会修改*/
    "customNotes": {
        "note1": "", //自定义备注1
        "note2": "", //自定义备注2
        "note3": "", //自定义备注3
        "note4": "", //自定义备注4
        "note5": "", //自定义备注5
        "note6": "", //自定义备注6
        "note7": "", //自定义备注7
        "note8": "", //自定义备注8
        "note9": "", //自定义备注8
        "note10": "", //自定义备注10
        "note11": "", //自定义备注11
        "note12": "" //自定义备注12
    },
    //货物信息列表，orderCargoes=null或不传递此字段则不修改，否则会覆盖原本的货物信息
    "orderCargoes": [
        {
            "name": "", //货物名称
            "quantity": 1.0, //件数
            "value": 2.0, //货值
            "volume": 3.0, //体积
            "weight": 4.0, //重量
            "productModel": "", //备注
            "note1": "", //自定义货物备注1
            "note2": "", //自定义货物备注2
            "note3": "", //自定义货物备注3
            "note4": "", //自定义货物备注4
            "note5": "", //自定义货物备注5
            "note6": "" //自定义货物备注6
        }
    ]
}
```

## 受理单参数说明
CustomerOrderEntity结构如下:
```java
{
    "consignerAddress": "", //发货人地址:必填
    "consignerName": "", //发货人姓名:必填
    "consignerPhone": "", //发货人电话:必填
    "appointArriveTime": 1573178874, //预约送达时间:非必填，时间戳，精确到秒
    "originalOrderNumber": "", //客户单号:非必填
    "consigneeAddress": "", //收货人地址:非必填
    "consigneeName": "", //收货人姓名:非必填
    "consigneePhone": "", //收货人电话:非必填
    "deliveryTime": 1573178874, //提货时间:非必填，时间戳，精确到秒
    "deliveryType": 1, //提送类型:非必填，1)自提, 2)送货
    "deviceNumber": "", //绑定设备号:非必填
    "startAddress": "", //起始地:非必填
    "endAddress": "", //目的地:非必填
    //发货方经纬度:非必填
    "consignerLocation": {
        "lng": 0.0, //经度
        "lat": 0.0 //纬度
    },
    //收货方经纬度:非必填
    "consigneeLocation": {
        "lng": 0.0, //经度
        "lat": 0.0 //纬度
    },
    "note1": "", //自定义备注1:非必填
    "note2": "", //自定义备注2:非必填
    "note3": "", //自定义备注3:非必填
    "note4": "", //自定义备注4:非必填
    "note5": "", //自定义备注5:非必填
    "note6": "", //自定义备注6:非必填
    "note7": "", //自定义备注7:非必填
    "note8": "", //自定义备注8:非必填
    "note9": "", //自定义备注8:非必填
    "note10": "", //自定义备注10:非必填
    "note11": "", //自定义备注11:非必填
    "note12": "", //自定义备注12:非必填
    "organizationPath": "0-11", //组织机构:非必填，具体请看常见问题中的组织机构相关内容
    "receiptCount": 1, //回单数:非必填
    "remarks": "", //备注:非必填
    "shipperPay": 12.0, //上游运费:非必填
    "shipperPayType": 1, //上游运费支付方式:非必填，1)现付, 2)到付, 3)回付, 4)周结, 5)月结, 6)货款扣, 7)季度结, 8)在线支付, 9)到付月结
    //货物列表
    "cargoList": [
        {
            "name": "", //货物名称
            "note1": "", //自定义备注1
            "note2": "", //自定义备注2
            "note3": "", //自定义备注3
            "note4": "", //自定义备注4
            "note5": "", //自定义备注5
            "note6": "", //自定义备注6
            "productModel": "", //货物备注
            "quantity": 1.0, //件数
            "value": 2.0, //货值
            "volume": 3.0, //体积
            "weight": 4.0 //重量
        }
    ]
}
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)