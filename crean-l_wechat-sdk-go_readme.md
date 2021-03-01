# wechat

[![Latest Tag](https://img.shields.io/badge/tag-v0.2.0-blue.svg)](https://gitee.com/cuckoopark/wechat/releases)

这是用Golang封装了微信的所有API接口的SDK，并自动生成和解析XML数据，包括微信支付、公众号、小程序、移动端的工具函数。

* 支持境内普通商户和境内服务商(境外和银行服务商没有条件测试)。
* 支持全局配置应用ID、商家ID等信息。
* 全部参数和返回值均使用`struct`类型传递，而不是`map`类型。

### 安装

```shell
go get -u gitee.com/cuckoopark/wechat
```

### 初始化

```go
const (
    isProd       = true                             // 生产环境或沙盒环境
    isMch        = false                            // 是否是企业模式，仅当调用企业付款时为true
    serviceType  = wechat.ServiceTypeNormalDomestic // 普通商户或服务商等类型
    apiKey       = "xxxxxxxx"                       // 微信支付上设置的API Key
    certFilepath = "/xxx/yyy/apiclient_cert.p12"    // 微信证书文件的本地路径，仅部分接口使用，如果不使用这些接口，可以传递空值
)
config := wechat.Config{
    AppId: AppID,
    MchId: MchID,
    SubAppId: SubAppId, // 仅服务商模式有效
    SubMchId: SubMchID, // 仅服务商模式有效
}
client := wechat.NewClient(isProd, isMch, serviceType, apiKey, certFilepath, config)
```

### 使用

以下是通用的接口，使用上面初始化时生成的实例`client`进行相应函数的调用。其中带有`(*Client)`字样的接口，需要使用`wechat.NewClient`创建的实例对象来调用，而不带的接口，则可以直接使用`wechat.XXX`调用。

使用样例：

```go
func Test() {
	// 初始化参数
	body := wechat.QueryOrderBody{}
	body.OutTradeNo = "YgENQFTovdeJdFouNyy3nFVOhGD6ZvPH"
	// 请求订单查询
	wxRsp, err := client.QueryOrder(body)
	if err != nil {
		return
	}
	fmt.Printf("返回值: %+v\n", wxRsp)
}
```

注意事项：

* 参数或返回值的类型，请查看接口对应的文件，里面有`XXXBody`和`XXXResponse`与之对应。
* 参数或返回值中的常量，请参照[constant.go](constant.go)文件。
* 具体使用方法，请参照接口对应的测试文件。

#### 微信支付

对应文件：`wx_pay_xxxxxx.go`

* 提交付款码支付：`(*Client) Micropay`。
* 统一下单：`(*Client) UnifiedOrder`。
* 查询订单：`(*Client) QueryOrder`。
* 关闭订单：`(*Client) CloseOrder`。
* 撤销订单：`(*Client) Reverse`。
* 申请退款：`(*Client) Refund`。
* 查询退款：`(*Client) QueryRefund`。
* 下载对账单：`(*Client) DownloadBill`。
* 交易保障(JSAPI)：`(*Client) ReportJsApi`。
* 交易保障(MICROPAY)：`(*Client) ReportMicropay`。
* 下载资金账单：TODO，client.DownloadFundFlow()。
* 拉取订单评价数据：TODO，client.BatchQueryComment()。
* 企业付款到零钱：`(*Client) Change`。
* 查询企业付款到零钱：`(*Client) QueryChange`。

#### 微信支付回调

对应文件：`wx_notify_xxxxxx.go`

* 支付回调：`(*Client) NotifyPay`。
* 退款回调：`(*Client) NotifyRefund`。

#### 微信公众号

对应文件：`wx_service_xxxxxx.go`

* 授权码查询OpenId：`(*Client) OpenIdByAuthCode`。
* 获取基础支持的AccessToken：`GetBasicAccessToken`。
* 获取用户基本信息(UnionId机制)：`GetUserInfo`。
* 获取H5支付签名：`GetH5PaySign`。

#### 微信小程序

对应文件：`wx_applet_xxxxxx.go`

* 获取小程序支付签名：`GetAppletPaySign`。
* 获取小程序码：`GetAppletUnlimitQrcode`。

#### 移动端

对应文件：`wx_app_xxxxxx.go`

* 获取APP支付签名：`GetAppPaySign`。

### 文档

* 微信支付文档：[https://pay.weixin.qq.com/wiki/doc/api/index.html](https://pay.weixin.qq.com/wiki/doc/api/index.html)
* 随机数生成算法：[https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=4_3](https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=4_3)
* 签名生成算法：[https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=4_3](https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=4_3)
* 交易金额：[https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=4_2](https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=4_2)
* 交易类型：[https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=4_2](https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=4_2)
* 货币类型：[https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=4_2](https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=4_2)
* 时间规则：[https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=4_2](https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=4_2)
* 时间戳：[https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=4_2](https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=4_2)
* 商户订单号：[https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=4_2](https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=4_2)
* 银行类型：[https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=4_2](https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=4_2)
* 单品优惠功能字段：[https://pay.weixin.qq.com/wiki/doc/api/danpin.php?chapter=9_101&index=1](https://pay.weixin.qq.com/wiki/doc/api/danpin.php?chapter=9_101&index=1)
* 代金券或立减优惠：[https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=12_1](https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=12_1)
* 最新县及县以上行政区划代码：[https://pay.weixin.qq.com/wiki/doc/api/download/store_adress.csv](https://pay.weixin.qq.com/wiki/doc/api/download/store_adress.csv)

### 开发进度

* 境内普通商户
  * [付款码支付](https://pay.weixin.qq.com/wiki/doc/api/micropay.php?chapter=5_1)
  * [JSAPI支付](https://pay.weixin.qq.com/wiki/doc/api/jsapi.php?chapter=7_1)
  * [Native支付](https://pay.weixin.qq.com/wiki/doc/api/native.php?chapter=6_1)
  * [APP支付](https://pay.weixin.qq.com/wiki/doc/api/app/app.php?chapter=8_1)
  * [H5支付](https://pay.weixin.qq.com/wiki/doc/api/H5.php?chapter=15_1)
  * [小程序支付](https://pay.weixin.qq.com/wiki/doc/api/wxa/wxa_api.php?chapter=7_3&index=1)
  * (TODO) [代金券或立减优惠](https://pay.weixin.qq.com/wiki/doc/api/tools/sp_coupon.php?chapter=12_1)
  * (TODO) [现金红包](https://pay.weixin.qq.com/wiki/doc/api/tools/cash_coupon.php?chapter=13_1)
  * [企业付款](https://pay.weixin.qq.com/wiki/doc/api/tools/mch_pay.php?chapter=14_1)
* 境内服务商
  * [付款码支付](https://pay.weixin.qq.com/wiki/doc/api/micropay_sl.php?chapter=5_1)
  * [JSAPI支付](https://pay.weixin.qq.com/wiki/doc/api/jsapi_sl.php?chapter=7_1)
  * [Native支付](https://pay.weixin.qq.com/wiki/doc/api/native_sl.php?chapter=6_1)
  * [APP支付](https://pay.weixin.qq.com/wiki/doc/api/app/app_sl.php?chapter=8_1)
  * [H5支付](https://pay.weixin.qq.com/wiki/doc/api/H5_sl.php?chapter=15_1)
  * [小程序支付](https://pay.weixin.qq.com/wiki/doc/api/wxa/wxa_sl_api.php?chapter=7_3&index=1)
  * [现金红包](https://pay.weixin.qq.com/wiki/doc/api/tools/cash_coupon_sl.php?chapter=13_1)

### 测试方法

修改`client_test.go`中的生成测试Client的代码，调整沙盒/生产环境、普通商户/服务商等选项，或者修改环境变量，来调整商户参数。

环境变量的脚本在`env`文件中，修改后加载环境变量：

```shell
source env
go test
```

### TODO

- 测试改为不同情境使用不同的用例。
- 继续调试境内普通商户和境内服务商的其他模块API文档。
- 选择性调试境外接口。
- 继续增加公众号和小程序相关接口。
- 移除`service`开头的文件。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)