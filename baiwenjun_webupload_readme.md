# webupload

#### 介绍
整合webuploader+springboot+layui技术做的大文件分片上传，支持断点续传，解决前端大文件上传卡死，浏览器崩溃的问题，前端基于layui+webupload封装了一个layWebupload组件，欢迎使用

案例在static/webupload/layWebuploadDemo.html，后端源码在src/main/java在面，前端插件源码封装在static/webupload/layui_exts/webupload/layWebupload.js，可以自己参考一下

#### 效果图
![输入图片说明](https://images.gitee.com/uploads/images/2020/0503/215836_47f7ab16_1981821.png "weupload1.png")

![输入图片说明](https://images.gitee.com/uploads/images/2020/0503/215923_424e65cd_1981821.png "webuplaod2.png")

![输入图片说明](https://images.gitee.com/uploads/images/2020/0503/215943_1f8881dd_1981821.png "webupload3.png")

![输入图片说明](https://images.gitee.com/uploads/images/2020/0503/220023_329b0dfb_1981821.png "webupload4.png")

![输入图片说明](https://images.gitee.com/uploads/images/2020/0503/220035_e9e7d526_1981821.png "webupload5.png")

![输入图片说明](https://images.gitee.com/uploads/images/2020/0503/220049_19b4b69f_1981821.png "webupload6.png")

![输入图片说明](https://images.gitee.com/uploads/images/2020/0503/220059_1b6a3084_1981821.png "webupload7.png")

#### 分片上传思路

1. 通过计算文件MD5值，上传前后台校验MD5值，如果存在，则跳过，否则就把文件分割多个分片
2. 计算分片文件MD5值，上传前也校验一下，主要是判断分片是否存在，存在就跳过这个分片，这样就可以达到断点续传的目的，减少上传时间，否则就上传
分片，而后台就是提供一个上传分片的接口，并记录数据库，如果断掉了，可以根据MD5查询到,没有上传完，可以下一次继续上传这个文件
3. 等待一个文件的所有分片都上传完毕后，通知后台合并文件，返回文件访问信息，如果多个文件，继续A步骤

#### 后台提供三个接口

1. 文件校验地址，包括文件分片校验
2. 文件分片上传接口 
3. 文件合并通知接口

#### 前端插件使用

1. 引入layui，webupload下的文件引入自己的项目
2. layui引用
```
     var domain=window.location.protocol+"//"+window.location.host;
    layui.config({
        base: domain+'/webupload/layui_exts'
    }).extend({
        layWebupload: '/webupload/layWebupload'
    });
    layui.use(['table','layWebupload'], function(){
        var table = layui.table;
        var layWebupload=layui.layWebupload;
        var layWebuploadIns;
        var url=domain+"/upload/fileRecord/"
        console.log("layWebupload:",layWebupload)
        //第一个实例
        table.render({
            elem: '#fileList'
            ,method:"post"
            // ,height: 312
            ,url: url+'getList' //数据接口
            ,page: true //开启分页
            ,cols: [[ //表头
                {field: 'id', title: 'ID'}
                ,{field: 'orgName', title: '原文件名' }
                ,{field: 'serverLocalName', title: '系统文件名'}
                ,{field: 'serverLocalPath', title: '服务存储路径'}
                ,{field: 'networkPath', title: '网络访问地址',templet:function (d) {
                        return domain+d.networkPath;
                    }}
                ,{field: 'uploadType', title: '上传类型',templet:function (d) {
                        return d.uploadType==1?'普通文件':'用户头像';
                    }}
                ,{field: 'md5Value', title: '文件MD5'}
                ,{field: 'fileSize', title: '文件大小',templet:function (d) {
                        return formatFileSize(d.fileSize);
                    }}
                ,{field: 'uploadDevice', title: '设备信息'}
                ,{field: 'uploadIp', title: '设备IP'}
                ,{field: 'createTime', title: '上传日期'}
            ]]
           , request: {
                pageName: 'page' //页码的参数名称，默认：page
                ,limitName: 'size' //每页数据量的参数名，默认：limit
            }
            ,response: {
                statusCode: 10000 //规定成功的状态码，默认：0
            }
            ,parseData:function(res){ //res 即为原始返回的数据
                return {
                    "code": res.code, //解析接口状态
                    "msg": res.message, //解析提示文本
                    "count": res.data.total, //解析数据长度
                    "data": res.data.rows //解析数据列表
                };
            }
            ,page: true
            ,limits: [10, 20, 30, 50, 100,200]
            ,limit: 10
        });

        $("#uploadFileBtn").click(function () {//重点
            var fileType=''
            //常见图片
            fileType+="gif,png,jpeg,jpg";
            //常见的视频
            fileType+="cd,wave,aife,mpeg,mp3,mpeg-4,midi,wma,realaudio,vqf,oggvorbis,amr,ape,flac,aac";
            //常见音频
            fileType+=",avi,mov,rmvb,rm,flv,mp4,3gpavi,mov,3gp"

            layWebuploadIns=layWebupload.render({
                url: url+'/zone/upload',//上传文件服务器地址，必填
                fileCheckUrl:url+'/zone/upload/md5Check',//文件校验地址
                checkChunkUrl:url+'/zone/upload/md5Check',//文件块校验地址
                mergeChunksUrl:url+'/zone/upload/merge/',//文件合并地址
                size:5*1024*1024*1024,//单个文件大小，有默认值，可不填
                fileType:fileType,//允许上传文件格式,有默认值，可不填
                fileBoxEle:"#file_table_box",//上传容器
                fileNumLimit:500,//上限500个文件
                // headers:{//headers参数传递,根据自己需要添加
                //     Authorization:new Date().getTime()
                // }
            });
            openEditPanel("文件上传","webupload_box")
        });
        /**
         * 获取实例中上传数据
         ***/
        $("#getUploadFileDataBtn").click(function () {
            if(layWebuploadIns!=null&&layWebuploadIns!=undefined){
                var nowData=layWebuploadIns.getData();
                layer.msg("已经在控制台打印了，请按F12查看");
                console.log("当前实例中数据:",nowData)
            }else{
                layer.msg("没有上传文件，请先上传文件");
            }
        });
        $("#printUploadFileDataBtn").click(function () {
            if(layWebuploadIns!=null&&layWebuploadIns!=undefined){
                var nowData=layWebuploadIns.getData();
                layer.msg("已经在控制台打印了，请按F12查看");
                console.log("当前实例中数据:",nowData)
            }else{
                layer.msg("没有上传文件，请先上传文件");
            }
        });
        function formatFileSize(size){
            var fileSize =0;
            if(size/1024>1024){
                var len = size/1024/1024;
                fileSize = len.toFixed(2) +"MB";
            }else if(size/1024/1024>1024){
                var len = size/1024/1024;
                fileSize = len.toFixed(2)+"GB";
            }else{
                var len = size/1024;
                fileSize = len.toFixed(2)+"KB";
            }
            return fileSize;
        };
        /**
         * 弹窗面板
         */
        function openEditPanel(title,modelId,w,h) {
            if (title == null || title == '') {
                title = false;
            }
            ;

            if (w == null || w == '') {
                w=600;
            }
            ;
            if (h == null || h == '') {
                h='auto';
            }else{
                h=h+"px";
            }
            ;
            var index =layer.open({
                type: 1,
                area: [w + 'px', h],
                fix: false,
                maxmin: true,
                shadeClose: false,
                zIndex:50,
                shade: 0.4,
                title: title,
                content: $("#"+modelId)
            });
            return index;
        }
    })
````

 

![输入图片说明](https://images.gitee.com/uploads/images/2020/0503/223604_a79518f4_1981821.png "usewebupload.png")


````
 本人是一个后台开发的，前端写得不到位的地方，请多多指教
 使用过程中，遇到问题，请发邮件1573028099@qq.com或者加QQ1573028099，上班期间勿扰，谢谢


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)