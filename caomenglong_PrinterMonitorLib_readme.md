# PrinterMonitorLib
这是监控打印机状态的C++ DLL项目，可以非常方便的查询到当前打印机正在打印的文件状态，可以用于监控文档是否打印成功，打印机是否缺纸，打印机是否异常等状态。
使用C++编写的WIN32项目 DLL文件，项目编译后会生成 PrinterMonitorLib.dll 文件，可供.NET 使用。


 PrinterMonitorLib 提供了2个方法： 

 int GetJobs(LPSTR printNamestr);  //传入打印机名称，返回当前打印任务数量。 
 
 void GetJobInfo(JOBINFO *refJOBINFROArray[],int length); //引用传入打印任务结构体数组、长度。打印任务详情将会赋值到传入的结构中。
 


 如何在C#项目中使用 PrinterMonitorLib 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)