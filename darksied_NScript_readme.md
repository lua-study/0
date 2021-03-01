
##.Net 动态脚本引擎 NScript##

  用于解决.net环境windows系统下类似java中Grovvy的功能和方向。
在互联网项目可以用来做一些功能，如动态营销活动（营销业务解耦和剥离），规则引擎，流程引擎，windows运维脚本，源码式插件开发等。


##使用方式##

 包括exe Main方式,程序集方式,应用程序域三种方式。

##最终编译文件##

  BSF.BaseService.NScript.exe

 
exe 说明
1) 可以用cmd命令运行本exe
   /run 命令格式:/run {filename} {args}    

   说明:必须实现Main入口函数. {filename} 为文件路径,{args}为Main入口参数，默认空格分隔。
   /help 命令格式:/help    

   说明:用户查看当前exe支持的命令说明。
2）exe本身就是脚本编辑器。
   可以用作.net 脚本的编辑工具，在实际运行环境中直接编辑或临时修改代码,开发环境中建议还是使用vs。
3）exe本身也是脚本运行时。
   整个脚本解析和运行时。
4) exe大小
   exe 本身很小很小，因为打包合并了第三方编辑器控件,才变更大些。

5）exe可以被解决方案以dll方式引用，并使用NScriptHelper接口方法。

 
##Main方式示例##

*说明:*

以exe命令的方式运行脚本示例 
1. 点击“运行.bat” 
2. 点击 "bsf.baseservice.nscript.exe" 进行脚本编辑及调试。 

*截图:*
  
*压缩包下载*:
http://share.weiyun.com/043fe46f11aabc1c2c17eb4d7cfa1e00  
（或git源码目录下/文档/demo）

 

##程序集或应用程序域方式运行示例##

*说明* 
1) 解决方案引用"BSF.BaseService.NScript.exe" 
2) 程序集方式及应用程序域方式使用代码demo。 

 

		{
	    	this.richTextBox1.Text = @" public class B
	        {
	            //static void Main(string[] args)
	            //{
	            //    System.Console.WriteLine(""hello"");
	            //    System.Console.ReadLine();
	            //    System.Console.ReadKey();
	            //}
	            public string test(string a)
	            {
	                return a;
	            }
	        }";
        }
        //程序集方式
        private void button1_Click(object sender, EventArgs e)
        {
            try
            {
                string code = this.richTextBox1.Text;
                CompilerResult result = null;
                var r = NScriptHelper.Run(new CompilerParams()
                {
                    EnumSourceType = Core.EnumSourceType.Code,
                    EnumCompilerMode = Core.EnumCompilerMode.Assembly,
                    CodeOrFileName = code
                },
                     "B", "test", new object[] { "a" }, out result);
                MessageBox.Show(r);
            }
            catch (Exception exp)
            {
                MessageBox.Show(exp.Message);
            }
        }

        //应用程序域方式
        private void button2_Click(object sender, EventArgs e)
        {
            try
            {
                string code = this.richTextBox1.Text;
                CompilerResult result = null;
                var r = NScriptHelper.Run(new CompilerParams()
                {
                    EnumSourceType = Core.EnumSourceType.Code,
                    EnumCompilerMode = Core.EnumCompilerMode.AppDomian,
                    CodeOrFileName = code
                },
                     "B", "test", new object[] { "a" }, out result);
               
                MessageBox.Show(r);
            }
            catch (Exception exp)
            {
                MessageBox.Show(exp.Message);
            }
        }
 
 
*压缩包下载：*
http://share.weiyun.com/5b1f0adf5526b01c7f8ace09eaf9d113  
（或git源码目录下/文档/demo）


##使用exe编辑脚本示例##
 

##代码main.cs文件编写示例##

 

/*

 * codefiles=a.cs,codes\b.cs;//其他编译代码文件 ,分割多个文件 (支持相对路径) , 大小写敏感 （不要有分号和等号）

 * dllfiles=System.dll;//引用的dll,即编译需要的dll ,分割多个dll (支持相对路径) ,大小写敏感 （不要有分号和等号）

 * compilerlanguage=csharp;//编译语言类型,默认C#,可以不写

 */

 

/*

* 以上为主文件的编译头信息,必须要写置顶在代码文件头部。 包含源码文件信息,dll相关引用信息,代码编写语言;

      头信息中不要非常规的去使用;和=号，这个是用来解析的分隔符。主文件建议使用.main.cs命名结尾,这样可以自动识别,其他代码文件为cs结尾。

* 以下为代码编码内容,语法遵循.net本身的语法及书写规范

* by 车江毅

*/

using System;

using System.Collections.Generic;

using System.Linq;

using System.Text;

 

namespace mytest //可以不要命名空间也可

{

    public class B

    {

        //程序集或者应用程序域方式运行

        //关于调试: 通过“编辑器”->“调试” 暂不支持传入参数调试,但是实际环境是可以传入参数的

        public string test()

        {

            return new C().test();

        }

 

        //Main编译方式需要指定的Main入口函数

        //关于调试: 通过“编辑器”->“调试” 暂不支持传入参数调试,但是实际环境是可以传入参数的

        static void Main(string[] args)

        {

            System.Console.Read();

        }

    }

}
 

开源相关群: .net 开源基础服务 **238543768**
(大家都有本职工作，也许不能及时响应和跟踪解决问题，请谅解。)

##.net 开源第三方开发学习路线 ##

- 路线1:下载开源源码->学习开源项目->成功部署项目（根据开源文档或者QQ群项目管理员协助）->成为QQ群相关项目管理员->了解并解决日常开源项目问题->总结并整理开源项目文档并分享给大家或推广->成为git项目的开发者和参与者
- 路线2:下载开源源码->学习开源项目->成功部署项目（根据开源文档或者QQ群项目管理员协助）->在实际使用中发现bug并提交bug给项目相关管理员
- 路线3:下载开源源码->学习开源项目->成功部署项目（根据开源文档或者QQ群项目管理员协助）->自行建立开源项目分支->提交分支新功能给项目官方开发人员->官方开发人员根据项目情况合并新功能并发布新版本

## 关于.net 开源生态圈的构想 ##
 .net 生态闭环 ：官方开源项目->第三方参与学习->第三方改进并提交新功能或bug->官方合并新功能或bug->官方发布新版本 
 为什么开源?  .net 开源生态本身弱,而强大是你与我不断学习，点滴分享,相互协助，共同营造良好的.net生态环境。 
 开源理念:  开源是一种态度，分享是一种精神，学习仍需坚持，进步仍需努力，.net生态圈因你我更加美好。 

by 车江毅




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)