# plural
translate the word to plural form 


这是一套开源的名词单数变复数的系统 

英语名词单数变复数的规则： 
一、绝大多数的可数名词的复数形式,是在该词末尾加上后辍-s. 读音变化：结尾是清辅音读[s],结尾是浊辅音或元音读[z]. 例：friend→friends; cat→cats; style→styles; sport→sports; piece→pieces 
二、凡是以s、z、x、ch、sh结尾的词,在该词末尾加上后辍-es构成复数. 读音变化：统一加读[iz]. 例：bus→buses; quiz→quizzes; fox→foxes; match→matches; flash→flashes 
三、以辅音字母+y结尾的名词,将y改变为i,再加-es. 读音变化：加读[z]. 例：candy→candies; daisy→daisies; fairy→fairies; lady→ladies; story→stories 
四、以-o结尾的名词,如果不是外来词或缩写,就加-es,否则加-s构成复数. 读音变化：加读[z]. 例：tomato→tomatoes; potato→potatoes; torpedo→torpedoes; bingo→bingoes 反例：silo→silos; piano→pianos（外来词）; photo→photos; macro→macros（缩写词） 
五、以-f或-fe结尾的名词,多为将-f或-fe改变为-ves,但有例外. 读音变化：尾音[f]改读[vz]. 例：knife→knives; life→lives; leaf→leaves; staff→staves; scarf→scarves 反例：roof→roofs 
六、以-us结尾的名词（多为外来词）,通常将-us改变为-i构成复数. 读音变化：尾音[Es]改读[ai],其中[kEs]要改读为[sai],[gEs]要改读为[dVai]. 例：fungus→fungi; abacus→abaci; focus→foci; cactus→cacti; cestus→cesti 


使用方法: 
1.将项目按照已存在的maven项目导入； 
2.将doc下的sql导入你本地数据库； 
3.把esource下的数据库连接修改成你本地的连接配置，项目默认使用的mysql（修改的是application-mysql.yml）,同时也可以使用h2,使用h2的话需要修改application.yml中mysql变为h2,再去application-h2.yml中修改相关配置； 
3.运行PluralApplication.java中main的方法，启动项目； 
4.访问本地的http://127.0.0.1:8081/swagger-ui.html#/ 
界面如下：
![](http://otivx9rbg.bkt.clouddn.com/Screenshot%20from%202017-09-28%2013:19:42.png)
注意：本系统根据上述6中变化规则进行名词单数变复数，其他特殊的单词变复数需要先添加到数据库中，才能在正确获取名词的复数形式！


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)