#  Nuxt.js
## 介绍
Nuxt.js简单的说是Vue.js的通用框架，最常用的就是用来作SSR（服务器端渲染）。再直白点说，就是Vue.js原来是开发SPA（单页应用）的，但是随着技术的普及，很多人想用Vue开发多页应用，并在服务端完成渲染。这时候就出现了Nuxt.js这个框架，她简化了SSR的开发难度。还可以直接用命令把我们制作的vue项目生成为静态html。
### 什么是服务器端渲染
最主要的原因时SPA（单页应用）不利于搜索引擎的SEO操作。比如你作一个新闻网站，流量的一个主要来源是通过百度、谷歌、bing这些搜索引擎，但是它们对SPA的抓取并不好，特别是百度根本没法抓取到SPA的内容页面，所以我们必须把我们的应用在服务端渲染成适合搜索引擎抓取的页面，再下载到客户端。那Nuxt.js适合作新闻、博客、电影、咨询这样的需要搜索引擎提供流量的项目。如果你要作移动端的项目，就没必要使用这个框架了。
### 什么是SSR
SSR，即服务器渲染，就是在服务器端将对Vue页面进行渲染生成html文件，将html页面传递给浏览器。

SSR有两个优点：
> SEO 不同于SPA的HTML只有一个无实际内容的HTML和一个app.js，SSR生成的HTML是有内容的，这让搜索引擎能够索引到页面内容。

> 更快内容到达时间 传统的SPA应用是将bundle.js从服务器获取，然后在客户端解析并挂载到dom。而SSR直接将HTML字符串传递给浏览器。大大加快了首屏加载时间。

### Nuxt.js
> Nuxt.js 是一个基于 Vue.js 的通用应用框架。

> 通过对客户端/服务端基础架构的抽象组织，Nuxt.js 主要关注的是应用的 UI渲染。

### Nuxt.js特点
1. 基于 Vue.js
2. 自动代码分层
3. 服务端渲染
4. 强大的路由功能，支持异步数据
5. 静态文件服务
6. ES6/ES7 语法支持
7. 打包和压缩 JS 和 CSS
8. HTML头部标签管理
9. 本地开发支持热加载
10. 集成ESLint
11. 支持各种样式预处理器： SASS、LESS、 Stylus等等

## 环境搭建和Hello World
### nuxt.js安装

	//安装vue-cli依赖
	npm install vue-cli -g
	//安装nuxt，初始化项目
	vue init nuxt/starter
	//安装依赖包
	npm install
	//启动服务
	npm run dev
在浏览器输入localhost:3000可以查看结果

