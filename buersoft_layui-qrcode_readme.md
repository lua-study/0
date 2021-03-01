# layui_qrcode
  
 				 layui生成二维码的扩展进阶用法 
 			 
 			    指定 二维码的生成方式：    
 			 可以在调用函数的同时输入想要的二维码生成方式（table/canvas）。  
 			 //使用table生成
 $('#qrcode').qrcode({
 	render: "table",
 	text: "http://www.buersoft.cn"
 });
 
 //使用canvas生成
 $('#qrcode').qrcode({
 	render: "canvas",
 	text: "http://www.buersoft.cn"
 }); 
 			   指定 生成二维码的大小：  
 			 可以在调用函数的同时输入想要生成二维码的宽度和高度即可指定生成的二维码的大小。 
 			 //生成100*100(宽度100，高度100)的二维码
 $('#qrcode').qrcode({
 	render: "canvas", //也可以替换为table
 	width: 100,
 	height: 100,
 	text: "http://www.buersoft.cn"
 }); 
 			   指定 生成二维码的色彩样式：  
 			 可以在调用函数的同时输入想要生成二维码的前景色和背景色即可指定生成的二维码的色彩样式。 
 			 //生成前景色为红色背景色为白色的二维码
 $('#qrcode').qrcode({
 	render: "canvas", //也可以替换为table
 	foreground: "#C00",
 	background: "#FFF",
 	text: "http://www.buersoft.cn"
 }); 
 			  中文ULR生成方法:  
 			  $("#output").qrcode(encodeURI("http://中文中文"));//使用encodeURI进行转码 
 		 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)