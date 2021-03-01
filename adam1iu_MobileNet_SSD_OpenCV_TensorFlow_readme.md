# MobileNetV1/V2_SSD for the DNN modul of OpenCV
A example of OpenCV dnn framework working on a bare Raspberry Pi with TensorFlow models.
Papers  
https://arxiv.org/abs/1611.10012  
Training set: COCO  
Size: 300x300  
Frame rate V1     : 3.19 FPS (RPi 4)  
Frame rate V1_0.75: 4.98 FPS (RPi 4)  
Frame rate V2     : 2.02 FPS (RPi 4)  
Frame rate V2 Lite: 3.86 FPS (RPi 4)  
 
Special made for a bare Raspberry Pi see: https://qengineering.eu/deep-learning-with-opencv-on-raspberry-pi-4.html  
 
To extract and run the network in Code::Blocks  
$ mkdir *MyDir*  
$ cd *MyDir*  
$ wget https://github.com/Qengineering/MobileNet_SSD_OpenCV_TensorFlow/archive/master.zip  
$ unzip -j master.zip  
Remove master.zip and README.md as they are no longer needed.   
$ rm master.zip  
$ rm README.md    
Your *MyDir* folder must now look like this:   
Traffic.jpg  
COCO_labels.txt  
frozen_inference_graph_V1.pb (download this file from: https://drive.google.com/open?id=1sDn1guYV6oj-AeYuC-riGRh4kv9XBTMz ) 
frozen_inference_graph_V2.pb (download this file from: https://drive.google.com/open?id=1EU6tVcDNLNwv-pbJUXL7wYUchFHxr5fw ) 
ssd_mobilenet_v1_coco_2017_11_17.pbtxt  
ssd_mobilenet_v2_coco_2018_03_29.pbtxt  
TestOpenCV_TensorFlow.cpb  
MobileNetV1.cpp (can be use for V2 version also) 
  
Run TestOpenCV_Caffe.cpb with Code::Blocks. Remember, you also need a working OpenCV 4 on your Raspberry.  

![output image]( https://qengineering.eu/images/V1_FPS.png )
![output image]( https://qengineering.eu/images/V1_075_FPS.png )
![output image]( https://qengineering.eu/images/V2_FPS.png )
![output image]( https://qengineering.eu/images/V2_Lite_FPS.png )



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)