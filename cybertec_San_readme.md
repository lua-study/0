 
     
         
     
 

 SAN 

 
A Flexible JavaScript Component Framework.  HomePage 
 

 
     
     
     
     
     
 




## Download

NPM:

```
$ npm i san
```

CDN:

```html
  
```

[Dist Files Infomation](https://github.com/ecomfe/san/tree/master/dist)


## Quick Start

```html
 
 

 
     Quick Start 
      
 

 
     
        const MyApp = san.defineComponent({
            template: `
                 
                     
                     Hello {{name}}! 
                 
            `
        });

        let myApp = new MyApp({
            data: {
                name: 'San'
            }
        });
        myApp.attach(document.body);
     
 

 
```


## Document

- [Start](https://ecomfe.github.io/san/tutorial/start/)
- [Tutorial](https://ecomfe.github.io/san/tutorial/setup/)
- [Example](https://ecomfe.github.io/san/example/)
- [API](https://ecomfe.github.io/san/doc/api/)
- [ANode](https://github.com/ecomfe/san/blob/master/doc/anode.md)


## Companions

- [san-devtool](https://github.com/ecomfe/san-devtool/blob/master/docs/user_guide.md) - Chrome DevTool extension
- [san-router](https://github.com/ecomfe/san-router) - SPA Router
- [san-store](https://github.com/ecomfe/san-store) - Application States Management
- [san-update](https://github.com/ecomfe/san-update) - Immutable Data Update Library
- [san-mui](https://ecomfe.github.io/san-mui/) - Material Design Components Library
- [san-xui](https://ecomfe.github.io/san-xui/) - A Set of SAN UI Components that widely used on Baidu Cloud Console


## ChangeLog

Please visit document [ChangeLog](https://github.com/ecomfe/san/blob/master/CHANGELOG.md)


## License

San is [MIT licensed](./LICENSE).


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)