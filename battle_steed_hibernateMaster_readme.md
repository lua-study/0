# hibernateMaster--让数据操作更简单

- 0sql 0hql操作数据库,跟冗长,繁琐的sql语句分手!
- 几行代码搞定增删改查,告别低效开发!剩下更多的时间陪老婆!(~~如果你有的话~~)
- 首创面向实体类编程,程序结构更合理,彻底告别数据库触发器!(~~虽然也没多少人用触发器~~)
- 自动生成的sql,hql均用替换符代替where条件,妈妈再也不用担心我被脱~~裤~~了!
- 0配置文件,告别繁琐的配置!(~~问:ehcache.xml,hibernate.cfg.xml是什么?答:我不知道~~)
- 提供查询切面,从底层掌控返回的数据,轻松实现用户只能看自己公司的数据等功能,无需每个查询都要加上 where company_id = 当前登陆用户公司id 筛选条件
- 仅仅依赖hibernate orm一个项目,jar包不足80kb,小巧轻便!

## 使用本框架需要掌握的技能
- java基础(~~不会?还不赶紧把这个网页关了学java去!~~)
- jpa注解(~~不会?且慢!先别关网页,这么简单还要学?照着例子的注解就是干~~)

## 使用本框架不需要掌握的技能
- sql,hql(~~你当我前面说的0sql,0hql是吹逼的吗?~~)
- hibernate 二级缓存,hibernate session管理,hibernate链接池配置等等...
- 煮饭,做菜,缝衣服,带孩子等...
- 开挖掘机,潜艇,直升机,高达等...


## 快速入门
[在线javadoc](http://battle_steed.gitee.io/hibernatemaster/hibernateMaster/javadoc/)

maven如下添加依赖
```
	 
		 com.github.battlesteed 
		 hibernateMaster 
		 1.0.9 
	 
```
gradle:
```
compile group: 'com.github.battlesteed', name: 'hibernateMaster', version: '1.0.9'
```
- 0sql完成增删查改

```
package steed.hibernatemaster.sample;


import org.junit.Test;

import steed.hibernatemaster.sample.domain.user.User;
import steed.hibernatemaster.test.SteedTest;

/**
 * 快速入门.
 * @author 战马
 *
 */
public class QuickStart extends SteedTest{
	
	/**
	 * 运行之后会保存一个niceName为'战马'的user实体类.
	 * 不需要提前建表,hibernate会自动生成.
	 */
	@Test
	public void save(){
		User user = new User();
		user.setNickName("战马");
		user.save();
	}
	
	/**
	 * 运行之后会把主键为"战马"的user实体类的数据库记录中name列设置为'战小马',
	 * 其他列设置为null.因为会把其他列设置为null,所以一般不直接update
	 * @see #updateNotNullFild()
	 */
	@Test
	public void update(){
		User user = new User();
		user.setNickName("战马");
		user.setName("战小马");
		user.update();
	}
	
	/**
	 * 运行之后会把主键为"战马"的user实体类的数据库记录中e_mail设置为'"battle_steed@163.com"',
	 * 并且不影响其他记录.这方法适合利用struts的modelDriven把值封装到实体类后更新到数据库.
	 * 因为前台一般不把user的字段值全部传过来,比如密码或用户状态等就不会传,
	 * 这时候直接update数据库记录的密码列更新为null了,所以需要updateNotNullFild(只更新不为null的字段).
	 */
	@Test
	public void updateNotNullFild(){
		User user = new User();
		user.setNickName("战马");
		user.setE_mail("battle_steed@163.com");
		user.updateNotNullField(null);
	}
	
	
	/**
	 * 运行之后会删除一个nickName为'战马'的user实体类.
	 * 不需要提前建表,hibernate会自动生成.
	 */
	@Test
	public void delete(){
		User user = new User();
		user.setNickName("战马");
		user.delete();
	}
}

```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)