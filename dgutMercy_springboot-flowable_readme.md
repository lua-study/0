# springboot-flowable 

#### 介绍
springboot-flowable  快速开发工作流

#### 软件架构
springboot + flowable + modeler + idm

springboot version : 2.1.5

flowable version : 6.4.0

==注意:== 版本需于数据库 act_ge_property 相同 

​		需要先登录 http://127.0.0.1:8080/expense/idm/index.html

​		account: admin

​		pwd : test
​	 再访问:    创建设计器


#### 使用说明

1. 将flowable的依赖加入到POM中即可,flowable使用需要一个数据库，这里为了方便我选择mysql
2. 增加 mybatis, modeler,idm 等配置

~~~xml
  
         1.8 
         6.4.0 
         1.3.1 
     

     
         
             org.springframework.boot 
             spring-boot-starter-web 
         
         
         
             org.flowable 
             flowable-spring-boot-starter-basic 
             ${flowable.version} 
         
         
         
             mysql 
             mysql-connector-java 
             8.0.11 
         

         
         
             org.mybatis.spring.boot 
             mybatis-spring-boot-starter 
             ${mybatis-spring-boot} 
         
         
             com.alibaba 
             druid 
             1.0.31 
         
         
             log4j 
             log4j 
             1.2.17 
         
         
             com.alibaba 
             fastjson 
             1.2.46 
         
         
             org.springframework.boot 
             spring-boot-starter-thymeleaf 
         
         
             org.flowable 
             flowable-ui-common 
             ${flowable.version} 
         
         
             org.flowable 
             flowable-ui-modeler-rest 
             ${flowable.version} 
         
         
             org.flowable 
             flowable-idm-spring-configurator 
             ${flowable.version} 
         
         
             org.flowable 
             flowable-ui-idm-rest 
             ${flowable.version} 
         
         
             org.flowable 
             flowable-ui-idm-conf 
             ${flowable.version} 
         
         
             org.liquibase 
             liquibase-core 
             3.6.2 
         

         
         
             org.springframework.security 
             spring-security-core 
         
         
             org.springframework.security 
             spring-security-config 
         
         
             org.springframework.security 
             spring-security-crypto 
         
         
             org.springframework.security 
             spring-security-web 
         
         
         
             javax.servlet 
             javax.servlet-api 
             provided 
         
     
     
         
             
                 org.springframework.boot 
                 spring-boot-maven-plugin 
             
         
     
~~~



2.yml 文件配置

增加: idm, modeler , mybatis , servlet 等配置

~~~yml
spring:
  datasource:
    url: jdbc:mysql://127.0.0.1:3306/flowable?autoReconnect=true&useUnicode=true&characterEncoding=utf8&useSSL=false&serverTimezone=CTT
    username: root
    password: 123456
  security:
    filter:
      dispatcher-types: REQUEST,FORWARD,ASYNC
flowable:
  #关闭定时任务JOB
  async-executor-activate: false
  common:
    app:
      idm-url: http://localhost:8080/expense/
  idm:
    app:
      admin:
        user-id: admin
        password: test
        first-name: admin
        last-name: admin
  rest:
    app:
      authentication-mode: verify-privilege
  modeler:
    app:
      rest-enabled: true
  database-schema-update: true
