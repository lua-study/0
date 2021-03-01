#security
##配置
```
	 
		 test 
		 com.refordom.roleplay.security.web.WebAuthInitFilter 
		 
			 config 
			 
				[main]
				realmA = com.refordom.roleplay.security.realm.AccountAuthRealm
				securityManager.sessionMode = native

				[realms]
				factory=com.refordom.roleplay.security.factory.SpringManagerFactory

				[platform]
				platform=rfd
				subsystem=rfd

				[filters]
				authc = org.apache.shiro.web.filter.authc.UserFilter
				shiro.loginUrl = /login.html
				rest = org.apache.shiro.web.filter.authz.HttpMethodPermissionFilter
				
			 
		 
	 
```
###realmA
完成认证和鉴权,如果每次都重新认证,不走shiro缓存,需要重写getAuthorizationInfo方法
###factory
realmFactory,根据环境配置对应的factory
##登录
###使用AccountAuthRealm认证方式
```
@RequestMapping(value="login",method=RequestMethod.POST)
public ResponseEntity  login(String name,String pwd){
	Account account = new Account(name, pwd);
	try {
		account.login();
		return new ResponseEntity (account.getAccountId(),HttpStatus.OK);
	} catch (NullAccountException e) {
		return new ResponseEntity (account.getAccountId(),HttpStatus.NOT_FOUND);
	} catch (UnknownAccountException e) {
		return new ResponseEntity (account.getAccountId(),HttpStatus.NOT_FOUND);
	} catch (AccountNotActivatedException e) {
		return new ResponseEntity (account.getAccountId(),HttpStatus.LOCKED);
	} catch (AuthenticationException e) {
		return new ResponseEntity (account.getAccountId(),HttpStatus.FORBIDDEN);
	}
	return new ResponseEntity (HttpStatus.SERVICE_UNAVAILABLE);
}
```
###使用自定义认证方式
```
//以上为系统认证代码
Account account = new Account();
account.setAccountId(userDto.getUserCode());
account.setPassword(userDto.getPassword());
account.login();
```
##扩展
```
+-SubjectPermissionRealm.getSubjectPermission(Subject subject);
|	\-AccountPermissionRealm
|	\-GroupPermissionRealm
|	\-RolePermissionRealm
```
扩展实现帐号的权限,帐号所在组的权限,帐号角色的权限等




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)