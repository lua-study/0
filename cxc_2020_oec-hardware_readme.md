# oec-hardware

## 背景介绍
OS 厂商为了扩大自己产品的兼容性范围，常常寻求与硬件厂商的合作，进行兼容性测试。OS 厂商制定一个测试标准，并提供测试用例，硬件厂商进行实际的测试。测试通过后，OS 厂商和硬件厂商将共同在对应的官网发布兼容性信息。

验证目的就是保证 OS 与硬件平台的兼容性，验证仅限于基本功能验证，不包括性能测试等其它测试。

openEuler硬件兼容性测试框架有如下特点：

1. 为满足可信要求，必须使用openEuler操作系统，不能随意重编/插入内核模块。
2. 通过扫描机制自适应发现硬件列表，来确定要运行的测试用例集合。
3. 面向对象抽象各种硬件类型以及测试用例类，用于扩展开发。

## 软件架构
```
.
├── hwcompatible 框架主功能
│   ├── compatibility.py  框架核心功能
│   ├── client.py         上传测试结果到服务端
│   ├── command.py        bash命令执行封装
│   ├── commandUI.py      命令行交互工具
│   ├── device.py         扫描设备信息
│   ├── document.py       收集配置信息
│   ├── env.py            全局变量，主要是各个配置文件或目录的路径
│   ├── job.py            测试任务管理
│   ├── log.py            日志模块
│   ├── reboot.py         重启类任务专用，便于机器重启后仍能继续执行测试
│   ├── sysinfo.py        收集系统信息
│   └── test.py           测试套模板
├── scripts   工具脚本
│   ├── oech                  框架命令行工具
│   ├── oech-server.service   框架服务端 service 文件，用于启动 web 服务器
│   ├── oech.service          框架客户端 service 文件，用于接管 reboot 用例
│   └── kernelrelease.json    规范可用于认证的系统和内核版本
├── server   服务端
│   ├── oech-server-pre.sh    服务预执行脚本
│   ├── results/              测试结果存放目录
│   ├── server.py             服务端主程序
│   ├── static/               图片存放目录
│   ├── templates/            网页模板存放目录
│   ├── uwsgi.conf            nginx 服务配置
│   └── uwsgi.ini             uwsgi 服务配置
└── tests   测试套
```

## 安装测试框架

### 前提条件

安装了 openEuler 20.03 (LTS) 或更高版本。

### 获取安装包

* 安装包从 openEuler 官方网站下载。

* 校验安装包的完整性。

  1. 获取校验文件中的校验值：

     ```
     cat oec-hardware-*.rpm.sha256sum
     ```

  2. 计算文件的 sha256 校验值:

     ```
     sha256sum oec-hardware-*.rpm
     ```
	 

     命令执行完成后，输出校验值。

  3. 对比步骤1和步骤2计算的校验值是否一致。

     如果校验值一致说明安装文件完整性没有破坏，如果校验值不一致则可以确认文件完整性已被破坏，需要重新获取。

### 安装过程

#### 客户端

