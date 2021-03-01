# Cycle-Dehaze: Enhanced CycleGAN for Single Image Dehazing

This reposotory is our project for  NTIRE 2018 Challenge on Image Dehazing . 

 Our paper  published in CVPR 2018 Workshop  (3rd NTIRE) . Please cite our paper, if it is helpful for your research.

```sh
@inproceedings{engin2018cycle,
  title={Cycle-Dehaze: Enhanced CycleGAN for Single Image Dehazing},
  author={Engin, Deniz and Gen{\c{c}}, An{\i}l and Ekenel, Haz{\i}m Kemal},
  booktitle={The IEEE Conference on Computer Vision and Pattern Recognition (CVPR) Workshops},
  year={2018}
}
```

## Model Architecture

 

## Prerequisites

* TensorFlow 1.4.1 or later
* Python 3
* MATLAB 

Our code is tested under Ubuntu 16.04 environment with Titan X GPUs.

## Demo

* Test the model for Track 1: Indoor

```sh
 sh demo.sh data/indoor results/indoor models/Hazy2GT_indoor.pb
```

* Test the model for Track 2: Outdoor

```sh
sh demo.sh data/outdoor results/outdoor models/Hazy2GT_outdoor.pb
```

*  You can use this model for your own images. 

```sh
sh demo.sh input_folder output_folder model_name
```

## License
This project is licensed under the MIT License - see the  LICENSE  file for details.

## Acknowledgments

The code is based on  CycleGAN-TensorFlow  implementation. 



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)