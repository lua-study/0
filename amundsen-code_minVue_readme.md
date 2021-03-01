### 学习vue原理编写的基础功能

### 1.0.7 

- 新增checkbox支持
- 新增:class 语法的支持

```html

.color{
    color: red
}
.bc{
    background: blue
}

 css 

colorKey:true,
bcKey:true

```

#### 1.0.4


- @click 支持参数传递 
- 取消默认接收event
- 目前只能传递一个字符串类型参数

``` html
 计算 
```

##### 1.0

- 需要绑定的数据请挂载到 data
- html 绑定到 v-value
- input 绑定使用 v-module
- 支持@click事件
- 支持v-if

### 安装
浏览器导入
```javascript
  
```

```javascript
npm || yarn
```

```javascript
npm install minVue  
yarn minVue

```

使用

```javascript
import minVue from 'min-vue'

const minVue = require('min-vue')

```

```html
 
     
        单价
         
          
        数量
         
          
        单品总价
          
         计算 
     
     
         1 
         切换显示1 
     
     
         2 
         切换显示2 
     
 
```

```javascript

new minVue({
    el:'#app',
    data:function(){
        return {
            num:'',
            num1:'',
            num3:'',
            li1:true,
            li2:true
        }
    },
    created:function(){
        // console.log('初始化完成')
    },

    methods:{
        onClick:function(){
            this.data.num3 = this.data.num * this.data.num1
        },
        onChangeli1:function(){
            this.data.li1 = !this.data.li1
        },
        onChangeli2:function(){
            this.data.li2 = !this.data.li2
        }
    }
})  
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)