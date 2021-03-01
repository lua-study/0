#version
这个版本是开发版本，是公司自己使用的包含所有功能
- 法币交易,币币交易

# bitrade

## 前端开发规范
1. 页面使用驼峰法命名，如Exchange.vue,WithdrawRecord.vue,名称为英文单词，并且要能正确描述该模块功能
2. 变量命名禁止使用拼音，特别是拼音缩写
3. 页面比较多时应该使用文件夹做分类,如路由以及国际化管理可以采用webpack提供的require来实现分包,方便维护;
4. 模块中data变量应该尽量少，比较多时应该使用子对象进行管理

> A Vue.js project
## 注意点
1. node版本必须大于8.0以上,需要使用对应的npm版本，如果安装依赖或者第三方包的过程中出现报错现象，可以使用npm代理，或者切换镜像
2. 因为这是基于一个完整版本的分离版，可能牵扯到杠杆交易，ieo管理的接口，由于页面之间的耦合度关系，需要跟踪错误，注掉报错的接口；
3. nginx 需要配置开启gzip压缩,可以极大提高首页的加载速度，防止出现白屏的现象;
4. compression-webpack-plugin 该插件版本需要关注，这个插件的作用是压缩js，css资源为.gz格式的，由于对应的webpack版本的关系，需要降低该compression-webpack-plugin插件版本，详情参阅 package.json文件



## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm test
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).


## 更新日志  
2018.7.27   
1、个人资产、手续费、成交金额等固定截取8位小数； 

2018.7.21   
1、修复账户设置绑定支付宝和微信部分页面乱码的BUG； 

2018.7.20   
1、修复币币交易买卖区域和委托记录会显示科学计数的BUG；   

2018.7.18   
1、修复币币交易换算人民币数值不正确的问题； 
2、优化币币交易选择交易对后左上选择区域的状态； 
3、交易挖矿、持币分红页面科学计数转换为数字；  
4、持币分红页面分页功能；  
5、法币交易我的订单增加联系电话；  

2018.7.17   
1、修复提币页面提现记录分页BUG并优化筛选功能； 
2、首页特点内容优化；  

2018.7.16   
1、币币交易去掉价格显示2位小数的限制；  
2、修复币币交易页面换算人民币数值错误的BUG；  
3、提币页面，提币地址下拉框允许用户手动输入； 
4、修复提币页面，提现记录表格币种列无数据的BUG；  
5、修复提币页面，提现记录表格选择币种返回的有数据但表格上未显示的BUG；  
6,法币交易样式修改
7:微信客服图片添加
8：聊天内容icon替换
9:提笔精度修改  

2018.7.13   
1、推广好友、我的佣金增加分页功能； 
2、buyPrice精度调整为8，以解决法币交易买入输入小数点数值时报“数量错误”的错误； 
3、样式修改；以及二维码上线； 

2018.7.12   
1、修复法币交易输入与卖出数量相等的值无法提交购买的BUG；  
2、公告页样式修改,首页公告走马灯添加;

2018.7.11   
1、banner图替换1-6；  
2、字段修正 买入卖出 以及样式修正;

2018.7.10  
1、真实姓名用*代替；  

2018.7.9   
1、实名认证上传图片超过2M拒绝提交；

2018.7.8  
1、banner指示器 bottom 3px=>20px；  
2、超级合伙人连接去掉；  
3、实名认证上传图片失败提示；   
4、实名认证审核失败提示；  
5、banner图替换126；  
6、修复提币页面poptip组件出现黑色滚动条的BUG。  

2018.7.7  
1、修复公告列表页第一页只有3条中文标题的BUG；  
2、修复首页折线图接口返回[]时js报错的问题；  
3、myextension页面中英文联动；  
4、财务中心=》持币分红 nodata 错误提示去掉；  
5、首页app下载二维码暂时去掉；  
6、注册按钮点击后字不显示的BUG。  

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)