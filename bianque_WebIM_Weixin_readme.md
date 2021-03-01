####小程序webIM数据结构：
```
登录页：
		login: {
			name:'',
			psd: '',
			grant_type: 'password',
		}
		
注册页：
		register: {
			username: '',
			password: ''
		}
		
通讯录页：
	   member:[],   //好友列表
	   
聊天页：
	   chatMsg:[{
			info:{
		        to:''         
			},
			username:'',      //用户名
			yourname:'',      //好友名
			msg: {
				type:'',    
				data:''
			},
			style:'',       //样式
			time:'',
			mid:''        //message ID
	   }]
	   
globalData: 
	userInfo: '',  //用户微信授权信息
	chatMsg: []   //用于存储离线消息
	
缓存：
   myUsername: ''    //缓存登录用户名	   
   yourname + myName:''  //以用户名跟好友名为key来缓存聊天记录


```

 

 

   PLAIN     

 ZWFzZW1vYi1kZW1vI2NoYXRkZW1vdWlfYmlhbnF1ZUBlYXNlbW9iLmNvbQBlYXNlbW9iLWRlbW8jY2hhdGRlbW91aV9iaWFucXVlACR0JFlXTXQ4aE5yU1BxR0VlYUgyU2VUREt4cmZrMS1TNkRjU2hIamtOWGhfN3FzMnZYUGprbGd0ZHdSNXFBVDR5UFl5dVFtQXdNQUFBRmFiX0lKZVFCUEdnRHR5VUtKajhmelBRQ2J2clpJazBkQUw2X25HU0xNNUw3ZWtIOFlmYjdad2c= 

 

 

 

       

   webim   

   easemob-demo#chatdemoui_bianque@easemob.com/webim   

   

 

   easemob  1.1.3  webim   

 

   

        

发送消息：
  {&quot;from&quot;:&quot;bianque&quot;,&quot;to&quot;:&quot;terry_jing&quot;,&quot;bodies&quot;:[{&quot;type&quot;:&quot;txt&quot;,&quot;msg&quot;:&quot;fadfafd &quot;}],&quot;ext&quot;:{&quot;weichat&quot;:{&quot;originType&quot;:&quot;webim&quot;}}}  

  WEBIM_33eae01e6e  WEBIM_33eae01e6e  


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)