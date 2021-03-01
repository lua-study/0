# Efficient networks for Computer Vision

This repo contains source code of our work on designing efficient networks for different computer vision tasks:   (1) Image classification, (2) Object detection, and (3) Semantic segmentation. 

 
     
          Real-time semantic segmentation using ESPNetv2 on iPhone7. See  here  for iOS application source code using COREML.  
     
     
         
              
         
         
              
         
     
 

 
     
          Real-time object detection using ESPNetv2  
     
     
         
              
         
     
     
         
              
         
         
              
         
     
 

    
**Table of contents**
 1. [Key highlihgts](#key-highlights)
 2. [Supported networks](#supported-networks)
 3. [Relevant papers](#relevant-papers)
 4. [Blogs](#blogs)
 5. [Performance comparison](#performance-comparison)
 6. [Training receipe](#training-receipe)
 7. [Instructions for segmentation and detection demos](#instructions-for-segmentation-and-detection-demos)
 8. [Citation](#citation)
 9. [License](#license)
 10. [Acknowledgements](#acknowledgements)
 11. [Contributions](#want-to-help-out)
    
## Key highlights
 * Object classification on the ImageNet and MS-COCO (multi-label)
 * Semantic Segmentation on the PASCAL VOC and the CityScapes
 * Object Detection on the PASCAL VOC and the MS-COCO
 * Supports PyTorch 1.0
 * Integrated with Tensorboard for easy visualization of training logs. 
 * Scripts for downloading different datasets.
 * Semantic segmentation application using ESPNetv2 on iPhone can be found [here](https://github.com/sacmehta/ESPNetv2-COREML). 

## Supported networks
This repo supports following networks:
 * ESPNetv2 (Classification, Segmentation, Detection)
 * DiCENet (Classification, Segmentation, Detection)
 * ShuffleNetv2 (Classification)
 

## Relevant papers
 * [ESPNet (ECCV'18)](https://arxiv.org/abs/1803.06815)
 * [ESPNetv2 (CVPR'19)](https://arxiv.org/abs/1811.11431)
 * [DiCENet (arxiv)](https://arxiv.org/pdf/1906.03516.pdf)
 
## Blogs

 * [Faster Training for Efficient Networks](https://medium.com/p/faster-training-of-efficient-cnns-657953aa080?source=email-dc17ff22fa63--writer.postDistributed&sk=f60110289b6157de4c9e0c00c77f51e9)
 * [Semantic segmentation using ESPNetv2](https://medium.com/@sachinmehta.ngb/espnetv2-for-semantic-segmentation-9e80f155d522?source=friends_link&sk=91bca9326b088a972c170d1f7f5063e8)
 
## Performance comparison

### ImageNet
Below figure compares the performance of DiCENet with other efficient networks on the ImageNet dataset. DiCENet outperforms all existing efficient networks, including MobileNetv2 and ShuffleNetv2. More details [here](model/classification/model_zoo/README.md)

![DiCENet performance on the ImageNet](/images/dicenet_imagenet.png)

### Object detection

Below table compares the performance of our architecture with other detection networks on the MS-COCO dataset. Our network is fast and accurate. More details [here](model/detection/model_zoo/README.md)

 
     
          
           MSCOCO  
     
     
          
           Image Size   
           FLOPs   
           mIOU   
           FPS   
     
     
          SSD-VGG 
          512x512  
          100 B 
          26.8  
          19  
     
     
          YOLOv2 
          544x544  
          17.5 B 
          21.6  
          40  
     
     
          ESPNetv2-SSD (Ours)  
          512x512  
          3.2 B 
          24.54  
          35  
     
 


### Semantic Segmentation

Below figure compares the performance of ESPNet and ESPNetv2 on two different datasets. Note that ESPNets are one of the first efficient networks that delivers competitive performance to existing networks on the PASCAL VOC dataset, even with low resolution images say 256x256. See [here](model/segmentation/model_zoo/README.md) for more details.

 
     
          
           Cityscapes  
           PASCAL VOC 2012   
     
     
          
           Image Size   
           FLOPs   
           mIOU   
           Image  Size  
           FLOPs  
           mIOU   
     
     
          ESPNet 
          1024x512  
          4.5 B 
          60.3  
          512x512  
          2.2 B 
          63  
     
     
          ESPNetv2 
          1024x512  
          2.7 B 
           66.2   
          384x384  
          0.76 B 
           68   
     
 

## Training Receipe

### Image Classification
Details about training and testing are provided [here](README_Classification.md).

Details about performance of different models are provided [here](model/classification/model_zoo/README.md).

### Semantic segmentation
Details about training and testing are provided [here](README_Segmentation.md).

Details about performance of different models are provided [here](model/segmentation/model_zoo/README.md).


### Object Detection

Details about training and testing are provided [here](README_Detection.md).

Details about performance of different models are provided [here](model/detection/model_zoo/README.md).

## Instructions for segmentation and detection demos

To run the segmentation demo, just type:

```
python segmentation_demo.py
```

To run the detection demo, run the following command:
``` 
python detection_demo.py

OR 

python detection_demo.py --live
```

For other supported arguments, please see the corresponding files.


## Citation
If you find this repository helpful, please feel free to cite our work:
```
@misc{mehta2019dicenet,
Author = {Sachin Mehta and Hannaneh Hajishirzi and Mohammad Rastegari},
Title = {DiCENet: Dimension-wise Convolutions for Efficient Networks},
Year = {2019},
Eprint = {arXiv:1906.03516},
}

@inproceedings{mehta2018espnetv2,
  title={ESPNetv2: A Light-weight, Power Efficient, and General Purpose Convolutional Neural Network},
  author={Mehta, Sachin and Rastegari, Mohammad and Shapiro, Linda and Hajishirzi, Hannaneh},
  booktitle={Proceedings of the IEEE conference on computer vision and pattern recognition},
  year={2019}
}

@inproceedings{mehta2018espnet,
  title={Espnet: Efficient spatial pyramid of dilated convolutions for semantic segmentation},
  author={Mehta, Sachin and Rastegari, Mohammad and Caspi, Anat and Shapiro, Linda and Hajishirzi, Hannaneh},
  booktitle={Proceedings of the European Conference on Computer Vision (ECCV)},
  pages={552--568},
  year={2018}
}
```

## License
By downloading this software, you acknowledge that you agree to the terms and conditions given [here](License).


## Acknowledgements
Most of our object detection code is adapted from [SSD in pytorch](https://github.com/amdegroot/ssd.pytorch). We thank authors for such an amazing work.

## Want to help out?
Thanks for your interest in our work :).

Open tasks that are interesting:
 * Tensorflow implementation. I kind of wanna do this but not getting enough time. If you are interested, drop a message and we can talk about it.
 * Optimizing the EESP and the DiceNet block at CUDA-level.
 * Optimize and port pretrained models across multiple mobile platforms, including Android.
 * Other thoughts are also welcome :).


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)