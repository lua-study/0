### ipar_shop
#####ios 发布前必须：
`npm run bundle-ios`
#####安卓打包命令：
`cd android && ./gradlew assembleRelease`
#####重新下载&添加node-modules...
`rm -rf node_modules && rm -rf ~/.rncache && yarn`

##
###注意 !  (每次重新下载node-modules的时候一定要修改)：

1.修改index.js文件（路径： node_modules\native-echarts\src\components\Echarts） 
  修改


````
import { WebView, View, StyleSheet } from 'react-native';

source={require('./tpl.html')}
````
为
````
import { WebView, View, StyleSheet, Platform } from 'react-native';

source={Platform.OS==='ios' ? require('./tpl.html'):{uri:'file:///android_asset/tpl.html'}}
````


2.修改index.js文件（路径： node_modules\react-native-tab-navigator\TabNavigator.js） 修改
```
 defaultSelectedIcon: {
        tintColor: 'black',//修改black
 },
```
3.修改Badge.ls (node_modules\react-native-tab-navigator\Badge.js) 修改
```
let styles = StyleSheet.create({
    container: {
        fontSize: 12,
        color: '#fff',
        backgroundColor: 'red',
        lineHeight: 15,
        textAlign: 'center',
        borderRadius: 7.5,
        overflow: 'hidden',
    },
});
```

4.修改ScrollableTabBar.js (node_modules\react-native-scrollable-tab-view\ScrollableTabBar) 修改
```
renderTab(){
...
 
                    {name}
 
...
}
//+ fontSize: isTabActive ? 18 : 14
```

5.修改ListView.js (路径：node_modules\react-native\Libraries\Lists\ListView.js);
```
 if (props.removeClippedSubviews === undefined) {
      props.removeClippedSubviews = true;//把true改成false
  }
```



##第三方组建文档
https://javascript.ctolib.com/article/wiki/89153（友盟推送）
//https://www.npmjs.com/package/react-native-umeng-push
//https:https://www.cnblogs.com/shaoting/p/6148085.html，，camera
//https://www.jianshu.com/p/2cef1baf9a6f,,,二维码，，http://www.cocoachina.com/ios/20170704/19717.html




###api 问题
https://admin.iparbio.com/api/v3/editCart  =  {code: 500, message: "ERROR", data: null, count: 0}


这就是我的爱好。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)