mybatis:
  mapper-locations: classpath:/META-INF/modeler-mybatis-mappings/*.xml
  config-location: classpath:/META-INF/mybatis-config.xml
  configuration-properties:
    prefix:
    blobType: BLOB
    boolValue: TRUE
server:
  servlet:
    context-path: /expense

~~~

这样操作后，flowable与springBoot的整个就完成了！

然后就可以运行了，初次运行时flowable会将自动执行flowable中的初始化脚本完成工作流所需要的数据表的建立，如果指定的数据库中还未创建过flowable的相关数据表的话。



## 定义流程文件

ExpenseProcess.bpmn20.xml

~~~xml
 
 
     
         报销流程 
          
         
             
                 
                      
             
         
          
         
             
                  
             
         
         
             
                  
             
         
          
         
               
         
         
               
         
          
          
         
               500}]]> 
         
         
               
         
         
               
         
         
               
         
     
     
         
             
                  
             
             
                  
             
             
                  
             
             
                  
             
             
                  
             
             
                  
             
             
                  
                  
             
             
                  
                  
             
             
                  
                  
             
             
                  
                  
                  
                  
             
             
                  
                  
             
             
                  
                  
             
             
                  
                  
             
             
                  
                  
                  
             
         
     
 
~~~



其中的两个代理类为：

~~~java
import org.flowable.engine.delegate.TaskListener;
import org.flowable.task.service.delegate.DelegateTask;
 
public class ManagerTaskHandler implements TaskListener {
 
    @Override
    public void notify(DelegateTask delegateTask) {
        delegateTask.setAssignee("经理");
    }
 
}
~~~

~~~java
public class BossTaskHandler implements TaskListener {
 
    @Override
    public void notify(DelegateTask delegateTask) {
        delegateTask.setAssignee("老板");
    }
 
}
~~~



尽管上面的BPMN文件很长，但放心，毕竟那是通过相关的工具生成出来的，对于核心的逻辑部分也很少（主要在process 标签内） ，如需要详细了解的可自行学习下BPMN的标签即可！当然，在flowable的使用文档中也有相关的描述,详见：Creating a ProcessEngine
--------------------- 


![微信图片_20190521103749](assets/微信图片_20190521103749.png)





#### 这样当此框架启动的时候它会默认加载resource目录下的processes时就可以将此流程配置加载到数据库进行持久化了



# 测试controller

为了方便这里通过一个controller来完成此DEMO的快速编写



~~~java
@Controller
@RequestMapping(value = "expense")
public class ExpenseController {
    @Autowired
    private RuntimeService runtimeService;
    @Autowired
    private TaskService taskService;
    @Autowired
    private RepositoryService repositoryService;
    @Autowired
    private ProcessEngine processEngine;
 
/***************此处为业务代码******************/
}

~~~



~~~java
/**
     * 添加报销
     *
     * @param userId    用户Id
     * @param money     报销金额
     * @param descption 描述
     */
    @RequestMapping(value = "add")
    @ResponseBody
    public String addExpense(String userId, Integer money, String descption) {
        //启动流程
        HashMap  map = new HashMap<>();
        map.put("taskUser", userId);
        map.put("money", money);
        ProcessInstance processInstance = runtimeService.startProcessInstanceByKey("Expense", map);
        return "提交成功.流程Id为：" + processInstance.getId();
    }
~~~



~~~java
/**
     * 获取审批管理列表
     */
    @RequestMapping(value = "/list")
    @ResponseBody
    public Object list(String userId) {
        List  tasks = taskService.createTaskQuery().taskAssignee(userId).orderByTaskCreateTime().desc().list();
        for (Task task : tasks) {
            System.out.println(task.toString());
        }
        return tasks.toArray().toString();
    }
~~~

~~~java
/**
     * 批准
     *
     * @param taskId 任务ID
     */
    @RequestMapping(value = "apply")
    @ResponseBody
    public String apply(String taskId) {
        Task task = taskService.createTaskQuery().taskId(taskId).singleResult();
        if (task == null) {
            throw new RuntimeException("流程不存在");
        }
        //通过审核
        HashMap  map = new HashMap<>();
        map.put("outcome", "通过");
        taskService.complete(taskId, map);
        return "processed ok!";
    }
~~~

~~~java
 /**
     * 拒绝
     */
    @ResponseBody
    @RequestMapping(value = "reject")
    public String reject(String taskId) {
        HashMap  map = new HashMap<>();
        map.put("outcome", "驳回");
        taskService.complete(taskId, map);
        return "reject";
    }
~~~

