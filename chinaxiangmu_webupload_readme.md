# SpringBoot 2.0 整合 WebUploader插件

## 一、项目介绍

​	本项目基于SpringBoot2.0构建，使用Thymeleaf视图解析器，前端使用bootstrap+WebUploader

## 二、技术介绍

* springboot官网：https://spring.io/projects/spring-boot/
* thymeleaf官网：https://www.thymeleaf.org/
* webuploader官网：https://fex.baidu.com/webuploader/
* bootstrap官网：https://www.bootcss.com/

## 三、页面效果

1. 下载项目，启动并访问：http://localhost:8080/upload/index 

2. 页面效果

   - 首页

     ![首页](https://github.com/zyt1272999061/webuploader_demo/blob/master/images/index.bmp)

   - 选择文件

     ![等待上传](https://github.com/zyt1272999061/webuploader_demo/blob/master/images/paused.bmp)

   - 开始上传/暂停上传

     ![暂停上传](https://github.com/zyt1272999061/webuploader_demo/blob/master/images/waiting.bmp)

## 四、技术实现

~~~flow
```flow
st=>start: 开始
op=>operation: 选择文件
op1=>operation: 将文件分片并上传每个分片到服务器
op2=>operation: 所有分片上传成功后，通知服务器合并分片
e=>end
st->op->op1->op2()->e
&```
~~~

## 五、代码实现

1. pom.xml

   ```xml
    
    
        4.0.0 
        
            org.springframework.boot 
            spring-boot-starter-parent 
            2.1.6.RELEASE 
              
        
        com.github.zyt 
        webuploader 
        0.0.1-SNAPSHOT 
        webuploader 
        Demo project for Spring Boot 
   
        
            1.8 
        
   
        
            
                org.springframework.boot 
                spring-boot-starter-web 
            
            
            
                org.springframework.boot 
                spring-boot-starter-thymeleaf 
            
            
            
                org.springframework.boot 
                spring-boot-devtools 
                runtime 
            
            
                org.springframework.boot 
                spring-boot-starter-test 
                test 
            
        
   
        
            
                
                    org.springframework.boot 
                    spring-boot-maven-plugin 
                
                
                
                    org.springframework.boot 
                    spring-boot-maven-plugin 
                    
                        
                        true 
                    
                
   
            
        
    
   ```

   

2. application.properties

   ```properties
   # thymeleaf
   spring.thymeleaf.prefix=classpath:/templates/
   spring.thymeleaf.suffix=.html
   spring.thymeleaf.mode=HTML
   spring.thymeleaf.encoding=UTF-8
   spring.thymeleaf.servlet.content-type=text/html
   spring.thymeleaf.cache=false
   #开启静态资源扫描
   spring.mvc.static-path-pattern=/**
   #开启热部署
   spring.devtools.restart.enabled=true
   #设置最大上传大小
   spring.servlet.multipart.enabled=true
   spring.servlet.multipart.max-file-size=5GB
   spring.servlet.multipart.max-request-size=5GB
   ```

   

3. 上传页面

   * 引入css、js

     ```html
      
      
      
      
       
       
      
     ```

     

   * 页面HTML

     ```html
      
          
              
                  
                      
                          上传 
                      
                      
                          
                              
                               
                              
                                  选择文件 
                                  开始上传 
                              
                          
                      
                  
     
              
          
      
     ```

     

   * javascript

     ```javascript
      
         /* ' +
                      ' \n' +
                      '  ' + file.name + '  \n' +
                      '  删除  \n' +
                      ' \n' +
                      ' \n' +
                      '  等待上传...  \n' +
                      '    \n' +
                      ' ');
     });
     // 文件上传过程中创建进度条实时显示
     uploader.on('uploadProgress', function (file, percentage) {
         //计算每个分块上传完后还需多少时间
         var index = file.id.slice(8);//文件的下标
         var currentTime = new Date();
         var timeDiff = currentTime.getTime() - timeArr[index].getTime();//获取已用多少时间
         var timeStr;
         //如果percentage==1说明已经全部上传完毕，则需更改页面显示
         if (1 == percentage) {
             timeStr = "上传用时：" + countTime(timeDiff);//计算总用时
         } else {
             timeStr = "预计剩余时间：" + countTime(timeDiff / percentage * (1 - percentage));//估算剩余用时
         }
         //创建进度条
         var $li = $('#' + file.id), $percent = $li.find('.progress .progress-bar');
         // 避免重复创建
         if (!$percent.length) {
             $percent = $(
                 ' '
                 + ' '
                 + ' ' + ' ')
                 .appendTo($li).find('.progress-bar');
         }
         $li.find('p.state').text('上传中');
         $li.find('span.time').text(timeStr);
         $percent.css('width', percentage * 100 + '%');
     });
     /*    uploader.on('uploadSuccess', function (file) {
                 var index = file.id.slice(8);
                 $('#' + file.id).find('p.state').text('已上传');
                 $.post(/!*[[@{/upload/combine}]]*!/, {
                     "guid": md5Arr[index],
                     fileName: file.name,
                 }, function () {
                     uploader.removeFile(file);
                 }, "json");
             });*/
     
     //上传失败时
     uploader.on('uploadError', function (file) {
         $('#' + file.id).find('p.state').text('上传出错');
     });
     //上传完成时
     uploader.on('uploadComplete', function (file) {
         $('#' + file.id).find('.progress').fadeOut();
     });
     //上传状态
     uploader.on('all', function (type) {
         if (type === 'startUpload') {
             state = 'uploading';
         } else if (type === 'stopUpload') {
             state = 'paused';
         } else if (type === 'uploadFinished') {
             state = 'done';
         }
         if (state === 'uploading') {
             $btn.text('暂停上传');
         } else {
             $btn.text('开始上传');
         }
     });
     //开始上传，暂停上传的函数
     $btn.on('click', function () {
         //每个文件的删除按钮不可用
         $(".delbtn").attr("disabled", true);
         if (state === 'uploading') {
             uploader.stop(true);//暂停
             //删除按钮可用
             $(".delbtn").removeAttr("disabled");
         } else {
             uploader.upload();
         }
     });
     //删除文件
     function delFile(id) {
         //将文件从uploader的文件列表中删除
         uploader.removeFile(uploader.getFile(id, true));
         //清除页面元素
         $("#" + id).remove();
     }
     //获取上传时还需多少时间
     function countTime(date) {
         var str = "";
         //计算出相差天数
         var days = Math.floor(date / (24 * 3600 * 1000))
         if (days > 0) {
             str += days + " 天 ";
         }
         //计算出小时数
         var leave1 = date % (24 * 3600 * 1000) //计算天数后剩余的毫秒数
         var hours = Math.floor(leave1 / (3600 * 1000))
         if (hours > 0) {
             str += hours + " 小时 ";
         }
         //计算相差分钟数
         var leave2 = leave1 % (3600 * 1000) //计算小时数后剩余的毫秒数
         var minutes = Math.floor(leave2 / (60 * 1000))
         if (minutes > 0) {
             str += minutes + " 分 ";
         }
         //计算相差秒数
         var leave3 = leave2 % (60 * 1000) //计算分钟数后剩余的毫秒数
         var seconds = Math.round(leave3 / 1000)
         if (seconds > 0) {
             str += seconds + " 秒 ";
         } else {
             /* str += parseInt(date) + " 毫秒"; */
             str += "  */
      
     ```

   

4. 后端代码

   * 校验

     ```java
     /**
      * 查看当前分片是否上传
      *
      * @param request
      * @param response
      */
     @PostMapping("checkblock")
     @ResponseBody
     public void checkMd5(HttpServletRequest request, HttpServletResponse response) {
         //当前分片
         String chunk = request.getParameter("chunk");
         //分片大小
         String chunkSize = request.getParameter("chunkSize");
         //当前文件的MD5值
         String guid = request.getParameter("guid");
         //分片上传路径
         String tempPath = uploadPath + File.separator + "temp";
         File checkFile = new File(tempPath + File.separator + guid + File.separator + chunk);
         response.setContentType("text/html;charset=utf-8");
         try {
             //如果当前分片存在，并且长度等于上传的大小
             if (checkFile.exists() && checkFile.length() == Integer.parseInt(chunkSize)) {
                 response.getWriter().write("{\"ifExist\":1}");
             } else {
                 response.getWriter().write("{\"ifExist\":0}");
             }
         } catch (IOException e) {
             e.printStackTrace();
         }
     }
     ```

     

   * 上传分片

     ```java
     /**
      * 上传分片
      *
      * @param file
      * @param chunk
      * @param guid
      * @throws IOException
      */
     @PostMapping("save")
     @ResponseBody
     public void upload(@RequestParam MultipartFile file, Integer chunk, String guid) throws IOException {
         String filePath = uploadPath + File.separator + "temp" + File.separator + guid;
         File tempfile = new File(filePath);
         if (!tempfile.exists()) {
             tempfile.mkdirs();
         }
         RandomAccessFile raFile = null;
         BufferedInputStream inputStream = null;
         if (chunk == null) {
             chunk = 0;
         }
         try {
             File dirFile = new File(filePath, String.valueOf(chunk));
             //以读写的方式打开目标文件
             raFile = new RandomAccessFile(dirFile, "rw");
             raFile.seek(raFile.length());
             inputStream = new BufferedInputStream(file.getInputStream());
             byte[] buf = new byte[1024];
             int length = 0;
             while ((length = inputStream.read(buf)) != -1) {
                 raFile.write(buf, 0, length);
             }
         } catch (Exception e) {
             throw new IOException(e.getMessage());
         } finally {
             if (inputStream != null) {
                 inputStream.close();
             }
             if (raFile != null) {
                 raFile.close();
             }
         }
     }
     ```

     

   * 合并分片

   ```java
   /**
    * 合并文件
    *
    * @param guid
    * @param fileName
    */
   @PostMapping("combine")
   @ResponseBody
   public void combineBlock(String guid, String fileName) {
       //分片文件临时目录
       File tempPath = new File(uploadPath + File.separator + "temp" + File.separator + guid);
       //真实上传路径
       File realPath = new File(uploadPath + File.separator + "real");
       if (!realPath.exists()) {
           realPath.mkdirs();
       }
       File realFile = new File(uploadPath + File.separator + "real" + File.separator + fileName);
       FileOutputStream os = null;// 文件追加写入
       FileChannel fcin = null;
       FileChannel fcout = null;
       try {
           logger.info("合并文件——开始 [ 文件名称：" + fileName + " ，MD5值：" + guid + " ]");
           os = new FileOutputStream(realFile, true);
           fcout = os.getChannel();
           if (tempPath.exists()) {
               //获取临时目录下的所有文件
               File[] tempFiles = tempPath.listFiles();
               //按名称排序
               Arrays.sort(tempFiles, (o1, o2) -> {
                   if (Integer.parseInt(o1.getName()) < Integer.parseInt(o2.getName())) {
                       return -1;
                   }
                   if (Integer.parseInt(o1.getName()) == Integer.parseInt(o2.getName())) {
                       return 0;
                   }
                   return 1;
               });
               //每次读取10MB大小，字节读取
               //byte[] byt = new byte[10 * 1024 * 1024];
               //int len;
               //设置缓冲区为10MB
               ByteBuffer buffer = ByteBuffer.allocate(10 * 1024 * 1024);
               for (int i = 0; i < tempFiles.length; i++) {
                   FileInputStream fis = new FileInputStream(tempFiles[i]);
                   /*while ((len = fis.read(byt)) != -1) {
                           os.write(byt, 0, len);
                       }*/
                   fcin = fis.getChannel();
                   if (fcin.read(buffer) != -1) {
                       buffer.flip();
                       while (buffer.hasRemaining()) {
                           fcout.write(buffer);
                       }
                   }
                   buffer.clear();
                   fis.close();
                   //删除分片
                   tempFiles[i].delete();
               }
               os.close();
               //删除临时目录
               if (tempPath.isDirectory() && tempPath.exists()) {
                   System.gc(); // 回收资源
                   tempPath.delete();
               }
               logger.info("文件合并——结束 [ 文件名称：" + fileName + " ，MD5值：" + guid + " ]");
           }
       } catch (Exception e) {
           logger.error("文件合并——失败 " + e.getMessage());
       }
   }
   ```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)