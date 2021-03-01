# PingPangMVC

![类路径说明](https://images.gitee.com/uploads/images/2020/0116/174647_5a47d424_62082.png "屏幕截图.png")


![配置项](https://images.gitee.com/uploads/images/2020/0116/174205_e746f3b5_62082.png "屏幕截图.png")

例子

`
@PathAnnotation(path = "hello", type = "")
public class PingPangTest {

	@PathAnnotation(path = "test", type = "")
	public void helloWord(HttpServletRequest request,HttpServletResponse response) throws ServletException, IOException {
       	System.out.println("-----------");
       	request.getRequestDispatcher("/login.jsp").forward(request, response);
	 }
}
`



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)