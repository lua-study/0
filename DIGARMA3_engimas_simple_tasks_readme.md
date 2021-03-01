1。 “Engima”文件夹复制到你的任务文件夹。
2。 创建文件”init。 sqf”你的任务文件夹(如果你不已经有)。 添加以下行init.sqf的顶部:
 
> call compile preprocessFileLineNumbers "Engima\SimpleTasks\Init.sqf";
3. > Customize the list of mission's initial tasks in the file "Engima\SimpleTasks\UserConfig.sqf".

> [size=11]Usage:[/size]

添加以下函数调用动态地创建一个新的任务:[代码][“ExampleTask”,“这是一个例子。 "]叫ENGTASKS_CreateTask;

添加下面的函数调用来更新现有的任务:任务状态
 
> ["ExampleTask", "SUCCEEDED."] call ENGTASKS_SetTaskState;

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)