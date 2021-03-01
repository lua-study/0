# avue-plugin-ueditor

## avue 富文本编辑器

## Avue官网
[https://avuejs.com](https://avuejs.com)

## 介绍
[avue-plugin-ueditor](https://avuejs.com/doc/plugins/ueditor-plugins)

## npm
[avue-plugin-ueditor](https://www.npmjs.com/package/avue-plugin-ueditor)

## git
[avue-plugin-ueditor](https://gitee.com/smallweigit/avue-plugin-ueditor)

## demo
 
   
 

## use
```
1.安装
npm install avue-plugin-ueditor --save

2.导入
import AvueUeditor from 'avue-plugin-ueditor'
Vue.use(AvueUeditor);

3.使用(双击图片可改变大小)
...
column:[
  ...
    {
      label:'test',
      prop:'test',
      component: "avueUeditor",
      options:{
        //普通图片上传
        action: "https://avuejs.com/upload",
        props: {
          res: "data",
          url:'url'
        },
        //七牛云oss配置
        qiniu: {
          AK: "",
          SK: "",
          scope: "test",
          url: "http://pm7cc17lu.bkt.clouddn.com/",
          deadline: 1
        },
        //阿里云oss配置
        ali: {
          region: "oss-cn-beijing",
          endpoint: "oss-cn-beijing.aliyuncs.com",
          accessKeyId: "",
          accessKeySecret: "",
          bucket: "avue"
        }
      }
    }
  ...
]
或者直接
  

4.图片上传配置————(支持oss,支持ctrl+v粘贴图片)
具体用法参考https://avuex.avue.top/#/doc/form-upload
upload: {
  //普通图片上传
  action: "https://avuejs.com/upload",
  props: {
    res: "data",
    url:'url'
  },
  //七牛云oss配置
  qiniu: {
    AK: "",
    SK: "",
    scope: "test",
    url: "http://pm7cc17lu.bkt.clouddn.com/",
    deadline: 1
  },
  //阿里云oss配置
  ali: {
    region: "oss-cn-beijing",
    endpoint: "oss-cn-beijing.aliyuncs.com",
    accessKeyId: "",
    accessKeySecret: "",
    bucket: "avue"
  }
}
...
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)