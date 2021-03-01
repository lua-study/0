[whoami代码论坛(码谈)](http://106.52.166.52)
===============
### 资料
[Spring 文档](https://spring.io/guides)    
[Spring Web](https://spring.io/guides/gs/serving-web-content/)  
[菜鸟教程](https://www.runoob.com/mysql/mysql-insert-query.html)    

[Spring Dev Tool](https://docs.spring.io/spring-boot/docs/2.0.0.RC1/reference/htmlsingle/#using-boot-devtools)  
[Spring MVC官网](https://docs.spring.io/spring/docs/5.0.3.RELEASE/spring-framework-reference/web.html#mvc-handlermapping-interceptor)  
 
#### BootStrap


#### 工具
[lombok的安装和使用](https://blog.csdn.net/motui/article/details/79012846)    
[Markdown 插件](http://editor.md.ipandao.com/)  
[REST API测试 Chrome插件](http://www.cnplugins.com/devtool/restlet-client-rest-api-t/)

码谈介绍(完善中...)
----------------------
#### 界面设计模块
1. 使用bootstrap设计简单的响应式页面
    + 下载bootstrap官方资源包
    + 引入项目所需资源
    + 根据官方文档使用相应的组件
    + [BootStrap](https://v3.bootcss.com/components/)     
    + [栅格系统](https://v3.bootcss.com/css/#grid)

#### 登录功能模块
[github官网](https://github.com/)     
[github OAuth](https://developer.github.com/apps/building-oauth-apps/creating-an-oauth-app/)
1. 用户点击登录按钮     
    使用github的登录授权，发送请求，请求调用authorize接口，需要提供的参数
    + client_id：github自动生成
    + redirect_uri：回调接口地址
    + state=1
    + scope=user
1. github自动跳转到设置的callback接口中，并携带参数code
1. 然后调用github提供的access_token接口，需要提供参数，将数据传的参数封装成AccessTokenDTO
    + client_id：github生成
    + client_secret：github生成
    + code: github回调返回的参数
    + redirect_uri：回调接口地址
    + state=1
1. 使用OkHttp所提供的类将请求设为post请求
    + https://github.com/login/oauth/access_token
    ``` java
   Request request = new Request.Builder()
                   .url("https://github.com/login/oauth/access_token")
                   .post(body)
                   .build(); 
   ```
1. 再次将返回的access_token使用get方式请求github提供的user接口
    + https://api.github.com/user?access_token=xxx
    ``` java
   Request request = new Request.Builder()
                   .url("https://api.github.com/user?access_token="+accessToken)
                   .build(); 
   ```
   注：该方法即将弃用，后续更新使用方法
1. 最后返回github用户参数，存入数据库，更新登录状态。

### 论坛发布、修改、分页展示模块
1. 前提条件：已登录用户。
1. 将问题信息封装成QuestionDTO，并添加Lombok支持，减少代码getter/setter等方法的编写。
    ``` java
   @Data
   public class QuestionDTO {
       private Long id;
       private String title;
       private String description;
       ......
   }
    ```
1. 发布问题之前的校验
    ``` java
    //校验输入是否为空
    if (title == null || title.equals("")) {
        model.addAttribute("error","标题不能为空");
        return "publish";
    } 
   //其他校验
   ......
   ```
1. 使用thymeleaf+Bootstrap+Jquery解析数据解析美化发布问题页面
    + [Thymeleaf](https://www.thymeleaf.org/doc/tutorials/3.0/usingthymeleaf.html#setting-attribute-values)    
    + [JQuery](https://www.runoob.com/jquery/jquery-tutorial.html)
1. 实现我的问题列表以及首页分页展示示例
    + 使用mybatis-generator自动生成代码的插件实现分页等多种功能
    ``` java
   QuestionExample example = new QuestionExample();
           example.createCriteria()
                   .andCreatorEqualTo(userId);
           example.setOrderByClause("gmt_create desc");
           List  questions = questionMapper.selectByExampleWithRowbounds(example, new RowBounds(offset, size)); 
   ```
    + [插件github地址](https://github.com/mybatis/generator)  
    + [使用教程](https://blog.csdn.net/testcs_dn/article/details/77881776)

### 多级回复、浏览数及评论点赞功能
1. 数据表设计采用单表设计
    + 通过type属性指定评论为问题评论还是评论回复
    + 通过parent_id在单表中指定级联关系
1. 问题显示页面
    + 首次进入问题页面应保证效率,仅展示一级评论,即问题的回复
    + 每条评论显示有点赞数及评论数,用户可点击评论查看二级评论,并显示出二级评论窗口
1. 每访问一次问题详情页浏览数+1
    ``` java
   /**
    * 根据id查询到问题，对问题的浏览数+1
    * @param id
    */
    public void incview(Long id) {
        Question question = new Question();
        question.setId(id);
        question.setViewCount(1);
        questionExtMapper.incView(question);
    } 
   ```
1. 将点赞数量保存至Redis数据库中
    ``` java
    //被点赞数+1
    @Override
    public void incrementLikedCount(String likedUserId) {
        redisTemplate.opsForHash().increment(RedisKeyUtil.MAP_KEY_USER_LIKED_COUNT,likedUserId,1);
    } 
   ```

### Tag标签库完善
1. 将所有标签封装成TagCache
2. 不允许提交问题时输入非法标签
    ``` java
   //校验标签的合法性
    String invalid = TagCache.filterInvalid(tag);
    if (StringUtils.isNotBlank(invalid)){
        model.addAttribute("error","输入非法标签"+invalid);
        return "publish";
    }
    ```
3. 焦点移动到标签时，弹出选择标签，用户选择符合自己的标签进行添加
4. 标签与标签之间用逗号分隔

### 通知回复功能模块
1. createNotify(创建通知)
    + 每当有一次评论请求成功时,同时创建一条通知,保存parent_id问题的id,设置状态为未读,在通知页面显示评论内容及评论人
    + 使用Spring事务进行管理,保证评论与通知的原子性
    ``` java
   @Transactional
    public void  insert(Comment comment, User commentator){
   //创建通知
   createNotify(......);
   }
   private void createNotify(Comment comment, ......) { 
   ......
   }
   ```
1. 评论数增加
1. 通知条数及内容展示
    + 使用拦截器查询当前用户在数据库中通知的未读条数,放入Session中
    + 用户请求通知列表，展示所有被评论的信息
    + 用户点击某条通知时，根据parent_id,
    转发请求到question页面并将该通知状态置为已读

### 集成Markdown富文本编辑器
1. 开源在线Markdown编辑器
    + [Markdown](https://pandao.github.io/editor.md/)
1. 引入使用编辑器的基本样式及必须资源
1. 示例：
``` html
 
    $(function () {
        var editor = editormd("question-editor", {
            width: "100%",
            height: 350,
            path: "/js/lib/",
            delay: 0,
            syncScrolling : "single",
            placeholder: "请输入问题描述",
            imageUpload: true,
            imageFormats: ["jpg", "jpeg", "gif", "png", "bmp", "webp"],
            imageUploadURL: "/file/upload",
            saveHTMLToTextarea : true
        });
    });
 
```
### 7天最热话题&点赞关系存储
1. 引入定时任务
1. 定时查询和存储Redis数据
### ......


------------------------------------
##### 开发日志  
1. 2020/02/15 完成部署    
1. 2020/02/18 添加动态导航栏    
1. 2020/02/20 完善登录用户名为null的情况   
1. 2020/02/24 添加使用Redis实现点赞功能   
1. ......

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)