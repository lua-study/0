# dts双轨制会员积分系统
>>> 简要的说：双轨制会员积分系统模拟分销，代理的逻辑相互推荐节点的产生1倍增2的原理。

系统已经有 PC 版和 Android版。需要的请在群里所要。
**************************
欢迎来Q群了解情况： ：689547896 
**************************

## 开始使用
- 具备linux系统环境：
- 安装好 nginx
- 修改 nginx.local.conf 中的静态文件指向 ( kingbloc.web ) 本地目录
- mysql 数据库
- redis 缓存工具
- 更改配置（.ini）文件数据库链接信息


### 启动:
```
chmod a+x dts.start.linux
dts.start.linux 
> 可选参数： -conf=/home/user/default.dts.ini
/usr/bin/nginx -s /home/user/nginx.loacl.conf
```



## 配置文件介绍
default.dts.ini 是 dts.start.linux 运行文件的配置
> initializedDatabase 默认为 true
> 第二次启动可以修改 false

default.sso.ini 是 sso.start.linux 运行文件的配置
> 与dts.start.linux配置相似

## 预览界面
![创客中心](https://gitee.com/611041314/dtsShuangGuiZhiHuiYuanJiFenXiTong/raw/master/Screenshot_20171225-232847.png)
![我的钱包](https://gitee.com/611041314/dtsShuangGuiZhiHuiYuanJiFenXiTong/raw/master/Screenshot_20171226-214921.png){:width=200px}



## 业务逻辑介绍

### 层碰奖计算规则：
在自己的报单节点下面，每层的左区与右区第一个单相碰，取最小金额并且不大于自己的报单金额；
第一层50%；
第二及以后层都是100%；
碰出的金额给收益顶点账户；
无限层，无限代

### 量碰奖计算规则：
左右按一定时间段报单业绩区分大小区；大小区同时减去小区的业绩，同时把业绩的15%分配给收益顶点账户；

### 幸运奖计算
前后20人，共40人收益当前量奖的1%；
前面不足20人，
以后面的人补足到40人,

### 管理奖计算
当天量碰奖受益人向上找，
同时分配受益给上面xx代，xx层，
受益金额为当天所有的量碰奖0.5%

### 魅力奖
直推一定的人数给予固定的奖励

### 其它说明：
报单分不同等级，不同收益比例可配置，立即生效




## 系统应用场景：
> 商场，超市，零售店会员积分系统，会员系统扩展，加强，升级；
> 集团公司融资系统；
> 项目众筹系统；
> 会员融资，投资系统；
> 民间借贷会员管理系统；
> 会员管理系统扩展业务；




```
**************************
欢迎来QQ群吐槽： ：689547896 
**************************
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)