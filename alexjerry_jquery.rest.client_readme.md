#RestClient
===============

这是一个用于快速方便的访问RESTful接口的JQuery组件

特点
----------------

1. 内置多套默认请求模型,通过更少的代码就可以生成Rest请求
2. 自动完成对象的序列化和反序列化
3. 灵活的可叠加的配置管理
4. 自动进行的参数转义替换和url构建​

快速开始
----------------
```html
  
  
 
    //修改默认设置
    $.rest.updateOptions({
        baseUrl:'http://localhost:8080/rest/',
        error: function(errMessage){
            alert(errMessage);
        }
    });
    
    $(function(){
        // 发送一个GET请求到 http://localhost:8080/rest/my_resources/100
        // 请求时 url 中的占位符 {id} 会自动被 urlParams 中的同名属性替换掉
        $.rest.get({
            url: 'my_resources/{id}',
            urlParams: {id:100},
            success: function(data){
                alert(data.name);
            }
        });
    });
 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)