# 零、任务背景
在课堂上我们了解了个体软件过程（PSP），并且基于该过程给大家介绍了在编码阶段如何使用源代码管理工具Git进行代码管理，如何在测试阶段使用单元测试保证模块质量和如何用功能测试验证软件功能，所以我们此次的任务就是结合课程中介绍的贪吃蛇游戏改进任务练习PSP、Git、功能测试。任务主要有6项：
1. 阅读并观看下文中给出的Git、码云教程与视频，了解工具和方法的使用
2. 获取贪吃蛇仓库源码并在自己的个人计算机上将其运行起来，尝试玩儿一会儿这个游戏并思考你准备如何改进这个游戏
3. 完成游戏UI改进任务并提交到远程代码仓库
4. 根据自己的思考，根据PSP开展工作（计划、开发、测试、总结、反思等）
5. 按要求撰写作业博客并发布提交

# 一、任务要求
## 1. 学习工具与方法的使用
1) Git与码云使用学习：从酷课网下载视频《Git基本使用方法》，《码云基本使用方法》，《如何在VS Code中进行源代码管理》并观看。除此之外网络上还有相关学习资源，也可以进行拓展学习：
- [廖雪峰的官方网站-Git教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
- [菜鸟教程-Git教程](http://www.runoob.com/git/git-tutorial.html)
- [腾讯课堂-零基础学习Git版本管理工具（从入门到实战）](https://ke.qq.com/course/237926)
- [码云-帮助文档](https://gitee.com/help#article-header0)
- [码云配置git SSH密钥](https://www.jianshu.com/p/a90aeaef73a5)

2) 开发环境配置
- 安装Python3.6或以上版本： [Python3.7.2](https://www.python.org/downloads/windows/)
- 安装Pygame游戏开发模块: [Pygame下载安装教程](https://jingyan.baidu.com/article/d2b1d102bc24865c7e37d4ff.html)
- 安装VS Code集成开发环境

## 2. 获取贪吃蛇代码并在本地运行
1) 从码云[北软软工/贪吃蛇](https://gitee.com/sybrjsjrg_br_jsj_rg/sesnake)仓库Fork仓库到自己个人的码云仓库
2) 从个人码云仓库中将仓库克隆到本地
3) 运行代码并试完游戏
4) 思考你想如何改进游戏，并将改进想法记录下来

## 3. 完成游戏UI改进任务并提交到远程代码仓库
除了你自己的想法外，你还必须完成游戏UI改进任务，主要任务如下：
1) 将游戏名称改为“贪吃蛇”
2) 将“score”改为中文“分数”
3) 将游戏除了上边框以外的边框全部去除并给上边框设置合适的高度
4) 重新设计一套游戏配色方案并应用到游戏中
5) 验证你对代码的更改全部生效且未对整个游戏其他功能造成破坏后将代码推送到远程仓库

**注意：**
- 如何使用Python和pygame进行游戏开发可以阅读此系列教程：[Pygame 教程：《用 Python 和 Pygame 写游戏 - 从入门到精通》](https://blog.csdn.net/mingzznet/article/details/22660991)
- 在这个任务的完成过程中你就应该尝试使用Git对源代码进行管理，建议完成一个小任务将代码提交到本地代码仓库一次，完成所有任务后将代码推送到个人的远程代码仓库。

## 4. 根据PSP开展工作（计划、开发、测试、总结、反思等）
1) 按照上课时使用的PSP计划表估算各项工作需要花费的时间并做好记录
2) 进行需求分析与设计，并将分析结果与设计方案写成文档保存，并记录工作耗时
3) 根据需求分析与设计进行具体实现的设计和编码工作，并使用Git和码云对源代码进行管理，记录工作耗时（前提是准备好了开发环境与相应工具）
4) 对新增的游戏特性或功能进行测试，形成测试报告
5) 计算工作量并进行总结反思

**注意：**
- 初次尝试不要尝试太复杂的功能与特性的实现，可以从简单的功能与特性开始，比如：
  - 给游戏增加“开始游戏”按钮，当游戏运行后出现该按钮，点击该按钮正式开始游戏
  - 给游戏增加“障碍物”，当蛇碰到障碍物，游戏结束
  - 给游戏增加背景音乐以及音效
- 编码时最好每天都将当天完成的经过测试没有问题的代码推送到远程仓库。

## 5. 按要求撰写作业博客并发布提交
将以上任务的完成情况撰写成博客随笔发布到博客园并提交到班级博客。博客随笔排版要求采用博客园的markdown排版，范飞龙 老师提供了[说明](http://www.cnblogs.com/math/p/se-tools-001.html)。

**注意**：发布博客后并不代表提交了作业，需要进入班级博客后点击进入作业界面并点击提交按钮，才能提交作业，若未提交作业，助教无法进行评分，所以务必提交作业。

1) 博客开头给出自己的基本信息，格式建议如下：
- 学号（保留前4位和后4位，中间用星号代替，避免泄露个人信息）；
- 姓名：***，*用你的真实姓名替代
- 我的码云贪吃蛇项目仓库：https://gitee.com/sybrjsjrg_br_jsj_rg/personal_project41634.git（用你的真实仓库地址替代）

**注意：**务必给出仓库地址，很多评分将基于仓库中的数据进行评分。

2) 给出你的各项任务完成时间估算与实际消耗时间表。

3) 给出你对该游戏改进的基本想法的文字描述以及你对需求的分析和设计。

4) 给出你的具体设计的文字描述以及此次任务的代码量（**行），提交（commit）次数，推送（push）次数。

5) 给出你对你所添加的功能或者特性的功能测试报告。请给出测试清单，哪些功能，预期结果是什么，测试结果是什么。

6) 录制一个演示视频，演示你新增的功能和特性，将该视频上传到优酷之类的视频平台，将视频链接给出，建议视频不要超过3分钟。

7) 给出你对此次任务的总结与反思。

# 二、评分标准
本次作业总分 **35**分。**切勿抄袭，一经发现，本次作业得-5分。**

（1）博客开头给出了个人信息，得1分

（2）博客开头给出了代码仓库的地址，得1分

（3）博客给出了各项任务的完成时间估算与实际消耗时间表，结合学生任务，若其估算与实际消耗合理，得3分，否则不得分

（4）博客给出了游戏改进想法及需求分析与设计（7分）
    - 改进想法：合理得分，不合理不得分。简要描述得1分，详细描述得3分
    - 需求分析与设计：合理得分，不合理不得分。简要描述得2分，详细描述得4分

（5）博客给出了具体实现的设计思路与方案、编码工作完成情况及数据（12分）
    - 完成了游戏UI设计改进任务，部分完成得1分，全部完成得2分
    - 具体实现设计：合理、与需求分析设计一致得分，否则不得分。简要描述得2分，详细描述得4分
    - 编码工作完成情况：至少有四次在不同日期的代码推送，每次推送至少有一个提交得3分，低于此频度酌情减分，高于此频度酌情加分至不超过5分
    - 相关工作数据：给出得1分，给出数据若与仓库中的实际情况不一致不得分

（6）博客给出了清晰简要的测试报告，得3分

（7）博客给出了有效视频链接，且视频中演示了新功能特性（需与设计、实现描述一致），得3分

（8）博客给出此次任务完成情况的总结反思，根据总结反思的详细与深入程度给分，最高得5分，最低不得分

**注：**如能积极响应助教和老师的反馈并在评论2天内做出相应修改，会在已有评分上有一定加分，但原则上获得分数不超过本次作业总分。

**此游戏的基础源码来自于[贪吃蛇](https://github.com/xflywind/Python-Application)**

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)