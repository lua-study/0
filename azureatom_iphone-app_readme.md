# 开源中国 iOS [客户端](http://www.oschina.net/app/)

------

## 编译环境
Xcode 6＋

## 运行项目
1. 安装CocoaPods (关于CocoaPods的安装和使用，可参考[这个教程](http://code4app.com/article/cocoapods-install-usage))
2. 在终端下打开项目所在的目录，执行```pod install``` (若是首次使用CocoaPods，需先执行```pod setup```)
3. ```pod install```命令执行成功后，通过新生成的xcworkspace文件打开工程运行项目

## 目录简介
* API ——— 包含API和API返回数据的封装模型
* Utils ——— 常用的工具方法、类扩展及一些控件
* 用户、发现、动弹...... ——— 各个具体界面
* Main ViewControllers ——— 主要的视图控制器（作为基类或使用较广的控制器）



## 项目用到的开源类库、组件
1. AFNetworking                         网络请求
2. AFOnoSerializer                      序列化XML和HTML
3. Ono                                  解析XML
4. RESideMenu                           侧拉栏
5. MBProgressHUD                        显示提示或加载进度
6. SDWebImage                           加载网络图片和缓存图片
7. SSKeychain                           账号密码的存取
8. TTTAttributedLabel                   支持富文本显示的label
9. ReactiveCocoa                        函数式编程和响应式编程框架
10. GPUImage                            实现模糊效果
11. DTCoreText                          渲染HTML

## 开源协议
OSChina iOS app is under the GPL license. See the LICENSE file for more details.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)