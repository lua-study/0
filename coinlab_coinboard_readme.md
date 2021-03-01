# 跨平台自定义实时行情看板
### 前言
前段时间跟朋友炒币，总是需要打开交易平台才能看行情和炒币，有点麻烦，而且那个窗口也特别大，内容也很杂，所以跟我说能不能搞个跨平台的可以自己定制的行情看板。

### 主要工具
- electron
- vue
- element-ui
- aicoin

### 安装electron和vue
这个教程比较多，不过不用自己做，有这种template,参考[链接](https://github.com/SimulatedGREG/electron-vue)，建议使用cnpm快一些尤其是electron如果用npm特别慢。

```
# Install vue-cli and scaffold boilerplate
npm install -g vue-cli
vue init simulatedgreg/electron-vue my-project

# Install dependencies and run your app
cd my-project
yarn # or npm install
yarn run dev # or npm run dev
```

### 项目结构
![](media/15269811750411/15270635748011.jpg)
#### 主要文件说明
- MainPage用来配置要显示的货币类型
- ShowPage是看板页面
- aicoin是下载到本地的aicoin脚本，因为要翻墙所以先下好
- showcoin是具体显示数据的脚本。

#### 遇到的问题和说明
1. 如何在vue中导入非npm js脚本
    由于aicoin脚本为普通js脚本不能直接import所以这里使用动态 html tag的方式来导入，有两个小问题点1.如何导入，2.如何控制导入顺序  
    
    如何导入  
    
    ```
      let loadScript = function(url, callback) {
      var script = document.createElement("script");
      script.type = "text/javascript";
    
      if (script.readyState) {
        //IE
        script.onreadystatechange = function() {
          if (
            script.readyState == "loaded" ||
            script.readyState == "complete"
          ) {
            script.onreadystatechange = null;
            callback();
          }
        };
      } else {
        //Others
        script.onload = function() {
          callback();
        };
      }
    
      script.src = url;
      document.getElementsByTagName("head")[0].appendChild(script);
    };
    ```
    
    如何控制导入顺序
    
    ```javascript
        loadScript("./static/aicoin.js", function() {
          loadScript("./static/showcoin.js", function() {});
        });
    ```


2. vue如何调用electronAPI

electron分主线程和展示线程通过ipc进行通信  
注册事件  


```javascript
ipcMain.on('resizeWindow', (event, arg) => {
  mainWindow.setSize(arg.width, arg.height)
})
```

触发


```javascript
ipcRenderer.send("resizeWindow",  {width:1000, height:(dataitems.length+2)*34+38+30});
```

#### 跨平台打包

```bash
#  mac 
npm run build:mac
# win
npm run build:win
```

#### 使用方法
npm run dev
然后去[aicoin](https://www.aicoin.net.cn/widgets/markets)选择自己想看的币和平台，然后粘贴右面币列表代码  
![](media/15269811750411/15270646648479.jpg)
  
![](media/15269811750411/15270646958166.jpg)

点击立即创建  
![](media/15269811750411/15270647115421.jpg)


#### 代码[地址]()



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)