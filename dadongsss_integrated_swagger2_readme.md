 )5.7以下，新旧版本有差异
  - 安装时记得设置初始密码
- [navicat下载](https://pan.baidu.com/s/1gDJwNF4YrxszOz7TeYx3hQ),密码xzrr

#### 创建数据库

```
/*
Navicat MySQL Data Transfer

Source Server         : wxdemo
Source Server Version : 50725
Source Host           : localhost:3306
Source Database       : supermansirts

Target Server Type    : MYSQL
Target Server Version : 50725
File Encoding         : 65001

Date: 2019-03-30 21:10:37
*/

SET FOREIGN_KEY_CHECKS=0;

-- ---------男士衬衫三张表实际使用需要改-------------------
-- Table structure for tb_minfo
-- ----------------------------
DROP TABLE IF EXISTS `tb_minfo`;
CREATE TABLE `tb_minfo` (
  `m_id` int(10) NOT NULL AUTO_INCREMENT,
  `shirt_id` int(10) NOT NULL,
  `record_id` int(10) NOT NULL,
  `user_name` varchar(200) NOT NULL,
  `user_pass` int(30) NOT NULL DEFAULT '0',
  `user_himg` varchar(200) DEFAULT NULL,
  `nick_name` varchar(50) DEFAULT NULL,
  `m_shape` varchar(50) DEFAULT '标准体',
  `m_abdomen` varchar(50) DEFAULT '扁腹',
  `m_shoulder` varchar(50) DEFAULT '耸肩',
  PRIMARY KEY (`m_id`),
  UNIQUE KEY `UK_N` (`user_name`),
  KEY `record_id` (`record_id`)
) ENGINE=InnoDB AUTO_INCREMENT=5 DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of tb_minfo
-- ----------------------------
INSERT INTO `tb_minfo` VALUES ('3', '0', '0', '18822179535', '123456', 'https://ss0.bdstatic.com/-0U0b8Sm1A5BphGlnYG/kmarketingadslogo/49b8e752ae9dbb3a5ed375f1185d7683_250_250.jpg', 'superman1553929794077', '标准体', '扁腹', '耸肩');
INSERT INTO `tb_minfo` VALUES ('4', '0', '0', '15534510036', '123456', 'https://ss0.bdstatic.com/-0U0b8Sm1A5BphGlnYG/kmarketingadslogo/49b8e752ae9dbb3a5ed375f1185d7683_250_250.jpg', 'superman1553930598372', '标准体', '扁腹', '耸肩');

-- ----------------------------
-- Table structure for tb_order
-- ----------------------------
DROP TABLE IF EXISTS `tb_order`;
CREATE TABLE `tb_order` (
  `record_id` int(10) NOT NULL AUTO_INCREMENT,
  `record_time` datetime DEFAULT NULL,
  `record_num` varchar(200) DEFAULT NULL,
  `record_img` varchar(30) DEFAULT NULL,
  `record_season` varchar(50) DEFAULT '夏季',
  `record_scene` varchar(50) DEFAULT '日常',
  PRIMARY KEY (`record_id`), 
  -- 添加外键约束 --
  CONSTRAINT `frc_key` FOREIGN KEY (`record_id`) REFERENCES `tb_minfo` (`record_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of tb_order
-- ----------------------------

-- ----------------------------
-- Table structure for tb_shirt
-- ----------------------------
DROP TABLE IF EXISTS `tb_shirt`;
CREATE TABLE `tb_shirt` (
  `shirt_id` int(10) NOT NULL AUTO_INCREMENT,
  `edition_type` varchar(50) DEFAULT '潮流',
  `shirt_size` varchar(200) DEFAULT '40,175,L',
  `shirt_material` varchar(30) DEFAULT '棉',
  `shirt_color` varchar(200) DEFAULT '黑色',
  `shirt_season` varchar(50) DEFAULT '夏季',
  `shirt_scene` varchar(50) DEFAULT '日常',
  `shirt_img_id` int(10) NOT NULL,
  PRIMARY KEY (`shirt_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of tb_shirt
-- ----------------------------
SET FOREIGN_KEY_CHECKS=1;

```



## 开发工具与helloword

#### [下载idea]( )

#### HelloWrod

- 创建项目

  - 新建项目

     

  - 选包名

  - 选择需要的库

  - 创建项目

- 手动导入模块化(lombok)、热部署包(devtools)

  - 模块化让mapping映射文件也可以通过注解方式实现
  - 热部署修改静态网页应用不会重启

- 找到应用的入口类(初建项目只有一个类里边有main方法)

  - ```
    /*此类使springboot项目可以直接访问controller,即你设置的请求地址*/
    @SpringBootApplication
    public class SpringbootApplication {
    	public static void main(String[] args) {
    		System.out.println("sklahjks");
    		SpringApplication.run(SpringbootApplication.class, args);
    	}
    }
    ```

  - 在配置文件中设置项目访问端口

    - 在resources下的application.properties中添加：server.port=8090

  - 创建第一个controller类并通过浏览器访问

    - ```
      /*新建controller包，在包下新建UserController*/
      @RestController
      public class UserController {
      	//设置访问路径
      	@RequestMapping(value = "/test",method = RequestMethod.GET)
          public String test(){
              return "hello springboot";
          }
      }
      ```

    - 这时启动项目在浏览器输入： 我们就可以看到浏览器有"hello springboot"输出

## 快速开发接口

#### 与数据库的交互

- 配置数据库的连接

  ```
  #设置默认端口
  server.port=8070
  #mybatis扫描默认的实体类方便数据库映射
  mybatis.type-aliases-package=com.supermanshirts.entity
  #旧版本数据库驱动
  #spring.datasource.driverClassName = com.mysql.jdbc.Driver
  #新版本数据库驱动,好像新版本驱动会默认加载
  spring.datasource.driverClassName = com.mysql.cj.jdbc.Driver
  #数据库地址，supermansirts是你创建的数据库名称
  spring.datasource.url = jdbc:mysql://localhost:3306/supermansirts?useUnicode=true&characterEncoding=utf-8&useSSL=false&&serverTimezone=UTC
  #数据库用户名密码
  spring.datasource.username = root
  spring.datasource.password =123456
  ```

- 创建客户端请求的响应实体类

     

  ```
  import lombok.Data;
  import java.io.Serializable;
  /*实体类需要通过Data来注解*/
  @Data
  public class UserEntity implements Serializable {
      /*用户id*/
     private int m_id;
     /*衬衫id*/
     private int shirt_id;
     /*定制订单id*/
     private int record_id;
     /*用户名*/
     private String user_name;
     /*用户密码*/
     private String user_pass;
     /*用户头像*/
     private String user_himg;
     /*用户昵称*/
     private String nick_name;
     /*用户体型*/
     private String m_shape;
     /*用户腹部描述*/
     private String m_abdomen;
     /*用户肩部描述*/
     private String m_shoulder;
  
      public int getM_id() {
          return m_id;
      }
  
      public int getShirt_id() {
          return shirt_id;
      }
  
      public int getRecord_id() {
          return record_id;
      }
  
      public String getUser_name() {
          return user_name;
      }
  
      public String getUser_pass() {
          return user_pass;
      }
  
      public String getUser_himg() {
          return user_himg;
      }
  
      public String getNick_name() {
          return nick_name;
      }
  
      public String getM_shape() {
          return m_shape;
      }
  
      public String getM_abdomen() {
          return m_abdomen;
      }
  
      public String getM_shoulder() {
          return m_shoulder;
      }
  
      public void setM_id(int m_id) {
          this.m_id = m_id;
      }
  
      public void setShirt_id(int shirt_id) {
          this.shirt_id = shirt_id;
      }
  
      public void setRecord_id(int record_id) {
          this.record_id = record_id;
      }
  
      public void setUser_name(String user_name) {
          this.user_name = user_name;
      }
  
      public void setUser_pass(String user_pass) {
          this.user_pass = user_pass;
      }
  
      public void setUser_himg(String user_himg) {
          this.user_himg = user_himg;
      }
  
      public void setNick_name(String nick_name) {
          this.nick_name = nick_name;
      }
  
      public void setM_shape(String m_shape) {
          this.m_shape = m_shape;
      }
  
      public void setM_abdomen(String m_abdomen) {
          this.m_abdomen = m_abdomen;
      }
  
      public void setM_shoulder(String m_shoulder) {
          this.m_shoulder = m_shoulder;
      }
  
      public UserEntity() {
      }
  
      public UserEntity(int shirt_id, int record_id, String user_name, String user_pass, String user_himg, String nick_name, String m_shape, String m_abdomen, String m_shoulder) {
          this.shirt_id = shirt_id;
          this.record_id = record_id;
          this.user_name = user_name;
          this.user_pass = user_pass;
          this.user_himg = user_himg;
          this.nick_name = nick_name;
          this.m_shape = m_shape;
          this.m_abdomen = m_abdomen;
          this.m_shoulder = m_shoulder;
      }
  }
  
  ```

  

- 通过mapper往数据库插入数据和查询数据(这里需要服务层和控制层调用)

  ```
  /*在这里通过mapper映射插入，直接这么做就好，想理解原理请学习spring和springmvc与mybatis整合相关知识*/
  /*新建mapper包，创建UserMapper类,需要Mapper来注解*/
  @Mapper
  public interface UserMapper { 
  	//查询数据库数据
     @Select("SELECT * FROM tb_minfo WHERE user_name = #{username}")
      UserEntity getUserByName(String username);
      //插入数据库数据,前面括号对应数据库字段，后面括号对应实体类这里两边字段相同
      @Insert("INSERT INTO tb_minfo(shirt_id,record_id,user_name,user_pass,user_himg,nick_name,m_shape,m_abdomen,m_shoulder" +
              ") VALUES(#{shirt_id},#{record_id},#{user_name}, #{user_pass},#{user_himg},#{nick_name},#{m_shape},#{m_abdomen},#{m_shoulder})")
      @Options(useGeneratedKeys = true,keyColumn = "id")
      void insert(UserEntity user);
  }
  ```

- service层操作

  ```
  //创建service包,需要service注解类
  @Service
  public class UserService {
  	//Autowired注解让mapper关联到此，使其生效
      @Autowired
      private UserMapper userMapper;
      //调用mapper实现插入数据，需要控制层调用起作用
      public void insertUser(UserEntity user) {
          userMapper.insert(user);
      }
      //调用mapper查询数据
      public UserEntity getUser(String username,String userpass){
          return userMapper.getUserByName(username);
      }
    }
  ```

  

- 服务器响应结果实体类

  ```
  import java.io.Serializable;
  //响应实体类，包含响应状态、信息、数据
  public class ResponseEntity  implements Serializable {
      private int status;
      private String msg;
      private T data;
  
      public int getStatus() {
          return status;
      }
  
      public void setStatus(int status) {
          this.status = status;
      }
  
      public String getMsg() {
          return msg;
      }
  
      public void setMsg(String msg) {
          this.msg = msg;
      }
  
      public T getData() {
          return data;
      }
  
      public void setData(T data) {
          this.data = data;
      }
      public ResponseEntity(){}
      /*响应数据*/
      public ResponseEntity(int status, String msg, T data) {
          this.status = status;
          this.msg = msg;
          this.data = data;
      }
  }
  
  ```

  

- 在controller控制器中添加数据库操作的接口

  ```
  //此版本springboot中返回的实体类会自动转化为json
  import com.supermanshirts.entity.ResponseEntity;
  import com.supermanshirts.entity.UserEntity;
  import com.supermanshirts.service.UserService;
  import org.springframework.beans.factory.annotation.Autowired;
  import org.springframework.web.bind.annotation.RequestMapping;
  import org.springframework.web.bind.annotation.RequestMethod;
  import org.springframework.web.bind.annotation.RestController;
  @RestController
  public class UserController {
      @Autowired
      private UserService userService;
  	/*通过用户名查询数据库对应记录，模拟登录操作*/
      @RequestMapping(value = "/login",method = RequestMethod.POST)
      public ResponseEntity get(String username,String userpass){
          ResponseEntity responseEntity=new ResponseEntity();
          UserEntity userEntity=userService.getUser(username,userpass);
          if(userEntity.getUser_pass().equals(userpass)){
              responseEntity.setStatus(200);
              responseEntity.setMsg("登录成功");
              responseEntity.setData(userEntity);
          }else {
              responseEntity.setStatus(300);
              responseEntity.setMsg("登录失败");
          }
          return responseEntity;
      }
      /*往数据库插入数据,注册用户*/
      @RequestMapping(value = "/register",method = RequestMethod.POST)
      public ResponseEntity register(String username,String userpass){
          ResponseEntity responseEntity=new ResponseEntity(200,"注册失败","");
         try{
             String nickName="superman"+System.currentTimeMillis();
             UserEntity userEntity=new UserEntity(0,0,username,userpass,"https://ss0.bdstatic.com/-0U0b8Sm1A5BphGlnYG/kmarketingadslogo/49b8e752ae9dbb3a5ed375f1185d7683_250_250.jpg",nickName,"标准体","扁腹","耸肩");
             userService.insertUser(userEntity);
             responseEntity.setStatus(200);
             responseEntity.setMsg("注册成功");
             return responseEntity;
         }catch (Exception e){
             return responseEntity;
         }
  
      }
      /*测试接口*/
      @RequestMapping(value = "/test",method = RequestMethod.GET)
      public String test(){
          System.out.println("");
          return "测试";
      }
  }
  ```

  

=======
# springboot快速开发后台与接口

## 数据库表设计与创建

#### 工具下载

- [mysql下载]( )5.7以下，新旧版本有差异
  - 安装时记得设置初始密码
- [navicat下载](https://pan.baidu.com/s/1gDJwNF4YrxszOz7TeYx3hQ),密码xzrr

#### 创建数据库

```
/*
Navicat MySQL Data Transfer

Source Server         : wxdemo
Source Server Version : 50725
Source Host           : localhost:3306
Source Database       : supermansirts

Target Server Type    : MYSQL
Target Server Version : 50725
File Encoding         : 65001

Date: 2019-03-30 21:10:37
*/

SET FOREIGN_KEY_CHECKS=0;

-- ---------男士衬衫三张表实际使用需要改-------------------
-- Table structure for tb_minfo
-- ----------------------------
DROP TABLE IF EXISTS `tb_minfo`;
CREATE TABLE `tb_minfo` (
  `m_id` int(10) NOT NULL AUTO_INCREMENT,
  `shirt_id` int(10) NOT NULL,
  `record_id` int(10) NOT NULL,
  `user_name` varchar(200) NOT NULL,
  `user_pass` int(30) NOT NULL DEFAULT '0',
  `user_himg` varchar(200) DEFAULT NULL,
  `nick_name` varchar(50) DEFAULT NULL,
  `m_shape` varchar(50) DEFAULT '标准体',
  `m_abdomen` varchar(50) DEFAULT '扁腹',
  `m_shoulder` varchar(50) DEFAULT '耸肩',
  PRIMARY KEY (`m_id`),
  UNIQUE KEY `UK_N` (`user_name`),
  KEY `record_id` (`record_id`)
) ENGINE=InnoDB AUTO_INCREMENT=5 DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of tb_minfo
-- ----------------------------
INSERT INTO `tb_minfo` VALUES ('3', '0', '0', '18822179535', '123456', 'https://ss0.bdstatic.com/-0U0b8Sm1A5BphGlnYG/kmarketingadslogo/49b8e752ae9dbb3a5ed375f1185d7683_250_250.jpg', 'superman1553929794077', '标准体', '扁腹', '耸肩');
INSERT INTO `tb_minfo` VALUES ('4', '0', '0', '15534510036', '123456', 'https://ss0.bdstatic.com/-0U0b8Sm1A5BphGlnYG/kmarketingadslogo/49b8e752ae9dbb3a5ed375f1185d7683_250_250.jpg', 'superman1553930598372', '标准体', '扁腹', '耸肩');

-- ----------------------------
-- Table structure for tb_order
-- ----------------------------
DROP TABLE IF EXISTS `tb_order`;
CREATE TABLE `tb_order` (
  `record_id` int(10) NOT NULL AUTO_INCREMENT,
  `record_time` datetime DEFAULT NULL,
  `record_num` varchar(200) DEFAULT NULL,
  `record_img` varchar(30) DEFAULT NULL,
  `record_season` varchar(50) DEFAULT '夏季',
  `record_scene` varchar(50) DEFAULT '日常',
  PRIMARY KEY (`record_id`), 
  -- 添加外键约束 --
  CONSTRAINT `frc_key` FOREIGN KEY (`record_id`) REFERENCES `tb_minfo` (`record_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of tb_order
-- ----------------------------

-- ----------------------------
-- Table structure for tb_shirt
-- ----------------------------
DROP TABLE IF EXISTS `tb_shirt`;
CREATE TABLE `tb_shirt` (
  `shirt_id` int(10) NOT NULL AUTO_INCREMENT,
  `edition_type` varchar(50) DEFAULT '潮流',
  `shirt_size` varchar(200) DEFAULT '40,175,L',
  `shirt_material` varchar(30) DEFAULT '棉',
  `shirt_color` varchar(200) DEFAULT '黑色',
  `shirt_season` varchar(50) DEFAULT '夏季',
  `shirt_scene` varchar(50) DEFAULT '日常',
  `shirt_img_id` int(10) NOT NULL,
  PRIMARY KEY (`shirt_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of tb_shirt
-- ----------------------------
SET FOREIGN_KEY_CHECKS=1;

```



## 开发工具与helloword

#### [下载idea]( )

#### HelloWrod

- 创建项目

  - 新建项目
  - 选包名
  - 选择需要的库
  - 创建项目

- 手动导入模块化(lombok)、热部署包(devtools)

  - 模块化让mapping映射文件也可以通过注解方式实现
  - 热部署修改静态网页应用不会重启

- 找到应用的入口类(初建项目只有一个类里边有main方法)

  - ```
    /*此类使springboot项目可以直接访问controller,即你设置的请求地址*/
    @SpringBootApplication
    public class SpringbootApplication {
    	public static void main(String[] args) {
    		System.out.println("sklahjks");
    		SpringApplication.run(SpringbootApplication.class, args);
    	}
    }
    ```

  - 在配置文件中设置项目访问端口

    - 在resources下的application.properties中添加：server.port=8090

  - 创建第一个controller类并通过浏览器访问

    - ```
      /*新建controller包，在包下新建UserController*/
      @RestController
      public class UserController {
      	//设置访问路径
      	@RequestMapping(value = "/test",method = RequestMethod.GET)
          public String test(){
              return "hello springboot";
          }
      }
      ```

    - 这时启动项目在浏览器输入： 我们就可以看到浏览器有"hello springboot"输出

## 快速开发接口

#### 与数据库的交互

- 配置数据库的连接

  ```
  #设置默认端口
  server.port=8070
  #mybatis扫描默认的实体类方便数据库映射
  mybatis.type-aliases-package=com.supermanshirts.entity
  #旧版本数据库驱动
  #spring.datasource.driverClassName = com.mysql.jdbc.Driver
  #新版本数据库驱动,好像新版本驱动会默认加载
  spring.datasource.driverClassName = com.mysql.cj.jdbc.Driver
  #数据库地址，supermansirts是你创建的数据库名称
  spring.datasource.url = jdbc:mysql://localhost:3306/supermansirts?useUnicode=true&characterEncoding=utf-8&useSSL=false&&serverTimezone=UTC
  #数据库用户名密码
  spring.datasource.username = root
  spring.datasource.password =123456
  ```

- 创建客户端请求的响应实体类

     

  ```
  import lombok.Data;
  import java.io.Serializable;
  /*实体类需要通过Data来注解*/
  @Data
  public class UserEntity implements Serializable {
      /*用户id*/
     private int m_id;
     /*衬衫id*/
     private int shirt_id;
     /*定制订单id*/
     private int record_id;
     /*用户名*/
     private String user_name;
     /*用户密码*/
     private String user_pass;
     /*用户头像*/
     private String user_himg;
     /*用户昵称*/
     private String nick_name;
     /*用户体型*/
     private String m_shape;
     /*用户腹部描述*/
     private String m_abdomen;
     /*用户肩部描述*/
     private String m_shoulder;
  
      public int getM_id() {
          return m_id;
      }
  
      public int getShirt_id() {
          return shirt_id;
      }
  
      public int getRecord_id() {
          return record_id;
      }
  
      public String getUser_name() {
          return user_name;
      }
  
      public String getUser_pass() {
          return user_pass;
      }
  
      public String getUser_himg() {
          return user_himg;
      }
  
      public String getNick_name() {
          return nick_name;
      }
  
      public String getM_shape() {
          return m_shape;
      }
  
      public String getM_abdomen() {
          return m_abdomen;
      }
  
      public String getM_shoulder() {
          return m_shoulder;
      }
  
      public void setM_id(int m_id) {
          this.m_id = m_id;
      }
  
      public void setShirt_id(int shirt_id) {
          this.shirt_id = shirt_id;
      }
  
      public void setRecord_id(int record_id) {
          this.record_id = record_id;
      }
  
      public void setUser_name(String user_name) {
          this.user_name = user_name;
      }
  
      public void setUser_pass(String user_pass) {
          this.user_pass = user_pass;
      }
  
      public void setUser_himg(String user_himg) {
          this.user_himg = user_himg;
      }
  
      public void setNick_name(String nick_name) {
          this.nick_name = nick_name;
      }
  
      public void setM_shape(String m_shape) {
          this.m_shape = m_shape;
      }
  
      public void setM_abdomen(String m_abdomen) {
          this.m_abdomen = m_abdomen;
      }
  
      public void setM_shoulder(String m_shoulder) {
          this.m_shoulder = m_shoulder;
      }
  
      public UserEntity() {
      }
  
      public UserEntity(int shirt_id, int record_id, String user_name, String user_pass, String user_himg, String nick_name, String m_shape, String m_abdomen, String m_shoulder) {
          this.shirt_id = shirt_id;
          this.record_id = record_id;
          this.user_name = user_name;
          this.user_pass = user_pass;
          this.user_himg = user_himg;
          this.nick_name = nick_name;
          this.m_shape = m_shape;
          this.m_abdomen = m_abdomen;
          this.m_shoulder = m_shoulder;
      }
  }
  
  ```

  

- 通过mapper往数据库插入数据和查询数据(这里需要服务层和控制层调用)

  ```
  /*在这里通过mapper映射插入，直接这么做就好，想理解原理请学习spring和springmvc与mybatis整合相关知识*/
  /*新建mapper包，创建UserMapper类,需要Mapper来注解*/
  @Mapper
  public interface UserMapper { 
  	//查询数据库数据
     @Select("SELECT * FROM tb_minfo WHERE user_name = #{username}")
      UserEntity getUserByName(String username);
      //插入数据库数据,前面括号对应数据库字段，后面括号对应实体类这里两边字段相同
      @Insert("INSERT INTO tb_minfo(shirt_id,record_id,user_name,user_pass,user_himg,nick_name,m_shape,m_abdomen,m_shoulder" +
              ") VALUES(#{shirt_id},#{record_id},#{user_name}, #{user_pass},#{user_himg},#{nick_name},#{m_shape},#{m_abdomen},#{m_shoulder})")
      @Options(useGeneratedKeys = true,keyColumn = "id")
      void insert(UserEntity user);
  }
  ```

- service层操作

  ```
  //创建service包,需要service注解类
  @Service
  public class UserService {
  	//Autowired注解让mapper关联到此，使其生效
      @Autowired
      private UserMapper userMapper;
      //调用mapper实现插入数据，需要控制层调用起作用
      public void insertUser(UserEntity user) {
          userMapper.insert(user);
      }
      //调用mapper查询数据
      public UserEntity getUser(String username,String userpass){
          return userMapper.getUserByName(username);
      }
    }
  ```

  

- 服务器响应结果实体类

  ```
  import java.io.Serializable;
  //响应实体类，包含响应状态、信息、数据
  public class ResponseEntity  implements Serializable {
      private int status;
      private String msg;
      private T data;
  
      public int getStatus() {
          return status;
      }
  
      public void setStatus(int status) {
          this.status = status;
      }
  
      public String getMsg() {
          return msg;
      }
  
      public void setMsg(String msg) {
          this.msg = msg;
      }
  
      public T getData() {
          return data;
      }
  
      public void setData(T data) {
          this.data = data;
      }
      public ResponseEntity(){}
      /*响应数据*/
      public ResponseEntity(int status, String msg, T data) {
          this.status = status;
          this.msg = msg;
          this.data = data;
      }
  }
  
  ```

  

- 在controller控制器中添加数据库操作的接口

  ```
  //此版本springboot中返回的实体类会自动转化为json
  import com.supermanshirts.entity.ResponseEntity;
  import com.supermanshirts.entity.UserEntity;
  import com.supermanshirts.service.UserService;
  import org.springframework.beans.factory.annotation.Autowired;
  import org.springframework.web.bind.annotation.RequestMapping;
  import org.springframework.web.bind.annotation.RequestMethod;
  import org.springframework.web.bind.annotation.RestController;
  @RestController
  public class UserController {
      @Autowired
      private UserService userService;
  	/*通过用户名查询数据库对应记录，模拟登录操作*/
      @RequestMapping(value = "/login",method = RequestMethod.POST)
      public ResponseEntity get(String username,String userpass){
          ResponseEntity responseEntity=new ResponseEntity();
          UserEntity userEntity=userService.getUser(username,userpass);
          if(userEntity.getUser_pass().equals(userpass)){
              responseEntity.setStatus(200);
              responseEntity.setMsg("登录成功");
              responseEntity.setData(userEntity);
          }else {
              responseEntity.setStatus(300);
              responseEntity.setMsg("登录失败");
          }
          return responseEntity;
      }
      /*往数据库插入数据,注册用户*/
      @RequestMapping(value = "/register",method = RequestMethod.POST)
      public ResponseEntity register(String username,String userpass){
          ResponseEntity responseEntity=new ResponseEntity(200,"注册失败","");
         try{
             String nickName="superman"+System.currentTimeMillis();
             UserEntity userEntity=new UserEntity(0,0,username,userpass,"https://ss0.bdstatic.com/-0U0b8Sm1A5BphGlnYG/kmarketingadslogo/49b8e752ae9dbb3a5ed375f1185d7683_250_250.jpg",nickName,"标准体","扁腹","耸肩");
             userService.insertUser(userEntity);
             responseEntity.setStatus(200);
             responseEntity.setMsg("注册成功");
             return responseEntity;
         }catch (Exception e){
             return responseEntity;
         }
  
      }
      /*测试接口*/
      @RequestMapping(value = "/test",method = RequestMethod.GET)
      public String test(){
          System.out.println("");
          return "测试";
      }
  }
  ```

=======
# 集成swagger2

#### 介绍
有了swagger2我再也不用写接口文档了

#### 软件架构
软件架构说明


#### 安装教程

1. xxxx
2. xxxx
3. xxxx

#### 使用说明

1. xxxx
2. xxxx
3. xxxx

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
>>>>>>> 96644ed794122516c375f5e29f82c0c5268cf166


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)