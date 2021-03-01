 ESP32 BLE - MI Temperature Humidity 2 Reader 

   

### 项目介绍

[MicroPython for ESP32 开发板低功耗蓝牙（BLE）研究学习项目](https://gitee.com/walkline/esp32-ble)的分支项目，用`ESP32开发板`读取`米家温湿度计2`温湿度数据

### 如何使用呢？

简单说分为如下步骤：

* 下载并烧录自定义的固件到开发板
* 如果你用的是官方最新固件的话可以参考`不想烧录自定义固件？`部分
* 把项目目录下的`ble`文件夹上传到开发板
* 在开发板上运行`ble\ble_miot.py`
* 等待开发板扫描周围的`米家温湿度计2`
* 如果找到设备就会在`REPL`中显示温湿度数据

> 注：
> * 米家`BLE 设备`都使用统一的`UUID`进行广播，但是如何区分具体是什么设备还没找到相关文档，所以。。。。使用时请确保附近只有`米家温湿度计2`设备，否则可能会出现读取数据错误的情况（毕竟可能连接到了不知道是什么的设备，呵）
> * 如果排除上述原因还是不能获取到温湿度数据，有可能是连接失败导致的，重新运行`ble\ble_miot.py`多试几次即可

### 下载烧录自定义固件

访问 [自定义固件下载项目](https://gitee.com/walkline/esp32_firmware) 下载最新的自定义固件，并参考 [附录1：如何刷写固件](https://gitee.com/walkline/esp32_firmware#%E9%99%84%E5%BD%951%E5%A6%82%E4%BD%95%E5%88%B7%E5%86%99%E5%9B%BA%E4%BB%B6) 烧录固件到开发板

### 不想烧录自定义固件？

当然没问题，不过要确认你现在的固件是**支持`ble`的**，然后

* 下载 [const.py](https://gitee.com/walkline/micropython-beacon-library/raw/master/ble/const.py)

* 下载 [tools.py](https://gitee.com/walkline/micropython-beacon-library/raw/master/ble/tools.py)

保存到项目目录`ble`文件夹下，一起上传到开发板即可

### 合作交流

* 联系邮箱： 
* QQ 交流群：
    * 走线物联：163271910
    * 扇贝物联：31324057

    


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)