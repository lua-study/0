# Pagination

基于 jQuery 的简单 JavaScript 分页组件

# 使用方法

1.  引用`jQuery`

```html
    
```

2.  引用`Pagination`

```html
    
```

3.  页面指定分页组件容器：可以使用`class`或`id`，实现多个分页

```html
   
      
   
```

4.  实例化分页组件

```javascript
const pageSize = 10 // 默认页码大小
const dataCount = 95 // 测试数据数量
const pager = new Pagination('.page-container', {
  pageSize: pageSize,
  autoLoad: true,
  unit: '条',
  toPage: function(index, _pageSize) {
    // 设置记录总数，用于生成分页HTML内容
    if (index === 0 || _pageSize) this.updateCount(dataCount, _pageSize)

    // 根据页码以及分页大小生成html内容
    let pageListHtml = ''
    for (var i = 0; i  
             
               
                 Card - ${index *
                  (_pageSize || pageSize) +
                  i +
                  1} 
                 card-text,card-text,card-text,card-text 
               
             
           
        `
    }
    $('.page-list').html(pageListHtml)
  }
})
```

5. 查看效果：[JavaScript分页组件](https://liverwang.github.io/Pagination/src/index.html)

# 兼容性
> chrome
> firefox
> safari
> edge
> ie9以上

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)