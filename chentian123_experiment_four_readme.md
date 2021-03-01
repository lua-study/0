# 《JAVA EE企业级架构》课程实验报告
院（系）名称：网络空间安全学院  
专业班级： 17软卓2班  
学号： 201741404247  
姓名： 陈钿     
实验题目：实验4 JDBC                      
实验日期：2019.5.27  
实验（上机）学时： 2  
成绩：

## 一、实验内容、要求
*改写用户注册/登录模块，使用JDBC或JPA技术实现用户数据的持久化，大致功能如下：
>1、	设计用户实体Entity与莞工登录用户Entity，并设置关联。  
 2、	Entity需要校验用户数据的合法性。  
 3、	用户照片保存在数据库中；前端显示用户照片时，改为读取数据库。  
 4、	任何数据库操作发生错误时，请导向error.jsp，并回滚数据库事务。  
 5、	增加绑定莞工中央认证账号的功能。本地账号登录的用户，可以在用户中心绑定莞工认证账号。  绑定后，本地账号与莞工中央认证账号关联（一对一），并且使用莞工中央认证登录等价于本地账号登录。
>
## 二、所采用的Java EE技术规范
1. JSP的基础语法  
2. Filter配置
3. Serlet配置
4. JPA的配置以及应用
5. web.xml的配置
6. jsonbean
7. html，css，js

## 三、实验的主要模块及其功能
### loginServlet.java
获取前端网页post请求中的信息，读取数据库中用户表的内容，然后遍历数据库，检验账号和密码是否符合。 
若正确则存入session中
```java
            HttpSession session = request.getSession(true);
            Map  hashmap = new HashMap ();
            hashmap.put("username",userDTO.getUsername());
            hashmap.put("password",userDTO.getPassword());
            hashmap.put("email",userDTO.getEmail());
            hashmap.put("sno",userDTO.getSno());
            hashmap.put("img",userDTO.getImg());
            hashmap.put("name",userDTO.getName());
            //HttpSession session = request.getSession(true);
            session.setAttribute("usermessage", hashmap);
            session.setAttribute("token", "not null"); 
```
错误则跳转到error.html页面

### loginFilter2.java
利用userName，token的session判定登陆状态，若无登陆则重定向到login.html 
### loginFilter1.java
利用getParameter验证获取的token，state，若无则再重定向到```https://cas.dgut.edu.cn?appid=javaee&state=STATE```获取token

### Servlet2.java
清除key为userName,token的session，并退出当前登录状态并重定向到登录界面login.html
```java
        protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
            request.getSession().removeAttribute("userName");
            request.getSession().removeAttribute("token");
           // response.sendRedirect("https://cas.dgut.edu.cn/logout?callback=http://localhost:8080/index.jsp");
            response.sendRedirect("https://cas.dgut.edu.cn/logout?callback=http://localhost:8080/login.html");
    }
 ```
###getInformation.java
```java
    public static String get(HttpServletRequest request, HttpServletResponse response)
```  
获取当前登陆用户的userName

### uploadServlet.java
使用注解设置绝对路径完成上传照片，并获取图片信息filename
```java
    @MultipartConfig(location = "C:\\Users\\ct\\IdeaProjects\\myExperiment3\\src\\main\\webapp\\img")
```  
再调用```ImgUpload.upload(fileName,request,response)```完成用户信息的修改
### dgutLogin.java
 *用于实现用户的莞工登录功能  
获取莞工第三方传输的```token```
*利用httpClient组件去执行post请求获取对应所需要的信息,类似如下
```java
        HttpPost httpPost = new HttpPost("https://cas.dgut.edu.cn/ssoapi/v2/checkToken"+ "?" +param);
        // 设置ContentType(注:如果只是传普通参数的话,ContentType不一定非要用application/json)
          httpPost.setHeader("Content-Type", "application/x-www-form-urlencoded;charset=utf8");

        // 响应模型
          CloseableHttpResponse res = null;
          res = httpClient.execute(httpPost);
          HttpEntity entity2 = res.getEntity();
```
```java
public static void jion_message(Message MessageDTO, HttpServletRequest request, HttpServletResponse response)
```  
检验是否存在与第三方学号的用户，若无则使用“工号”自动创建一个本地账号，密码预设为“123456”，若有则登陆该用户  
```java
public  static  void chang_img(HttpServletRequest request, HttpServletResponse response,String filename)
```  
读取数据库中的用户信心，匹配当前登陆用户的信息，并修改头像信息，将新更新的```usermessage```实体类存入数据库中完成用户换头像的请求
```java
public static void change_Bone(Message MessageDTO, HttpServletRequest request, HttpServletResponse response)
```  
读取数据库中的用户信心，匹配当前登陆用户的信息，并修改绑定信息，将新更新的```Message```，```usermessage```实体类存入数据库中，完成用户换头像的请求
若获取不到便利用执行post请求直到获取到对应的实体，并解析。


## 四、程序运行时的输入数据/输出结果
### 登陆界面 
![avatar](./img/1.png)
### 注册界面 
![avatar](./img/2.jpg)
### 个人信息界面 （未绑定）
![avatar](./img/3.jpg)
![avatar](./img/4.jpg)
### 个人信息界面  （已绑定）
![avatar](./img/8.jpg)
### 头像上传   
![avatar](./img/5.jpg)
![avatar](./img/6.jpg)
### error界面   
![avatar](./img/7.jpg)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)