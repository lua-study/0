# flint 打火石
#### 介绍
Flint 是一个将网页上特定内容爬取，并按时进行推送的机器人，也可以生成csv文件。
定时爬取，定时推送。

#### 安装教程

1. 请使用python3.6及以上
2. 请输入以下命令安装依赖包：

`pip3 install -r requirements.txt`

#### 配置

目录：
` /config`

#### 使用说明

快速使用：
`python brk.py run --test`

详情：
`python brk.py --help`

```bash
usage: brk.py [-h] [-i] [-t] [-j JOB_ID [JOB_ID ...]] run

positional arguments:
  run                   运行打火石

optional arguments:
  -h, --help            show this help message and exit
  -i, --init            初始化out目录
  -t, --test            测试运行
  -j JOB_ID [JOB_ID ...], --job_id JOB_ID [JOB_ID ...]
                        指定运行的job id， 默认全部运行
```

#### 如果要自行开发新功能

1. 将新功能代码开发在plugins目录下
2. 新的apscheduler的job放在job_master.py的Jobs类里
3. job_master.JobMaster.load_jobs中规定任务的时间参数，务必添加job_id


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)