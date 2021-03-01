## 本项目基于[chineseocr](https://github.com/chineseocr/chineseocr) 与[psenet](https://github.com/WenmuZhou/PSENet.pytorch)  实现中文自然场景文字检测及识别

# 环境
pytorch  1.2.0
linux/macos
## PSENET 编译
``` Bash
cd psenet/pse
rm -rf pse.so 
make 
```

# 实现功能
- [x]  提供轻量的backone检测模型psenet（8.5M）,crnn_lstm_lite(9.5M) 和行文本方向分类网络（1.5M）
- [x]  任意方向文字检测，识别时判断行文本方向 
- [x]  crnn\crnn_lite lstm\dense识别（ocr-dense和ocr-lstm是搬运[chineseocr](https://github.com/chineseocr/chineseocr)的）   
- [x]  支持竖排文本识别  
- [x]  ncnn 实现 psenet （未实现核扩展）
- [x]  ncnn 实现 crnn_dense (改变了全连接为conv1x1)
- [x]  ncnn 实现 shuuflenev2 角度分类网络
- [x]  ncnn 实现 ocr 整个流程
- [ ]  mnn  实现 
- [ ]  提供竖排文本训练方案

 


## web服务启动
``` Bash
cd chineseocr_lite## 进入chineseocr目录
python app.py 8080 ##8080端口号，可以设置任意端口
```

## 访问服务
http://127.0.0.1:8080/ocr


## 识别结果展示

 
 
 
 
 


## ncnn检测识别展示(x86 cpu 单进程)
 
 

因为ncnn模型都是dense的 lstm的没转成功，效果差的不少，以后继续优化

## 参考
1. crnn  https://github.com/meijieru/crnn.pytorch.git              
2. chineseocr  https://github.com/chineseocr/chineseocr      
3. Psenet https://github.com/WenmuZhou/PSENet.pytorch  
4. 语言模型实现 https://github.com/lukhy/masr


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)