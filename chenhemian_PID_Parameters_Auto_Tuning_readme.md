# PID_Parameters_Auto_Tuning
 **项目说明：**
 利用MATLAB语言实现PID参数的自动整定，并设计了GUI界面，操作简单，可用于实验室环境下的PID参数自整定，整定原则是使得系统的衰减比接近4:1
 **文件说明：** 
（1）PID_GUI.m：项目主程序
（2）PID_GUI.fig:GUI界面文件
（3）GouZaotf.m:构造传递函数程序
（4）WenDingXing.m:判断稳定性程序
（5）DongTaiZhiBiao.m:计算系统的动态指标
（6）P_tune.m:整定比例系数P程序
（7）PID_tune.m:整定PID参数程序
（8）find_fun.m:寻找系统响应曲线与输入信号单位阶跃曲线的交点，以计算衰减比
（9）disp_P.m、disp_PI.m、disp_PID.m:响应曲线显示函数
（10）文件中包含的.jpg文件为程序运行时需要的背景图片        
**程序运行界面：**
（1）程序刚打开时：
![输入图片说明](https://gitee.com/uploads/images/2017/1022/084838_9c5aaf77_1477507.png "splash.png")   
（2）等待输入控制器参数：
![输入图片说明](https://gitee.com/uploads/images/2017/1022/084938_a90e1e8d_1477507.png "界面图.png")
（3）整定过程中：
![输入图片说明](https://gitee.com/uploads/images/2017/1022/085003_5b1cd767_1477507.png "截面图1.png")
（4）整定完成界面：
![输入图片说明](https://gitee.com/uploads/images/2017/1022/085541_9f3f9987_1477507.png "整定完成界面.png")


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)