# finalExam

#### 项目介绍
此项目用来作为期末考试!最多六个人一组，每组选出一个小组长，从给出的题目中选择一个，每两周做一次发表。期末上交程序。每个步骤都有期末考试分数，都体现在此网站上。

#### 考试步骤
1. 自由分组（一周，1分）：最多六人一组，选出小组长
2. 申请账号（一周，2分）：每人以自己名字的拼音全拼（如果重名，可加后缀）作为用户名，在码云https://gitee.com申请一个账号，每个组长建立一个仓库，这个仓库用来存放每组的程序和文档。（总结：每组一个仓库，每人一个账号）
3. 选题（一周,2分）：从下面列表中选择一个题目（十一放假前可自己选择题目，放假后必须从下表中选择）；组长关注此项目，把选题和相关信息填入GroupList_jike.md（计科班）或GroupList_wulianwang.md（物联网班）。（总结：每组一个题目）
4. 上传代码（二周，1分）：每组把各自程序源码的初始版本上传到码云网站的各组仓库中。
5. 修改代码（直到考试结束，5分）：小组成员为代码做贡献，直至完成程序（包括程序的说明文档等）
6. 课堂演讲（直到考试结束，4分）：在程序编写过程中，进行课堂讲演（可以包括以下内容：本阶段完成的工作，工作中碰到的技术，技术原理是什么，碰到的问题是什么，下一个阶段计划怎么解决等）
7. 期末演讲（期末考试前，50分）：提交课程设计报告和程序到仓库中；进行演讲，对整个项目进行讲解。

#### 分组示例

* 组长： 张三 （题目：利用openCV进行人脸识别签到）
* 组员及各自分工：
1. 张三  摄像头获取人脸模块
2. 李四，王五 人脸注册模块
3. 小明 训练模块
4. 小花 编写文档
5. 小黄 环境搭建、程序调试
* 进度计划
1. 10月份：熟悉码云操作流程，搭建编程环境
2. 11月份：成功编译代码
3. 12月份：找出代码不足的地方，修改完善
4. 1月份：熟悉代码，书写课程设计报告
* 本小组代码网址：https://gitee.com/***/***/***
* 本项目参考网址：
1. https://github.com/tensorflow
2. https://edu.csdn.net/course/detail/6412

#### 候选列表

1. Tensorflow object detection API 打造属于自己的物体检测模型（https://www.bilibili.com/video/av21539370/?p=1）
2. TensorFlow项目实战视频课程-人脸检测（https://www.bilibili.com/video/av20770105/?p=7）
3. TensorFlow项目实战-DQN让AI自己玩游戏（https://www.bilibili.com/video/av20109337/?p=1 ，  https://github.com/yenchenlin/DeepLearningFlappyBird ）
4. Tensorflow项目实战-DCGAN，程序自己生成图片（https://www.bilibili.com/video/av20033914）
5. 基于Tensorflow、树莓派的无人驾驶小车（https://www.bilibili.com/video/av20401916，https://github.com/hamuchiwa/AutoRCCar）
6. 深度学习TensorFlow框架（3）：Tensorflow项目实战-验证码识别（https://www.bilibili.com/video/av28571800，https://www.bilibili.com/video/av27533039）
7. 利用dlib进行人脸识别签到（https://github.com/ageitgey/face_recognition）
8. 利用dlib进行人脸识别签到2（http://dlib.net/ ， https://github.com/coneypo/Dlib_face_recognition_from_camera）
9. 利用MTCNN进行人脸识别签到（https://github.com/AITTSMD/MTCNN-Tensorflow）
10. 利用openCV进行人脸识别签到（自行搜集资料）
11. 利用facenet进行人脸识别签到（https://github.com/davidsandberg/facenet，https://github.com/008karan/Face-recognition，https://github.com/satinder147/Attendance-using-Face）
12. 利用openface进行人脸识别签到（https://github.com/cmusatyalab/openface）
13. 利用tensorflow.js进行人脸识别签到（慎选，https://swift.ctolib.com/justadudewhohacks-face-api-js.html）
14. 利用faceai进行人脸识别签到（https://github.com/vipstone/faceai）
15. 物体识别（https://github.com/balancap/SSD-Tensorflow）
16. 物体识别（https://github.com/qqwweee/keras-yolo3）
17. 利用yolov3进行物体识别（https://github.com/AlexeyAB/darknet）
18. 利用手机摄像头识别出手机号码（https://github.com/chen1311j/PhoneNumberOCRApp）
19. 利用CNN卷积神经网络对中文新闻进行分类（https://github.com/gaussic/text-classification-cnn-rnn）

#### 说明

1. 建议用python语言编写
2. 需要自己学习git工具的使用
3. 人脸签到大体的步骤：A、事先把每个人的人脸照片保存起来，B、从一张图片中把人脸都检测出来，每人生成一张人脸图片，C、生成的每张人脸图片再比对每个人保存的图片，选出相似度最大的那个人，如果相似度达到一个阈值，既认定图片是这个人。
![输入图片说明](https://images.gitee.com/uploads/images/2019/0204/061229_8a3112a1_1684885.jpeg "111.jpg")

#### 参与贡献

1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request

[请点击查看具体步骤](https://gitee.com/WeiKeAI/finalExam/edit/master/%E5%A6%82%E4%BD%95%E4%BF%AE%E6%94%B9%E8%BF%99%E9%87%8C%E7%9A%84%E4%BF%A1%E6%81%AF.md)

#### 参考资料
1. tensorflow：https://github.com/tensorflow/models
2. 参考网站其它项目：https://github.com/tensorflow
3. 吴恩达深度学习笔记：https://github.com/fengdu78/deeplearning_ai_books
4. 吴恩达机器学习笔记：https://github.com/fengdu78/Coursera-ML-AndrewNg-Notes
5. dlib官网：http://dlib.net/
6. 人脸识别的原理：https://zhuanlan.zhihu.com/p/24567586

#### 码云特技

1. 使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2. 码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3. 你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4. [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5. 码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6. 码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)