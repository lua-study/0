前言：最近项目需要切换到iOS平台做一些提交审核和支付对接相关的工作，上一篇刚分享了最新的iOS10提交审核的一些坑，这篇分享一些内购相关的流程。
# Unity iOS内购
### 思路：
Unity调用iOS内购代码实现
### 效果图：
![购买弹框](http://img.blog.csdn.net/20161031223902497)
![购买结果](http://img.blog.csdn.net/20161031223923716)

### 流程

这里就不重复写了，直接上截图
![这里写图片描述](http://img.blog.csdn.net/20161031224839086)

### OC代码：
#### IAPInterface(主要是实现Unity跟OC的IAP代码的一个交互作用，等于是一个中间桥梁)

```
#import  

@interface IAPInterface : NSObject

@end
```

```
#import "IAPInterface.h"
#import "IAPManager.h"

@implementation IAPInterface

void TestMsg(){
    NSLog(@"Msg received");

}

void TestSendString(void *p){
    NSString *list = [NSString stringWithUTF8String:p];
    NSArray *listItems = [list componentsSeparatedByString:@"\t"];
    
    for (int i =0; i 
#import  

@interface IAPManager : NSObject {
    SKProduct *proUpgradeProduct;
    SKProductsRequest *productsRequest;
}

-(void)attachObserver;
-(BOOL)CanMakePayment;
-(void)requestProductData:(NSString *)productIdentifiers;
-(void)buyRequest:(NSString *)productIdentifier;

@end
```

```
#import "IAPManager.h"

@implementation IAPManager

-(void) attachObserver{
    NSLog(@"AttachObserver");
    [[SKPaymentQueue defaultQueue] addTransactionObserver:self];
}

-(BOOL) CanMakePayment{
    return [SKPaymentQueue canMakePayments];
}

-(void) requestProductData:(NSString *)productIdentifiers{
    NSArray *idArray = [productIdentifiers componentsSeparatedByString:@"\t"];
    NSSet *idSet = [NSSet setWithArray:idArray];
    [self sendRequest:idSet];
}

-(void)sendRequest:(NSSet *)idSet{
    SKProductsRequest *request = [[SKProductsRequest alloc] initWithProductIdentifiers:idSet];
    request.delegate = self;
    [request start];
}

-(void)productsRequest:(SKProductsRequest *)request didReceiveResponse:(SKProductsResponse *)response{
    NSArray *products = response.products;
    
    for (SKProduct *p in products) {
        UnitySendMessage("Main", "ShowProductList", [[self productInfo:p] UTF8String]);
    }
    
    for(NSString *invalidProductId in response.invalidProductIdentifiers){
        NSLog(@"Invalid product id:%@",invalidProductId);
    }
    
    [request autorelease];
}

-(void)buyRequest:(NSString *)productIdentifier{
    SKPayment *payment = [SKPayment paymentWithProductIdentifier:productIdentifier];
    [[SKPaymentQueue defaultQueue] addPayment:payment];
}

-(NSString *)productInfo:(SKProduct *)product{
    NSArray *info = [NSArray arrayWithObjects:product.localizedTitle,product.localizedDescription,product.price,product.productIdentifier, nil];
    
    return [info componentsJoinedByString:@"\t"];
}

-(NSString *)transactionInfo:(SKPaymentTransaction *)transaction{
    
    return [self encode:(uint8_t *)transaction.transactionReceipt.bytes length:transaction.transactionReceipt.length];
    
    //return [[NSString alloc] initWithData:transaction.transactionReceipt encoding:NSASCIIStringEncoding];
}

-(NSString *)encode:(const uint8_t *)input length:(NSInteger) length{
    static char table[] = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/=";
    
    NSMutableData *data = [NSMutableData dataWithLength:((length+2)/3)*4];
    uint8_t *output = (uint8_t *)data.mutableBytes;
    
    for(NSInteger i=0; i >18) & 0x3f];
        output[index + 1] = table[(value>>12) & 0x3f];
        output[index + 2] = (i+1) >6) & 0x3f] : '=';
        output[index + 3] = (i+2) >0) & 0x3f] : '=';
    }
    
    return [[NSString alloc] initWithData:data encoding:NSASCIIStringEncoding];
}

-(void) provideContent:(SKPaymentTransaction *)transaction{
    UnitySendMessage("Main", "ProvideContent", [[self transactionInfo:transaction] UTF8String]);
}

-(void)paymentQueue:(SKPaymentQueue *)queue updatedTransactions:(NSArray *)transactions{
    for (SKPaymentTransaction *transaction in transactions) {
        switch (transaction.transactionState) {
            case SKPaymentTransactionStatePurchased:
                [self completeTransaction:transaction];
                break;
            case SKPaymentTransactionStateFailed:
                [self failedTransaction:transaction];
                break;
            case SKPaymentTransactionStateRestored:
                [self restoreTransaction:transaction];
                break;
            default:
                break;
        }
    }
}

-(void) completeTransaction:(SKPaymentTransaction *)transaction{
    NSLog(@"Comblete transaction : %@",transaction.transactionIdentifier);
    [self provideContent:transaction];
    [[SKPaymentQueue defaultQueue] finishTransaction:transaction];
}

-(void) failedTransaction:(SKPaymentTransaction *)transaction{
    NSLog(@"Failed transaction : %@",transaction.transactionIdentifier);
    
    if (transaction.error.code != SKErrorPaymentCancelled) {
        NSLog(@"!Cancelled");
    }
    [[SKPaymentQueue defaultQueue] finishTransaction:transaction];
}

-(void) restoreTransaction:(SKPaymentTransaction *)transaction{
    NSLog(@"Restore transaction : %@",transaction.transactionIdentifier);
    [[SKPaymentQueue defaultQueue] finishTransaction:transaction];
}


@end

```
#### Unity中调用的C#代码

```
using UnityEngine;
using System.Collections;
using System.Collections.Generic;
using System.Runtime.InteropServices;

public class IAPExample : MonoBehaviour {
	
	public List  productInfo = new List ();
	
	[DllImport("__Internal")]
	private static extern void TestMsg();//测试信息发送
	
	[DllImport("__Internal")]
	private static extern void TestSendString(string s);//测试发送字符串
	
	[DllImport("__Internal")]
	private static extern void TestGetString();//测试接收字符串
	
	[DllImport("__Internal")]
	private static extern void InitIAPManager();//初始化
	
	[DllImport("__Internal")]
	private static extern bool IsProductAvailable();//判断是否可以购买
	
	[DllImport("__Internal")]
	private static extern void RequstProductInfo(string s);//获取商品信息
	
	[DllImport("__Internal")]
	private static extern void BuyProduct(string s);//购买商品
	
	//测试从xcode接收到的字符串
	void IOSToU(string s){
		Debug.Log ("[MsgFrom ios]"+s);
	}
	
	//获取product列表
	void ShowProductList(string s){
		productInfo.Add (s);
	}
	bool back = false;
	//获取商品回执
	void ProvideContent(string s){
		Debug.Log ("[MsgFrom ios]proivideContent : "+s);
		back = true;
	}
	
	
	// Use this for initialization
	void Start () {
		InitIAPManager();
	}
	
	void OnGUI(){
		
		if(Btn ("GetProducts")){
			if(!IsProductAvailable())
				throw new System.Exception("IAP not enabled");
			productInfo = new List ();
			RequstProductInfo("com.aladdin.fishpocker1\tcom.aladdin.fishpocker2");
		}
		
		GUILayout.Space(40);

		if (back)
			GUI.Label (new Rect (10, 150, 100, 100), "Message back");

		for(int i=0; i<productInfo.Count; i++){
			if(GUILayout.Button (productInfo[i],GUILayout.Height (100), GUILayout.MinWidth (200))){
				string[] cell = productInfo[i].Split('\t');
				Debug.Log ("[Buy]"+cell[cell.Length-1]);
				BuyProduct(cell[cell.Length-1]);
				GUI.Label(new Rect (10, 10, 100, 200), string.Format("[Buy]{0}" ,cell[cell.Length-1]));
			}  
		}
	}
	
	bool Btn(string msg){
		GUILayout.Space (100);
		return 	GUILayout.Button (msg,GUILayout.Width (200),GUILayout.Height(100));
	}
}

```


 
### Git地址[点击下载](https://git.oschina.net/dingxiaowei/iOSPurchase.git)
---
欢迎关注我的[围脖](http://weibo.com/dingxiaowei2013) 
==================== 迂者 丁小未 CSDN博客专栏=================

MyBlog：http://blog.csdn.net/dingxiaowei2013 MyQQ:1213250243

Unity QQ群：375151422 cocos2dx QQ群：280818155

====================== 相互学习，共同进步 ===================

----------


# iOS 内购验证
如果我们不做任何处理的话，越狱机是可以直接绕过支付验证直接获得结果的，这样对于我们辛辛苦苦的开发者来说简直噩耗，所以我们有必要了解一下内购验证相关的知识，以及知道如何去预防这样的事情。

### 相关资料

* https://developer.apple.com/library/ios/releasenotes/General/ValidateAppStoreReceipt/Chapters/ReceiptFields.html#//apple_ref/doc/uid/TP40010573-CH106-SW1
* http://hpique.github.io/RMStore-presentation-for-NSBarcelona
* http://asciiwwdc.com/2014/sessions/305

### 本地验证:

优点：

* 无需服务器验证

缺点：

* 项目里需要引入 OpenSSL

链接：

* http://stackoverflow.com/a/20039394/656428
* https://github.com/robotmedia/RMStore#receipt-verification
* https://github.com/robotmedia/RMStore/wiki/Receipt-verification


###  服务器验证:

优点：

* server-side verification over SSL is the most reliable way to determine the authenticity of purchasing records

缺点：


* 需要部署服务器，服务器和 App 之间的数据交换可能更容易被破解

链接：

* https://github.com/nomad/venice
* https://github.com/pcrawfor/iap_verifier


### 双重验证：

先本地验证一次，后服务器再验证一次（感觉没必要）

### 其他：

* http://receigen.etiemble.com Mac App，直接生成代码，Xcode 集成

### 常见的破解方法：

* http://blog.hussulinux.com/2013/04/apple-ios-in-app-purchase-hacking-how-to-prevent-specially-com-zeptolab-ctrbonus-superpower1-hacks/
* http://stackoverflow.com/a/17687827/656428

### 总的来说：

* 服务器验证更适合有自己账号系统的 App，直接可以对 IAP 破解免疫，否则一样很简单就被破解
* 本地验证使用下面的方法来增强验证
   * Check that the SSL certificate used to connect to the App Store server is an EV certificate.
   * Check that the information returned from validation matches the information in the SKPayment object.
   * Check that the receipt has a valid signature.
   * Check that new transactions have a unique transaction ID.





 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)