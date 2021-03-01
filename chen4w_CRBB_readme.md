# CRBB(Copyright Register Based Blockchain)   
基于区块链的版权注册系统
>&emsp;本项目的开发目标，是构建基于区块链网络系统的图片版权保护应用系统。即实现不受特定中心化服务管理机构控制，由联盟共建、共同维护的，能提供在线图片版权保护服务的应用系统。该目标应用系统，由应用客户端和区块链网络服务端构成，其核心功能是为用户提供去中心化的图片版权记录操作相关服务，包括账户管理、图片版权登记以及图片版权授权记录服务。
### 参考
- [Node.js API](https://nodejs.org/dist/latest-v8.x/docs/api/)——编程语言采用Node.js
- [Meteor Guide](https://guide.meteor.com/) ——基于Meteor框架开发
- [React](https://reactjs.org/) ——构建用户界面的 JAVASCRIPT 库
- [Materical UI](http://www.material-ui.com/#/components/app-bar) ——前端页面各种快速开发组件
- [jsrsasign](https://www.npmjs.com/package/jsrsasign) ——用于生成公私钥、用户证书，交易签名的第三方库

### 安装
- 安装 [Node.js](https://nodejs.org/en/download/)
- 安装 [Meteor](https://www.meteor.com/)
- 安装 IDE 推荐 [Visual Studio Code](https://code.visualstudio.com/)

### 运行
- 使用`git clone` 或者下载压缩包，拷贝项目到本地
- 进入项目目录， 运行`meteor npm install`下载依赖包到本地，建议使用[阿里](http://npm.taobao.org/)镜像源，设置方法参考[CSDN](https://blog.csdn.net/lixiaomeng_/article/details/74617668)的博客
- 在项目目录下面运行`meteor`启动 meteor
- 打开浏览器输入 `http://localhost:3000`, 并打开开发者工具，设置为模拟移动设备模式。（建议使用Chrome浏览器，可以仿真主流的移动设备）

### 默认账户  
&emsp; 系统默认导入了2个用户，管理员和普通用户。  
- 管理员：账号：13388889999 密码：123  
- 普通用户：账号：18712341234 密码：123 

### 默认版权信息
&emsp; 系统默认导入了20条版权信息，方便用户查看系统功能。

### 注意  
1. `setting.js`文件中  
    - 上传图片目录设置
       >`this.pic_root = baseDir + "PictureCopyright";//存放图片根目录`  
        `this.pic_upload = 'uploadPics';   //图片上传目录`  
        
    最好保持默认，但用户也可以根据需要修改目录名称。  
    - 连接RepChain设置
        >`this.websocket_host = 'localhost';//RepChain的IP`  
         `this.websocket_port = '8081';//RepChain的端口`
2. 需要连接互联网，因为默认的20条版权信息中图片的地址是公网地址。

3. Keytool生成的私钥和证书的导入
    - 私钥：  
        目前该应用只接受`PKCS8PRV`无密码的`PEM`格式的私钥导入，导入有密码的私钥可能导致登录不了本应用.
        
    - 证书：  
        目前该应用只接受`X.509`类型的`PEM`格式的证书导入，导入其他格式的证书会导致应用出错.
        
    导入过程与普通用户导入过程一样，在注册用户的时候，填入用户信息以后，选择证书的这一步选择导入证书，并导入相应的密钥和证书即可。  
    **Notice：** `在导入结束，成功注册后，用户的密码默认设置为用户的手机号码，请尽快登录系统修改密码。`  
    
4. RepChain安装  
    - 安装[RepChain](https://gitee.com/chen4w/repchain)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)