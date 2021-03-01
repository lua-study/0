# 驱动打印小票--80热敏打印机

_项目环境基于JFinal2.2 偷了个懒直接在JFinal_demo上做的_
- - -
在大神 [SubLuLu/thermal_printer](https://github.com/SubLuLu/thermal_printer) 开源的项目基础上写了这个demo，SubLuLu用的是指令打印，而且环境是基于Android的，所以我用Java做的项目无法很方便的打印图片和兼容更多的热敏打印机，因此借鉴大神的构思我采用驱动方式进行打印。

## 打印流程
---
![输入图片说明](https://static.oschina.net/uploads/img/201609/26162058_wLgt.png "在这里输入图片标题")

_如图中所示，在项目实际使用中采用异步的方式进行打印。调用者只需要创建新的PrintJob 添加到任务队列中，挂起的线程就会被自动唤起完成打印任务_

###  打印模板
---
> 模板采用Json格式存储，分为header、goods、warn、msg四个部分，对模板的解析采用阿里出品的fastjson，模板共5中，模板名称分别对应PrintJob中missionType

####模板示例-（simple.json）

``` json
{
	"header": [{
		"text": "{$title}",
		"size": 14,
		"bold": true,
		"align": 1,
		"line": true,
		"type": 0
	},
	{
		"text": "品    牌：{$brandName}",
		"size": 9,
		"bold": false,
		"align": 0,
		"line": false,
		"type": 0
	},
	{
		"text": "({$shopName})",
		"size": 9,
		"bold": false,
		"align": 0,
		"line": true,
		"type": 0
	},
	{
		"text": "桌    号：{$tableNumb}",
		"size": 9,
		"bold": false,
		"align": 0,
		"line": false,
		"type": 0
	},
	{
		"text": "({$tableName})",
		"size": 9,
		"bold": false,
		"align": 0,
		"line": true,
		"type": 0
	},
	{
		"text": "--------------------------------",
		"size": 9,
		"bold": false,
		"align": 0,
		"line": true,
		"type": 0
	}],
	"goods": [{
		"name": "编码",
		"width": 8,
		"variable": "code"
	},
	{
		"name": "名称",
		"width": 12,
		"variable": "name"
	},
	{
		"name": "数量",
		"width": 6,
		"variable": "quantity"
	},
	{
		"name": "  金额",
		"width": 8,
		"variable": "price"
	}],
	"warn": [{
		"text": "-------------{$warnTitle}--------------",
		"size": 9,
		"bold": false,
		"align": 0,
		"line": true,
		"type": 0
	},
	{
		"text": "  ",
		"size": 9,
		"bold": false,
		"align": 0,
		"line": true,
		"type": 0
	},
	{
		"text": "{$warnMsg}",
		"size": 11,
		"bold": true,
		"align": 0,
		"line": true,
		"type": 0
	}],
	"msg": [{
		"text": "----------{$posTitle}-----------",
		"size": 9,
		"bold": false,
		"align": 0,
		"line": true,
		"type": 0
	},
	{
		"text": "{$posMsg}",
		"size": 9,
		"bold": false,
		"align": 0,
		"line": true,
		"type": 0
	}]
}
```
模板中{$title}等表示指定的占位符，将来在打印参数中会被替换

### 打印规则
---
![模板打印规则](https://static.oschina.net/uploads/img/201609/26155334_XLtB.png "模板打印规则")
### 打印参数
> - 打印根据模板和打印参数合成按照顺序进行打印
- 打印参数替换模板中的占位符
- 打印参数解析商品信息进行输出

### 参数示例

``` json
{
	"keys": {
		"dateTime": "2016-09-10 12:21:00",
		"posTitle": "收银软件下单结果",
		"brandName": "智慧餐厅",
		"orderId": "1609101220001",
		"shopName": "天山店",
		"title": "网络订单",
		"tableName": "外卖1",
		"barCode": "7255",
		"allPrice": "66.88",
		"tableNumb": "0002",
		"warnTitle": "异常提示",
		"posMsg": "点菜成功！1001 无此菜 本次点菜3/3份。其中2成功，1失败。合计XXXX元祝您用餐愉快！欢迎下次光临",
		"warnMsg": "部分菜品未下成功请联系服务员人工处理"
	},
	"goods": [{
		"code": "01001",
		"quantity": "1.0",
		"price": "18.0",
		"name": "牛肉"
	},
	{
		"code": "01002",
		"quantity": "1.0",
		"price": "10.0",
		"name": "酸辣土豆"
	},
	{
		"code": "01003",
		"quantity": "1.0",
		"price": "6.0",
		"name": "拍黄瓜"
	}]
}
```
打印参数的代码结构如上所示，主要分为keys和goods两个部分：

> - keys中的值负责替换模板中的占位符，如果模板中有，keys中没有则将占位符原样输出
- goods中的参数对用模板中的goods的每个属性

### 封装的PrintJob
``` java

    /**
	 * 任务类型：0=普通订单 1=预定单 2=支付订单 3=警告单 4=test单
	 */
	private int missionType;
	
	/**
	 * 需要打印的参数--可扩展
	 */
	private Map  param;
	
	/**
	 * 打印机逻辑名称
	 */
	private String printerName;
```
根据不同的missionType自动选用对应的模板，替换参数后打印

### 效果图(多模板)

![输入图片说明](https://static.oschina.net/uploads/img/201609/26160936_ZFa4.jpg "在这里输入图片标题")
![输入图片说明](https://static.oschina.net/uploads/img/201609/26161056_FFvT.jpg "在这里输入图片标题")
![输入图片说明](https://static.oschina.net/uploads/img/201609/26160953_5Gwi.jpg "在这里输入图片标题")
![输入图片说明](https://static.oschina.net/uploads/img/201609/26161013_5IQr.jpg "在这里输入图片标题")
![输入图片说明](https://static.oschina.net/uploads/img/201609/26160904_eSE3.jpg "在这里输入图片标题")
![输入图片说明](https://static.oschina.net/uploads/img/201609/26161041_0DQW.jpg "在这里输入图片标题")

## 使用示例
---
``` java
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

import com.demo.common.driverpos.PrintJob;
import com.demo.common.driverpos.PrintQueue;
import com.demo.common.driverpos.PrintThread;
import com.jfinal.kit.JsonKit;
import com.jfinal.plugin.activerecord.Db;
import com.jfinal.plugin.activerecord.Record;

public class DriverPrintQueueTest extends BaseTest {
	
	static{
		
		System.out.println("printThread is start : " + System.currentTimeMillis());
		PrintThread.start();
	}
	
	@Override
	public void test() {
		mySleep(5);
		PrintQueue.add(new PrintJob(0, jsonParam(), "BTP-2002CP(E)"));
		mySleep(15);
	}
	
	public void mySleep(int i) {
		try {
			System.out.println("sleep" + i*1000 + "ms ...");
			Thread.sleep(i * 1000);
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
	}
	
	public static Map  jsonParam(){
		Map  template = new HashMap ();
		Map  keys = new HashMap ();
		String posResult = "点菜成功！1001 无此菜 本次点菜3/3份。其中2成功，1失败。合计XXXX元祝您用餐愉快！欢迎下次光临";
		keys.put("title", "网络订单");
		keys.put("brandName", "智慧餐厅");
		keys.put("shopName", "天山店");
		keys.put("tableNumb", "0002");
		keys.put("tableName", "外卖1");
		keys.put("orderId", "1609101220001");
		keys.put("dateTime", "2016-09-10 12:21:00");
		keys.put("allPrice", "66.88");
		keys.put("barCode","7255");
		
		if(!posResult.contains("成功")){
			if(posResult.contains("重单")){
				keys.put("warnTitle", "提    示");
				keys.put("warnMsg", "该订单已处理");
			}else{
				keys.put("warnTitle", "异常提示");
				keys.put("warnMsg", "自动下单失败请人工处理");
			}
		}else{
			if(posResult.contains("无此") || posResult.contains("沽清")
					|| posResult.contains("不存在")){
				keys.put("warnTitle", "异常提示");
				keys.put("warnMsg", "部分菜品未下成功请联系服务员人工处理");
			}
		}
		
		keys.put("posTitle", "收银软件下单结果");
		keys.put("posMsg", posResult);
		
		List > goods = new ArrayList >();
		List  menu = Db.find("select * from menu");
//		int count = 0;
		for (Record record : menu) {
			Map  good = new HashMap ();
			good.put("code", record.get("code"));
			good.put("name", record.get("name"));
			good.put("quantity", "1.0");
			good.put("price", record.get("price"));
//			good.put("qrcode", "1.png");
//			if(count!=1){
//				good.put("remark", "免葱、免辣");
//			}
//			count++;
			goods.add(good);
		}
		
		template.put("goods", goods);
		template.put("keys", keys);
		System.out.println(JsonKit.toJson(template));
		return template;
	}

}
```
> - 在上面的代码中模拟多线程，一个线程取打印任务（Queue.take），当Queue队列为空时挂起。
- 另一个线程add PrintJob，这时挂起的线程会被唤起，完成打印任务
- 需要注意一点，示例中的baseTest类里有一个@BeforeClass 的方法加载SQLite数据库，用于读取菜品，
子类重写test方法即可用Unit进行单元测试

_另外强调一点：驱动打印文本时自动换行没有采用指令方便，项目中已经实现自动换行功能，有兴趣的可以看看实现方式:)_

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)