1. 配置 [openEuler 官方 repo](https://repo.openeuler.org/) 中对应版本的 everything 源，以20.03 LTS的版本的everyting源为例，路径为https://repo.openeuler.org/openEuler-20.03-LTS/everything/。使用 `dnf` 安装客户端 oec-hardware。

   ```
   dnf install oec-hardware-XXX.rpm
   ```


#### 服务端

1. 配置 [openEuler 官方 repo](https://repo.openeuler.org/) 中对应版本的 everything 源，以20.03 LTS的版本的everyting源为例，路径为https://repo.openeuler.org/openEuler-20.03-LTS/everything/。使用 `dnf` 安装服务端 oec-hardware-server。

   ```
   dnf install oec-hardware-server-XXX.rpm
   ```

2. 服务端 web 展示页面需要的部分组件系统本身不提供，需要使用 `pip3` 安装（请自行配置可用 pip 源）。

   ```
   pip3 install Flask Flask-bootstrap uwsgi
   ```

3. 启动服务。本服务默认使用 8080 端口，同时搭配 nginx（默认端口 80）提供 web 服务，请保证这些端口未被占用。

   ```
   systemctl start oech-server.service
   systemctl start nginx.service
   ```

4. 关闭防火墙和 SElinux。

   ```
   systemctl stop firewalld
   iptables -F
   setenforce 0
   ```

## 使用说明

1. 在客户端启动测试框架。在客户端启动 `oech`，其中 `ID` 和 `URL` 可以按需填写，`ID` 建议填写 gitee 上的 issue ID，`Server` 必须填写为客户端可以直接访问的服务器域名或 ip，用于展示测试报告和作网络测试的服务端。

   ```
   # oech
   The openEuler Hardware Compatibility Test Suite
   Please provide your Compatibility Test ID:
   Please provide your Product URL:
   Please provide the Compatibility Test Server (Hostname or Ipaddr):
   ```

2. 进入测试套选择界面。在用例选择界面，框架将自动扫描硬件并选取当前环境可供测试的测试套，输入 `edit` 可以进入测试套选择界面。

   ```
   These tests are recommended to complete the compatibility test:
   No. Run-Now?  Status  Class         Device
   1     yes     NotRun  acpi
   2     yes     NotRun  clock
   3     yes     NotRun  cpufreq
   4     yes     NotRun  disk
   5     yes     NotRun  ethernet      enp3s0
   6     yes     NotRun  ethernet      enp4s0
   7     yes     NotRun  ethernet      enp5s0
   8     yes     NotRun  kdump
   9     yes     NotRun  memory
   10    yes     NotRun  perf
   11    yes     NotRun  system
   12    yes     NotRun  usb
   13    yes     NotRun  watchdog
   Ready to begin testing? (run|edit|quit)
   ```

3. 选择测试套。`all|none` 分别用于 `全选|全取消`（必测项 `system` 不可取消）；数字编号可选择测试套，每次只能选择一个数字，按回车符之后 `no` 变为 `yes`，表示已选择该测试套。

   ```
   Select tests to run:
   No. Run-Now?  Status  Class         Device
   1     no      NotRun  acpi
   2     no      NotRun  clock
   3     no      NotRun  cpufreq
   4     no      NotRun  disk
   5     yes     NotRun  ethernet      enp3s0
   6     no      NotRun  ethernet      enp4s0
   7     no      NotRun  ethernet      enp5s0
   8     no      NotRun  kdump
   9     no      NotRun  memory
   10    no      NotRun  perf
   11    yes     NotRun  system
   12    no      NotRun  usb
   13    no      NotRun  watchdog
   Selection ( |all|none|quit|run):
   ```

4. 开始测试。选择完成后输入 `run` 开始测试。

5. 上传测试结果。测试完成后可以上传测试结果到服务器，便于结果展示和日志分析。如果上传失败，请检查网络配置，然后重新上传测试结果。

   ```
   ...
   -------------  Summary  -------------
   ethernet-enp3s0                  PASS
   system                           FAIL
   Log saved to /usr/share/oech/logs/oech-20200228210118-TnvUJxFb50.tar succ.
   Do you want to submit last result? (y|n) y
   Uploading...
   Successfully uploaded result to server X.X.X.X.
   ```
## 查看结果

### 如何查看

1. 浏览器打开服务端 IP 地址，点击导航栏 `Results` 界面，找到对应的测试 id 进入。


2. 进入单个任务页可以看到具体的测试结果展示，包括环境信息和执行结果等。

   - `Submit` 表示将结果上传到欧拉官方认证服务器（**当前尚未开放**）。

   - `Devices` 查看所有测试设备信息。

   - `Runtime` 查看测试运行日志。

   - `Attachment` 下载测试附件


### 结果说明&建议

在 **Result** 列展示测试结果，结果有两种：**PASS** 或者 **FAIL**。如果结果为**FAIL**，可以直接点击结果来查看执行日志，根据报错对照用例代码进行排查。



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)