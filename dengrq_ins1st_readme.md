 
     
        ins1st是一款Java快速开发平台，基于Springboot2.X、Beetl、Mybatis-Plus、Shiro、Redis、JWT等众多优秀框架开发而成，包含了代码生成让您一键生成出通用的CRUD后台代码以及前台页面，前端采用Beetl进行封装让您更加方便使用各个元素，界面简洁美观代码通俗易懂，是一款容易上手的后台手脚架！
               
         
         
             
           
         
             
         
         
             
           
         
             
          
         
             
               
     
 

-----------------------------------------------------------------------------------------------
 **最新分布式版本:INS1ST-PLUS https://gitee.com/sdjwj1118/ins1st-plus** 
 
 **最新分布式版本:INS1ST-PLUS https://gitee.com/sdjwj1118/ins1st-plus** 
 
 **最新分布式版本:INS1ST-PLUS https://gitee.com/sdjwj1118/ins1st-plus** 
 
 **最新分布式版本:INS1ST-PLUS https://gitee.com/sdjwj1118/ins1st-plus** 
 
 **最新分布式版本:INS1ST-PLUS https://gitee.com/sdjwj1118/ins1st-plus** 
 
 **最新分布式版本:INS1ST-PLUS https://gitee.com/sdjwj1118/ins1st-plus** 
 
 **最新分布式版本:INS1ST-PLUS https://gitee.com/sdjwj1118/ins1st-plus** 
 
### 交流讨论群
1.  QQ：701657098 

### 账号密码
1.  admin/admin

### 进度声明
1. 5.11 新增MyBatis——PLus多数据源(暂不支持一个方法下多数据源统一事务管理)
2. 5.12 集成jwt 新增api模块，具体查看api模块
3. 5.13 去除mybatisplus的多数据源启动器，改为其他方式
3. 5.14 集成redis 手动开关session是否由redis管理
5. 5.16 修复bug 因为mp3.x把''空字符也传入到sql查询 所以新增ControllerUtil处理''

### 版权声明
INS1ST协议：您可以随意下载，学习，或商业使用，但禁止二次包装出售。

### 前端模板
INS1ST所用前端模板为Xadmin后台开发框架,官网地址为：[http://x.xuebingsi.com/](http://x.xuebingsi.com/)。

### 如有帮助，请多star
如果INS1ST对您有所帮助，请`star`一下项目！支持一下作者！感谢！

### 管理系统功能
1. 用户管理 2.角色管理 3.菜单管理 4.字典管理 5.业务日志 6.登录日志 7.监控管理 8.通知管理 9.代码生成

### 项目特点
1. 基于SpringBoot，简化了大量项目配置和maven依赖，让您更专注于业务开发，独特的分包方式，代码多而不乱。
2. INS1ST特有@Req4Model和@Req4Json注解，整合了@RequestMapping和@ResponseBody注解在原基础上添加了log日志,编码的时候一个注解完成映射、转json以及日志记录
例子如下, title为日志名称 params是需要记录的参数,多个用逗号分开
```
        /**
        * 保存
        *
        * @param sysBizLog
        * @return
        */
        @Req4Json(value = "/save",title="保存业务日志",params="id")
        public Object save(SysBizLog sysBizLog) {
            boolean save = sysBizLogService.save(sysBizLog);
            if (save) {
                return R.success("保存成功");
            }
            return R.error("保存失败");
        }
```

3. beetl对常用的应用元素进行封装
详情见resouces/templates/common/tags
例如
```
     
     
     
     
     
     
     
```
4.多数据源使用方式
```
    @Service("testService")
    @Transactional
    public class TestService {
    
        @Autowired
        TestMapper testMapper;
    
        @DataSource(db = "slave")
        public void test() {
            Test test = new Test();
            test.setAaa("111");
            test.setBbb("111");
            testMapper.in
        }
    }
```
### INS1ST效果图
![输入图片说明](https://images.gitee.com/uploads/images/2019/0510/161931_58286765_756207.jpeg "1EA5DEF581CFEF4E886F87514CCB2798.jpg")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0510/161944_4e9a7ea9_756207.jpeg "4D9E3127C0BFC907ABDBA493E7EE03C0.jpg")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0510/161951_c6c55704_756207.jpeg 
"46B262C8A7CCFFB375FDCB20E55D9E51.jpg")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0510/162015_bc9bfa6e_756207.jpeg "4227E251189E3F2A8C865FCF82E19E78.jpg")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0510/162032_fc9a40e0_756207.jpeg "5876F5928EE590927190DD751CB75CF2.jpg")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0510/162039_50525ed8_756207.jpeg "A7D48BECCEE0DB0244AF3A39E920C99A.jpg")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0510/162049_84ad09bb_756207.jpeg "C449561F3100C0DC70D0AD3F9A27AC28.jpg")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0510/162059_b4238b0a_756207.jpeg "CD1FB28EA9B31CB1BE720C86F015F73A.jpg")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)