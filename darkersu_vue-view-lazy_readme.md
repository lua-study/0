# vue-view-lazy
原文链接：[gitee.com](https://gitee.com/cncgx/vue-view-lazy)


基于vue的懒加载插件

> 目的：图片或者其他资源进入可视区域后加载
## 注意
 >该插件依赖`IntersectionObserver API`，如需在较低版本浏览器运行，需要引入 polyfill


## 安装使用

1. 直接下载`dist`目录下的[vue-view-lazy.min.js](https://gitee.com/cncgx/vue-view-lazy/blob/master/dist/vue-view-lazy.min.js)使用
2. 使用npm安装

### 直接使用
``` html
 
      
 
  
  
 
    Vue.use(vViewLazy.default,{});
    new Vue({
        el:'#app',
        data:{
            msg:'数据'
        },
        methods:{
            handleModel(){
                console.log('出现了');
            },
        },
    })
 
```
### npm:
``` bash
$ npm install --save-dev vue-view-lazy
```
### 引入vue-view-lazy
.main文件
``` html
import vView from 'vue-view-lazy'
Vue.use(vView,{
    error:'../../static/images/loading.png',
    loading:'../../static/images/loading.gif',
});
```
### 懒加载图片
.vue文件
``` html
 
     
         
             
         
     
 

 
    export default {
        data () {
            return {
                msg: 'Welcome to Your Vue.js App',
                imgs:[
                    {src:'../../static/images/img1.jpg'},
                    {src:'../../static/images/img2.png'},
                    {src:'../../static/images/img2.jpg'},
                    {src:'../../static/images/img3.jpg'},
                    {src:'../../static/images/img4.jpg'},
                    {src:'../../static/images/img5.jpeg'},  
                ]
            }
        },
        mounted(){
        },
    }
 
 
    ...
 
```
### 懒加载数据
.vue文件
``` html
 
     
         
         method(e,...arg)'-->
         getAjaxContent(e,v.msg)">
            loading...
         
         
            loading...
         
     
 

 
    export default {
        data(){
            return{
                msg:[]
            }
        },
        mounted(){
            fetch('http://localhost:3000/test').then(res=>res.json()).then(res=>{
                this.msg = res;
            })
        },
        methods:{
            getAjaxContent(event,msg){
                event.innerText = msg
            },
        }
    }
 

 
    .cnt {
        /*background: #ececec;*/
        height: 500px;
        margin-bottom: 50px;
    }
 
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)