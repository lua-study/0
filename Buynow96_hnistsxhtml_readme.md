#开发说明

##模块开发
```
 
      
     账户管理 
 
```
### 对要开发的模块增加ID firstLoad 当进入index时直接进入该模块；
### 模块模板参考 view/template.html 文件
### 对模块需要异步加载页面使用属性data-ref="view/accountManager.html"
* 第一个参数为异步加载页面地址，第二个参数固定为this;
* 规范将内容里的页面放置于view目录下;

## 模块划分

### 实训动态
#### 新闻咨询
展示实训新闻，作为展示;
#### 通知公告
实训相关的通知公告，教师将直接发布各实训课题的详细信息到此，可下载附件;
### 实训管理
#### 选择实训
学生选择实训课题;
#### 日志发布
每日实训日志发布;
#### 发布月刊
小组长发布实训情况的月刊;
#### 实训成绩
公布实训成绩;
### 用户中心
#### 个人信息
展示账户信息、补充个人信息、修改密码、查看选课情况;

## 功能规范
### 通知功能
* 使用notify插件

```
//成功
$.notify("选择实训课题成功，请前往个人信息查证!", {
    //位置 'bottom left' 即为左下角弹出
    position:'top',
    className:'success'
});
//失败
$.notify("选择实训课题失败，请前重新选择!",{
    position:'top',
    className:'error'
});
//className 包括success、info、warn、error几种类型
```
### 弹窗

```
 
 
  Launch demo modal
 

 
 
   
     
       
          &times;  
         Modal title 
       
       
        ...
       
       
         Close 
         Save changes 
       
     
   
 
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)