![](https://i.imgur.com/fU7hqK1.png)

### 目录结构

![](https://i.imgur.com/hduWUlN.png)
## Nuxt常用配置项
### 配置IP和端口：

/package.json

	"config": {
	    "nuxt": {
	      "host": "127.0.0.1",
	      "port": "1818"
	    }
	}
配好后，`npm run dev`重启服务，访问地址：127.0.0.1:1818

### 配置全局CSS
在开发多页项目时，都会定义一个全局的CSS（例如：重置样式）来初始化我们的页面渲染。要定义这些配置，需要在nuxt.config.js里进行操作。

/assets/css/normailze.css

	html{
		color: red;
	}
/nuxt.config.js

	css:['~assets/css/normailze.css']
/pages/user.vue（使用nuxt.js新建完.vue文件后自动生成路由，无需再配，直接访问即可）

	 
	     
	       Hello QiShon 
	     
	 
重启服务，访问：http://localhost:3000/user

![](https://i.imgur.com/DGQAWqU.png)
### 配置webpack的loader
在nuxt.config.js里是可以对webpack的基本配置进行覆盖的，比如现在我们要配置一个url-loader来进行小图片的64位打包。就可以在nuxt.config.js的build选项里进行配置。

	loaders: [{
      test: /\.(png|jpg?g|gif|svg)$/,
      loader: "url-loader",
      query: {
        limit: 10000,
        name: 'img/[name].[hash].[ext]'
      }
    }]
## Nuxt的路由配置和参数传递

### 简单路由
在pages文件下新建两个文件夹，about和news

在about文件夹下新建index.vue文件

	 
	     
	       About Index page 
	       
	          HOME  
	       
	     
	 
在news文件夹下新建index.vue文件

	 
	   
	     News Index page 
	     NewsID: {{$route.params.newsId}} 
	     
	        HOME  
	     
	   
	 
修改原来的pages文件夹下的index.vue

	 
	   
	     
	        HOME  
	        ABOUT  
	        NEWS  
	     
	   
	 
	
	 
	export default {
	  components: {
	  }
	}
	 
	
	 
	 
`nuxt-link`标签

虽然上面的例子跳转已经成功，但是Nuxt.js并不推荐这种` `标签的作法，它为我们准备了` `标签（vue中叫组件）。我们先把首页的` `标签替换成` `。

	  HOME  
 	  ABOUT  
 	  NEWS  
params传递参数

修改pages下的Index.vue文件，给新闻的跳转加上params参数，传递3306ID。

	  NEWS  
在news文件夹下的index.vue里用$route.params.newsId进行接收

	 NewsID: {{$route.params.newsId}} 

![](https://i.imgur.com/OvuGivw.png)
## Nuxt的动态路由和参数校验
### 动态路由
在news文件夹下新建_id.vue的文件

/pages/news/_id.vue
	 
	     
	       News-content 
	       NewsId: {{$route.params.id}} 
	       
	          HOME  
	       
	     
	 
在/pages/news/index.vue增加两个路由news-1和news-2

	  news-1  
      news-2  
### 动态参数校验
进入/pages/news/_id.vue页面，对参数传递的正确性校验，利用Nuxt.js提供的校验方法validate()

/page/news/_id.vue

	 
	  export default {
	    validate({params}){
	      return /^\d+$/.test(params.id);	//对参数进行数字校验
	    }
	  }
	 
修改/pages/news/index.vue中的news-2参数，改为字符串

	  news-2  
结果校验返回false进入Nuxt提供的404页面。

![](https://i.imgur.com/jhFBJtj.png)
## Nuxt的路由动画效果
路由的动画效果=页面的更换效果

Nuxt.js提供两种方法为路由提供动画效果，一种是全局的、一种是针对单独页面制作。

现在需要完成一个进入和退出时的渐隐渐现效果。

/assets/css/normailze.css

	html{
	  color: red;
	}
	.page-enter-active, .page-leave-active{
	  transition: opacity 2s;
	}
	.page-enter, .page-leave-active{
	  opacity: 0;
	}
然后再nuxt.config.js中加入全局的css文件

	css: ['~assets/css/normailze.css'], // ~ 通配符匹配根目录
这时页面切换就会有2秒动画效果（必须是通过` `链接的）

/pages/news/index.vue

	  HOME  
      news-1  
单独设置页面动效

/assets/css/normailze.css

	.test-enter-active, .test-leave-active{
	  transition: all 2s;
	  font-size: 12px;
	}
	.test-enter, .test-leave-active{
	  opacity: 0;
	  font-size: 40px;
	}
about/index.vue

	export default {
	  transition:'test'
	}
这时about中的路由切换就具有独立的动效。
## Nuxt的默认模板和默认布局
默认模板

在根目录下新建app.html

	 
	 
	 
	    {{HEAD}}
	 
	 
	   QiShon 
	  {{APP}}
	 
	 

![](https://i.imgur.com/3XrqH7I.png)

这里{{HEAD}}读取的是nuxt.config.js里的信息，{{APP}}就是我们写的pages文件夹下的主体页面。这边均需要大写，否则报错。

默认布局

与默认模板功能类似，即layouts/default.vue文件，修改文件内容

	 
	   
	     启尚 
	     
	   
	 

![](https://i.imgur.com/pjJeldi.png)

这里` `就相当于我们每个页面的内容。

总结：要区分默认模板和默认布局的区别，模板可以定制很多头部信息，包括IE版本的判断；默认布局只能定制` `里的内容，跟布局有关系。
## Nuxt的错误页面和个性meta设置
用户输入路由错误时，需要有一个明确指引，即404页面

建立错误页面

layouts/error.vue

	 
	   
	       404页面不存在 
	       500服务器错误 
	       
	            HOME  
	       
	   
	 
	 
	 
	export default {
	  props:['error'],
	}
	 
个性meta设置

页面Meta对于SEO的设置非常重要，假如希望对每个页面设置不同的title和meta。直接使用head方法来设置当前页面的头部信息就可以。

举个栗子：把New-1这个页面设置成个性meta和title

pages/news/index.vue页面的链接进行修改，传入一个title，然后再新闻具体页面接收，形成文章标题。

	  News-1  
修改/pages/news/_id.vue，让它根据传递值变成独特的meta和title标签

	data(){
      return {
        title: this.$route.params.title
      }
    },
    head(){
      return {
        title: this.title,
        meta: [{
          hid: 'bbb',
          name: 'news1',
          content: 'This is news page'
        }]
      }
    }
## asyncData方法获取数据

在项目中需要在初始化页面前先得到数据，也就是异步请求数据。Nuxt.js提供了asyncData

在myjson.com创建远程数据

	{
	  "name": "qishon",
	  "age": 18,
	  "interest": "I LOVE CODING"
	}
然后会得到一个地址，即上面的JSON仓库的地址

安装Axios

	npm install axios --save
asyncData的promise方法，新建pages/asyncData.vue

	 
	     
	       姓名：{{info.name}} 
	       年龄：{{info.age}} 
	       兴趣：{{info.interent}} 
	     
	 
	
	 
	    import axios from 'axios';
	    export default {
	        data() {
	            return {
	                name: 'Hello World!!!'
	            }
	        },
	      asyncData(){
	          return axios.get('https://api.myjson.com/bins/ssran')
	            .then((res)=>{
	              return {
	                info: res.data
	              }
	            })
	        }
	    }
	 
![](https://i.imgur.com/JP3gOSB.png)

asyncData的await方法（推荐采用）

	 
	     
	       姓名：{{info.name}} 
	       年龄：{{info.age}} 
	       兴趣：{{info.interent}} 
	     
	 
	
	 
	    import axios from 'axios';
	    export default {
	        data() {
	            return {
	                name: 'Hello World!!!'
	            }
	        },
	      async asyncData(){
	          let {data} = await axios.get('https://api.myjson.com/bins/ssran');
	          return {info: data}
	      }
	    }
	 
## 静态资源和打包
下载一张logo图片放到项目中static文件夹，然后再index.vue中引用

	 
       
     
![](https://i.imgur.com/yNqG7tg.png)

“~”相当于定位到了项目根目录，这样做图片路径不会出现错误。

CSS引入图片，index.vue

	.diss{
	    width: 300px;
	    height: 100px;
	    background-image: url('~static/logo.png');
	}
正常看到背景图

![](https://i.imgur.com/Jyunkb3.png)

打包静态HTML并运行

	npm run generate
生成dist文件夹，拷出来单独运行（用idea打开，安装一个简单服务器live-server）

	npm install -g live-server
然后再dist文件夹下运行`live-server`命令启动服务，默认端口8080

访问：localhost:8080查看效果

![](https://i.imgur.com/Jyunkb3.png)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)