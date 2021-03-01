# STM32F103C8T6_CMSIS-DAP_SWO
-----------------------------

Based x893's code on: https://github.com/x893/CMSIS-DAP

My contribution is:

1. Upgrade CMSIS-DAP version to V2.00 .
2. Enable SWO_UART function(USART1), no SWO_STREAM/SWO_MANCHESTER mode.
3. CDC function improved(USART2).
4. Added a Soft-Reset function for Cortex-M.
5. Added BluePill board support, Remapped or unRemap (refer to Docs).
6. Added STLINK_V2A board support (refer to Docs).
7. Minor changes, e.g. LED handling, project files re-group......

Unsolved issue:
one compiling Warning on main.c (line 151), but still works fine.

Thanks.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)