# Code Coke for Quick Programming - 编程快速参考实例集

这个工程包含了常见软件库的实例代码，通过使用这些代码能够快速的学会如何利用这些库来加速程序的编写。当中也包含了一些使用方法的文档（`./doc`目录下）

## 1. 安装依赖
建议在Ununtu，LinuxMint环境下编译程序
```
sudo apt-get install build-essential g++ cmake git
sudo apt-get install freeglut3-dev libxmu-dev libxi-dev
sudo apt-get install libqt4-dev libqt4-opengl-dev
sudo apt-get install libopencv-dev 
sudo apt-get install libboost-all-dev
sudo apt-get install libgoogle-perftools-dev google-perftools
```

## 2. 编译
按照下述命令进行编译，建议使用qtcreator打开`CMakeLists.txt`来对项目文件进行编辑。
```
mkdir build
cd build
cmake ..
make
```

编译之后，可执行程序在项目的`bin`目录下，例如执行
```
../bin/c++_basic_types
```

## 3. 包含的程序列表

|实例模块|基本描述|
| -------------------------------- |:-------------------------------------------------------|
| `PICMake`                        | 本实例程序所使用的编译方法，具体的cmake模块位于`./cmake`目录下 |
|||
| `C++`           | C++以及多种C++库的实例，具体的代码位于`c++`目录下 |
| `C++/c++basic`  | C++的基本用法，以及常用的`utils`库                |
| `C++/stl`       | C++ STL的基本用法                                 |
| `C++/boost`     | boost库的使用例子                                 |
| `C++/eigen3`    | Eigen3 矩阵运算库的使用例子                       |
| `C++/argparse`  | argparse命令行参数读取的使用例子                  |
| `C++/exif`      | TinyEXIF的使用例子，读取JPEG图片的标签信息        |
| `C++/key-value` | unqlite的key-value数据库的使用例子                |
| `C++/nanoflann` | nanoflann的使用例子，头文件的快速最近距离计算库   |
| `C++/regexp`    | PCRE正则表达式的例子                              |
| `C++/sqlite3pp` | SQLite的实例代码                                  |
| `C++/uart`      | 串口设备读取的例子                                |
| `C++/xml`       | tinyxml2的使用例子                                |
| `C++/cache`     | OfflineFIFO等缓冲库                               |
|||
| `cv`                             | OpenCV的使用方法 |
| `cv/cv_mat.cpp`                  | OpenCV中Mat的使用方法 |
| `cv/cv_image.cpp`                | OpenCV中图像处理的使用方法 |
| `cv/cv_higui.cpp`                | OpenCV中图像读取、显式，视频读取、显示的使用方法 |
| `cv/cv_calib3d.cpp`              | OpenCV中相机标定的使用方法 |
|||
| `gslam`                          | GSLAM中的一些例子程序 |
| `gslam/gimage.cpp`               | GSLAM中图像读取的使用方法 |
| `gslam/gtest_demo.cpp`           | GTEST的使用方法 |
|||
| `qt`                             | QT的使用例子 |
| `qt/draw_map`                    | 利用QGraphicsView显示二维网格图的例子 |
| `qt/elasticnodes`                | 利用QGraphicsView/QGraphicsItem显示二维弹簧网络的例子 |
| `qt/pathplane_2d`                | 利用QGraphicsView展示二维网格地图的路径规划 |
| `qt/qglviewer`                   | QGLViewer的例子 |
| `qt/qt_controls`                 | Qt的一些控件 |
|||
| `python`                         | PYthon使用例子 |
| `python/basic`                   | Python常用的函数、用法等 |
| `python/pconf`                   | Python如何加载配置（json/yaml)的例子 |
| `python/modules`                 | Python模块化编程的例子 |
|||
| `thirdparty`                     | 常用的第三方库 |


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)