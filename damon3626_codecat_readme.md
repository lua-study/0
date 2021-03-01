#CodeCat
##一句话简介
**codecat**是一款http 服务器中间件，模仿tomcat的功能，目前实现了`热部署`，`热卸载`，`路由转发`功能。
##快速使用
- **cd /home/xxx/codecat/bin** 查看项目的`bin`目录
- **sudo chmod +x startup.sh** 修改启动脚本，获得执行权限
- **redis-server** 开启redis server , 并且可以启动一个客户端实时查看键值对情况， **hgetall codecat** 可以查看所有的port path的映射关系
- **./startup 8080** 开启codecat服务，注意这个操作会试图关闭你计算机的防火墙（测试的时候用），后面的参数是用户可以指定的codecat的服务端口。
- **打开浏览器访问localhost:8080(或者你指定的端口)**  访问服务根目录
- **cp codecat-api.jar /home/xxx/your project** 将bin下的 codecat-api.jar引入你的项目，注意项目在打包的时候命好名，因为这个名字将是你这个项目的根目录名字。
新建一个类，让其继承 `BasicHttpHandler`这个类，并实现 `service`方法，该方法的返回值会输出到页面上，并在该类上加注解`@Path("/xxx")`,表示该类处理的请求路径。代码如下：
```
@Path("/timer")
public class TimerHandler extends BasicHttpHandler {

    @Override
    public Object service(Object msg) {
        String timestamp = new SimpleDateFormat("YYYY-MM-dd HH:mm:ss").format(new Date());
        return " "+timestamp+" ";
    }
}
```
这里我写了一个获得当前系统时间的类。
- **讲jar包放入 codecat/apps 下，这里有个小问题，第一次放可能会失败，删除再放一次就好**  假设你的jar包叫 `index.jar` ,此时访问[localhost:8080/index/timer](),即可看到当前系统时间。
                                                        

##对比tomcat
tomcat的热部署 是无法再被卸载的，因此 **codecat** 引入了`热卸载`的概念，codecat内部使用一个代理，启动的时候默认代理一个server，每当用户向`codecat/apps` 中放入一个新的jar包后，**codecat**会读取jar包内相应的类，启动一个新的端口并注册到代理，启动之前把新的类加载到新的server
以jar包的名字作为项目根目录，从而达到一个jar包对应一个realserver端口的效果。用户的直接感受就是访问的端口没有变过。当用户卸载（删除）jar时， **codecat** 会根据所删除jar包名字，将映射的端口关闭，从而达到用户无法访问该jar包的功能的效果，来达到卸载的目的。

##尚存的缺陷BUG
- **1.**首次上传jar的时候可能读取不到jar包内容。
- **2.**卸载（删除）jar的时候，需要用 rm -f xxx.jar，图形化删除或用delete键都无法被见听到。
- **3.**用户api模块的 BasicHttpHandler尚且不完善，还没有封装httprequest,httpresponse,httpsession等类。


##备注：
###目录文件监听功能使用了第三方库 [JNotify](http://my.oschina.net/fuckmylife0/blog/324967)
###感谢
感谢 李敖 大牛提供的技术思路
[andilylia](https://github.com/andilyliao)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)