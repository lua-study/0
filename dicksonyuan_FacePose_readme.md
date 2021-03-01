# FacePose
千搜科技人脸姿态检测，51个人脸特征点，3个方向的角度  
![输入图片说明](http://www.qiansou.cn/Scripts/img/facePoint.png "在这里输入图片标题")  

## 调用Demo示例
```
#include  
#include  
#define POINTS_NUM 51
typedef struct {
	float roll;
	float yaw;
	float pitch;
	POINT points[POINTS_NUM];
} FacePointsModel;

//创建人脸特征点引擎engine
int CreateFacePointsEngine();

//engine 是CreateFacePointsEngine返回值
//rgb24 照片的RGB数据区
//width,height 照片的宽，长
//widthstep 详细可参考http://www.opencv.org.cn/forum.php?mod=viewthread&tid=1931
//rtFace 脸的举行区域
//fpm 人脸特征点以及三个角度的返回值
float CalculateFacePoints(int engine, unsigned char * rgb24, int width, int height, int widthstep, RECT rtFace, FacePointsModel &fpm);

//快速人脸检测接口
int DetectFaces(unsigned char * gray_data, int width, int height, int widthstep,RECT* rtFaces);
```
## 输出
roll=1.003720,  
yaw=-1.232409,  
pitch=-10.462233  

## 技术支持
QQ： 2843028512  
QQ群：567619263


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)