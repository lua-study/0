### 考虑固定效应的倍分法 (dif-in-difs-with-fixed-effects-in-stata)

- 做了一个模拟分析，对比分析了不同估计方法下 DID 的估计系数差异。
- 对于理解 Treatment effect 的 DGP (数据生成过程) 有一定的帮助，同时也帮我们重温了估计固定效应的几种方法。

Stata code comparing difference-in-differences estimation methods

The .do file contains code for simulating a longitudinal dataset for two-period difference-in-differences estimation.

I compare misspecified and correctly specified estimates.

I produce a table comparing estimates produced from the `reg,` `areg,` `xtreg,` and `xtreg, fe` commands.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)