一、	系统分两大模块：应用模块和管理模块。系统后台实现对数据进行分析处理和输出，是本系统设计的关键点。评教结果全部匿名显示。

应用模块包括：
用户登录(管理员、教师、学生)、
在线测评（互评）、
信息浏览（包括新闻公示、测评结果（直接统计结果输出）、【教师】-知彼知己（查看学生满意度及教学薄弱项等）、【学生】-困知勉行
（查看系统根据教师评价给出的建议）、【管理员】-用户反馈（显示用户反馈信息）、系统帮助（提供给用户意见反馈渠道，信息传递方向为用户
管理员）、测评指标等)、用户留言（教师   学生；）、
修改密码、
信息查询(包括用户信息及其测评记录（是否完成、完成时间），提供检索功能)等。

管理模块包括：
测评指标体系（增删查改）、
智能建议规则库的维护（计算方法为……在第二点中）、
测评监控（监控啥我也不知道，大概就是查看测评进度和问题反馈吧，前面功能好像已经实现了）、
新闻管理（管理员负责发布和删改）、
留言管理（管理员负责）、
用户管理（同上）、
系统初始化、
系统数据库备份（请自由发挥…）。

二、	测评指标体系和建议规则
为了方便提出建议，测评体系分四块，建议不考虑自评，根据评价的前三块来分析输出。
学生评价的四块分别是：【评价教师】课堂氛围、授课内容、教师风格，再加上【学生自评】。
教师评价的四块分别是：【评价学生】课堂表现、笔试情况、学生特点，再加上【教师自评】。
每一块的具体指标由管理员手动添加，前两块的指标添加时选项会根据评价高到低录入，【给老师的建议：】前两块若超过30%（或10个）
的学生选择评价最低的选项，则给出事先拟好的相应建议输出，否则不输出；第三块教师风格结果输出最多学生选的两个选项内容输出给老师。
【给学生的建议：】前两块若超过30%（或3个）的老师选择评价最低的选项，则给出事先拟好的相应建议输出，否则不输出；
第三块学生特点结果输出最多教师选的两个选项内容输出给学生。
我不知道这块实现会不会很复杂麻烦，如果还好的话请设计得更精细一些，如果会的话……请尽量吧！拜托啦！辛苦你啦~~~~


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)