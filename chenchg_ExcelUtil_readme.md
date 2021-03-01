官方文档地址：http://www.likaixuan.top/excelUtil

﻿#ExcelUtil

ExcelUtil借助反射和POI对Excel读取,省略了以往读取Excel的繁琐步骤,调用ExcelUtil只需要2步,对,你没有看错,2步足以读取到Excel的内容.兼容03/07版Excel.

 
 
     net.oschina.likaixuan 
     excelutil 
     2.0.1 
 
调用步骤:   
1.定义需要读取的表头字段和表头对应的属性字段 
String keyValue ="手机名称:phoneName,颜色:color,售价:price";  
2.读取数据 
List  list =  ExcelUtil.readXls("C://test.xlsx",ExcelUtil.getMap(keyValue),"com.lkx.model.PhoneModel");
升级到1.5.5
2018年6月26日 20:24:31
升级到2.0.1
2018年7月10日 22:50:40
1.本次升级新增大家呼声比较高的流导入功能。 使用Demo
2019年1月1日 16:16:58
升级到2.0.2
1.针对Excel中Double类型做了优化，以前有些不规范的Excle会默认为字符串类型，做了兼容处理
2.升级内置引用的POI版本，从3.8升级到最新4.0.1版本。

@RequestMapping("/test")

@ResponseBody

public List testImport(MultipartFile file) throws IOException, Exception{
String keyValue ="手机名称:phoneName,颜色:color,售价:price,时间:sj"; 
List  list = ExcelUtil.readXls(file.getBytes(), ExcelUtil.getMap(keyValue), "com.lkx.model.PhoneModel");
return list;
}

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)