~~~java
 /**
     * 生成流程图
     *
     * @param processId 任务ID
     */
    @RequestMapping(value = "processDiagram")
    public void genProcessDiagram(HttpServletResponse httpServletResponse, String processId) throws Exception {
        ProcessInstance pi = runtimeService.createProcessInstanceQuery().processInstanceId(processId).singleResult();
 
        //流程走完的不显示图
        if (pi == null) {
            return;
        }
        Task task = taskService.createTaskQuery().processInstanceId(pi.getId()).singleResult();
        //使用流程实例ID，查询正在执行的执行对象表，返回流程实例对象
        String InstanceId = task.getProcessInstanceId();
        List  executions = runtimeService
                .createExecutionQuery()
                .processInstanceId(InstanceId)
                .list();
 
        //得到正在执行的Activity的Id
        List  activityIds = new ArrayList<>();
        List  flows = new ArrayList<>();
        for (Execution exe : executions) {
            List  ids = runtimeService.getActiveActivityIds(exe.getId());
            activityIds.addAll(ids);
        }
 
        //获取流程图
        BpmnModel bpmnModel = repositoryService.getBpmnModel(pi.getProcessDefinitionId());
        ProcessEngineConfiguration engconf = processEngine.getProcessEngineConfiguration();
        ProcessDiagramGenerator diagramGenerator = engconf.getProcessDiagramGenerator();
        InputStream in = diagramGenerator.generateDiagram(bpmnModel, "png", activityIds, flows, engconf.getActivityFontName(), engconf.getLabelFontName(), engconf.getAnnotationFontName(), engconf.getClassLoader(), 1.0);
        OutputStream out = null;
        byte[] buf = new byte[1024];
        int legth = 0;
        try {
            out = httpServletResponse.getOutputStream();
            while ((legth = in.read(buf)) != -1) {
                out.write(buf, 0, legth);
            }
        } finally {
            if (in != null) {
                in.close();
            }
            if (out != null) {
                out.close();
            }
        }
    } 
~~~

通过传入流程ID生成当前流程的流程图给前端,如果流程中使用到中文且生成的图片是乱码的，则需要进配置下字体：

~~~java
/**
 * @author haiyangp
 * date:  2018/4/7
 * desc: flowable配置----为放置生成的流程图中中文乱码
 */
@Configuration
public class FlowableConfig implements EngineConfigurationConfigurer  {
 
    @Override
    public void configure(SpringProcessEngineConfiguration engineConfiguration) {
        engineConfiguration.setActivityFontName("宋体");
        engineConfiguration.setLabelFontName("宋体");
        engineConfiguration.setAnnotationFontName("宋体");
    }
} 
~~~



#### 测试请求

1.先启动好此项目，然后创建一个流程：

访问：http://localhost:8080/expense/expense/add?userId=123&money=123321

返回：提交成功.流程Id为：2501

 

2.查询待办列表:

访问：http://localhost:8080/expense/expense/list?userId=123

输出：Task[id=2507, name=出差报销]

 

3.同意： 

​	==注意 : 带的是taskid==

访问：http://localhost:8080/expense/expense/apply?taskId=2507

返回：processed ok!

 

4.生成流程图：

访问: http://localhost:8080/expense/expense/processDiagram?processId=2501

![](assets/return_process_img.png)





#### 流程设计器 modeler

解压 idm, modeler war包  导入两个war中的 static 包下的文件

![](assets/idm和modeler的静态文件.png)



#### 重写两个配置类
AppDispatcherServletConfiguration.java
ApplicationConfiguration
springboot 启动类 import 两个配置类

~~~java
![说明](assets/说明.png)@Import({
        ApplicationConfiguration.class,
        AppDispatcherServletConfiguration.class
})
@ComponentScan(basePackages = {"com.example.demo"})
@EnableTransactionManagement
@SpringBootApplication
public class DemoApplication {

    public static void main(String[] args) {
        SpringApplication.run(DemoApplication.class, args);
    }

}
~~~



![](assets/说明.png)

#### 添加国际化文件

![](assets/国际化文件.png)



#### 资源文件配置

~~~yml
spring:
  datasource:
    url: jdbc:mysql://127.0.0.1:3306/flowable?autoReconnect=true&useUnicode=true&characterEncoding=utf8&useSSL=false&serverTimezone=CTT
    username: root
    password: 123456
  security:
    filter:
      dispatcher-types: REQUEST,FORWARD,ASYNC
flowable:
  #关闭定时任务JOB
  async-executor-activate: false
  common:
    app:
      idm-url: http://localhost:8080/expense/
  idm:
    app:
      admin:
        user-id: admin
        password: test
        first-name: admin
        last-name: admin
  rest:
    app:
      authentication-mode: verify-privilege
  modeler:
    app:
      rest-enabled: true
  database-schema-update: true
mybatis:
  mapper-locations: classpath:/META-INF/modeler-mybatis-mappings/*.xml
  config-location: classpath:/META-INF/mybatis-config.xml
  configuration-properties:
    prefix:
    blobType: BLOB
    boolValue: TRUE
server:
  servlet:
    context-path: /expense

~~~









#### 参与贡献

1. Fork 本仓库
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request


#### 码云特技

1. 使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2. 码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3. 你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4. [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5. 码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6. 码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)