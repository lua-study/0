# abp代码生成器

#### 介绍

生成器集成与visual studio，操作流程：解决方案管理器-> 选择实体类文件 ->右键类文件->生成abp后端、生成vue前端代码。操作简单、完美的和vs解决方案集成，无需生成文件后再添加一个个添加现有项目。
* 基于vs插件visx 生成abp后端代码、vue-element-ui前端代码，使用vs提供的DTE2对象获取类(领域模型)的类名、属性、特性、字段类型、字段名称。生成的源码文件分为“新增文件”和“编辑文件”，其中新增文件
：使用razor模板引擎生成，编辑文件：后端.cs文件通过AppAuthorizationProviderProjectItem获取，修改保存对象；前端：使用自定义{#insertcode}模板替换

* 参考源码 不弃 / abpCodeBuilder，修复razor生成速度极慢的问题，使用 RazorEngine.Roslyn.RoslynCompilerServiceFactory() 解决。

* 后端生成的文件包括：Server.EntityframeworkCore.EntityMapper、Authoriztion.Permissions、Authoriztion.AppAuthorizationProvider、ApplicationService、IApplicationService、Application.Dto.CreateOrUpdateInputDto、Server.Application.Dto.DtoProfile、Server.Application.Dto.EditDto、Application.Dto.GetForEditOutputDto、Application.Dto.GetsInput、Application.Dto.ListDto

* 前端生成生成的文件包括：Vue.Store.Module、Vue.View.CreateOrUpdateComponent、Vue.View.Index

* 简单的使用partial部分类来整理生成前端、后端的源码

* 更多ABP应用点击查看 [基于ABP和Vue-Element-Admin的通用后台权限和工作流框架](https://gitee.com/fq_chenzhen/base-abp-auth-workflow-opensouce)

* 图片演示

后端生成
![后端生成](https://gitee.com/fq_chenzhen/abp_code_generator/raw/master/images/codebuild-back.gif)

前端生成
![前端生成](https://gitee.com/fq_chenzhen/abp_code_generator/raw/master/images/codebuild-front.gif)


代码生成器生成的效果 
![代码生成器生成的效果](https://gitee.com/fq_chenzhen/base-abp-auth-workflow-opensouce/raw/master/_screenshots/codeGen.gif)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)