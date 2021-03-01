# BabyOS_Example

# 移植BabyOS

## 利用STM32CUBE新建工程

选择调试接口、选择外部时钟，使能UART1

![](https://gitee.com/notrynohigh/BabyOS_Example/raw/master/doc/stm32cube.png)

## 生成代码并添加BabyOS源码

本次试验源码提交节点：

 

## 添加源文件和头文件路径

bos/core/ 核心文件全部添加至工程

bos/config/ 配置文件及设备列表文件，添加至工程

bos/driver/ 选择需要的驱动添加至工程

bos/hal/hal/ 硬件抽象层，将用到的接口添加至工程，根据具体平台进行修改

bos/hal/utils/ 底层实用代码，添加至工程

bos/modules/ 功能模块，全部添加至工程

bos/thirdparty/ 第三方开源代码，将用到的添加至工程

添加头文件

   ![](https://gitee.com/notrynohigh/BabyOS_Example/raw/master/doc/hfile.png)

##   配置b_config.h

本次实验测试b_log功能，因此只需要打开debug功能

![](https://gitee.com/notrynohigh/BabyOS_Example/raw/master/doc/config.png)

## 编辑b_device_list.h

由于本次实验不需要注册任何设备，则取消B_DEVICE_REG(null, bNullDriver, "null")的注释

   ![](https://gitee.com/notrynohigh/BabyOS_Example/raw/master/doc/device.png)

## 添加bHalIncSysTick()

```C
void SysTick_Handler(void)
{
  /* USER CODE BEGIN SysTick_IRQn 0 */
  bHalIncSysTick();
  /* USER CODE END SysTick_IRQn 0 */
  HAL_IncTick();
  HAL_SYSTICK_IRQHandler();
  /* USER CODE BEGIN SysTick_IRQn 1 */

  /* USER CODE END SysTick_IRQn 1 */
}
```

## 包含头文件b_os.h

## 添加bInit()和bExec()

```C
  //......
  /* USER CODE BEGIN WHILE */
  bInit();
  while (1)
  {
      bExec();
  /* USER CODE END WHILE */

  /* USER CODE BEGIN 3 */

  }
  /* USER CODE END 3 */
```

## 移植完成，开始测试b_log

### b_hal.h中定义输出log的串口号

```C
#define HAL_LOG_UART                    B_HAL_UART_1
```



测试b_log b_log_i b_log_w b_log_e

```C
  /* USER CODE BEGIN WHILE */
  bInit();
  b_log("b_log\r\n");
  b_log_i("b_log_i\r\n");
  b_log_w("b_log_w\r\n");
  b_log_e("b_log_e\r\n");
  while (1)
  {
      bExec();
  /* USER CODE END WHILE */

  /* USER CODE BEGIN 3 */

  }
  /* USER CODE END 3 */
```

实验效果：

![](https://gitee.com/notrynohigh/BabyOS_Example/raw/master/doc/log.png)

------

BabyOS master分支  

BabyOS教程更新会在公众号推送：

![](https://gitee.com/notrynohigh/BabyOS_Example/raw/master/doc/QRcode.jpg)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)