## 省份/城市/区县定位选择器 ##

  
 
>  💨🚀 微信小程序，一行代码引入的省份/城市/区县定位选择器的库

  

### 主要功能 ###
* 自动定位 城市、区县（也支持手动重新定位）
* 手动 汉字、拼音搜索 城市，支持搜索数量335个，覆盖地级市
* 亦可通过 侧边栏 选择，城市按拼音首字母排列
* 选择好城市后，自动显示 辖下区县




### 集成说明 ###
* 将libs文件夹拷贝至您的小程序项目根目录
* 在您的项目根目录 app.json 里的 pages 数组里增加一行  "libs/citySelector/switchcity/switchcity" 
* 打开项目里的 /libs/citySelector/config.default.js 文件
* 将其中的key改为自己的腾讯地图key（申请快速并免费） 点击立即打开腾讯地图Key申请页面 

### 快速使用 ###

>在您要打开选择器地方用navigator组件，将url设置为 "/libs/citySelector/switchcity/switchcity" 

>或者，在 JS 代码里直接使用 wx.navigateTo 打开地区选择器
 
 
wx.navigateTo({
    url: '/libs/citySelector/switchcity/switchcity',
});
 
 
> 两种方法二选一即可
 

### 获取返回数据 ###

> 在switchcity页选择完地区之后，点击会自动返回，并且将省份/城市/区县数据设置到本页面的  this.data.address   内

###### 如图所示 ######
  

###### 修改颜色样式 ######
* 在libs文件夹搜索 #c60a0d ，替换为您想要的颜色值即可

### 功能演示 ###

##### Gif有点卡，不过实际操作起来是超级流畅的 

  
 
 
   
### 🤗 🤗 🤗 如果对您有帮助，请star ###
        

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)