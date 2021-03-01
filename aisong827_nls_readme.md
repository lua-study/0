## 简介
借助于阿里云语音服务，实现的自动将语音转化为文本


## 使用

#### 1. 阿里云开通智能语音交互
智能语音交互网址： https://nls-portal.console.aliyun.com
添加一个项目，拿到这个刚添加项目的 Appkey（注意，采样率是16K）
![](//cdn.weiunity.com/site/341/news/2025458c20734b85b58d857bb563d29f.png)


#### 2. pom.xml 的 dependencies 中加入
````
 
 
 	 com.xnx3.util 
	 xnx3-util 
	 1.0.0 
 

 
 
     com.alibaba.nls 
     nls-sdk-long-asr 
     2.0.3 
 
 
     com.alibaba.nls 
     nls-sdk-short-asr 
     2.0.3 
 
       
     com.alibaba.nls 
     nls-sdk-tts 
     2.0.3 
 
 
     com.aliyun 
     aliyun-java-sdk-core 
     3.7.1 
 
 
     com.alibaba 
     fastjson 
     1.2.49 
 
````

#### 3. 代码使用示例
````
package com.xnx3.nls;

import java.io.IOException;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.ResponseBody;
import org.springframework.web.multipart.MultipartFile;
import com.xnx3.BaseVO;
import com.xnx3.nls.aliyun.NlsUtil;

/**
 * 智能对话
 * @author 管雷鸣
 */
@Controller
@RequestMapping("/chat")
public class TestController{
	static{
		/* 
    	 * 先设置初始化的参数。这个在程序中只需设置一次即可。
    	 * accessKeyId 阿里云 AccessKeyID
		 * accessKeySecret 阿里云AccessKeySecret
		 * appKey 语音识别 appkey
    	 */
		NlsUtil.init("LTA.............", "dTuDCHVnZF....................", "JbhVJ2..........");
	}
	
	/**
	 * 语音问答 
	 * @param voice 用户说出的话，语音
	 * @return baseVO.info 回复的内容
	 * @throws IOException 
	 */
	@RequestMapping(value="/voiceTell.do", method = RequestMethod.POST)
	@ResponseBody
	public BaseVO voiceTell(HttpServletRequest request, HttpServletResponse response,
			@RequestParam("voice") MultipartFile voice) throws IOException{
		//允许跨域请求
		response.addHeader("Access-Control-Allow-Origin", "*");	
		//说出的声音转换为的文字
		String voiceText = NlsUtil.voiceToString(voice.getInputStream());
		
		return BaseVO.success(voiceText);
	}
	
}

````

#### 4. 前端html界面
参见 https://gitee.com/leimingyun/aichat

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)