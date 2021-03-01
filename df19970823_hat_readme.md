# hat

#### 项目介绍
`hat` 是深圳汇智(`Hello`)自动化(`Automate`)测试(`Testing`)缩写，是一个自动化测试方案。目前已经放到 gitee.com 码云，是国内版本的 github.com.

gitee.com 上的项目地址：https://gitee.com/szcdtest/hat

git 是一个源代码管理工具，类似于 SVN。

#### 软件架构
hat 方案的结构如下，基于 Python 语言

```markdown
hat
	|_base/ : 存放的是底层封装好的类
	|_biz/ ： 存放的业务代码
	|_case/ ： 存放的测试用例
	|_runner/ ： 存放的测试运行器
	|_main.py ： 整个方案的入口
	|_requirements.txt : 提供了该方案所需要的依赖包
```




#### 安装教程

1. 安装 Python

2. 安装 依赖包

   ```bash
   pip install -r requirements.txt
   ```

   ![1532487464305.png](https://upload-images.jianshu.io/upload_images/1430016-3828e2f4c6802547.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3. 安装 浏览器和对应的浏览器驱动

4. 安装完毕

#### 使用说明

1. 最简单的使用步骤

   1. 使用 PyCharm 打开 hat 项目

   2. 直接创建一个 demo.py 

      ```python
      # 第一步：从 base 文件夹里面的 box.py 导入 BoxDriver 这个类
      from base.box import BoxDriver
      
      # 第二步：实例化 BoxDriver 类，赋值给对象 browser，可以使用 BoxDriver() 直接实例化，不传参数
      # 不传参数，默认使用 Chrome 浏览器
      browser = BoxDriver()
      
      browser.navigate("https://www.baidu.com")
      browser.forced_wait(2)
      
      
      browser.type("kw", "汇智动力 hat 自动化测试")
      browser.click("su")
      
      browser.forced_wait(2)
      
      if "汇智动力" in browser.get_title():
          print("搜索关键字成功！")
      else:
          print("没有进行搜索！")
      
      browser.quit()
      
      
      
      ```

      运行上面的结果，实际上就是 打开百度，输入 “汇智动力 hat 自动化测试”，按 “百度一下”按钮。如果标题有 “汇智动力”四个字，就代表执行成功。

   3. 具体执行第一步：打开百度，找到搜索输入框的元素，查看HTTML TAG(标签) 元素。

      ![1532487953252.png](https://upload-images.jianshu.io/upload_images/1430016-dd3271180881be7a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

      ```html
       
      ```

      于是选择 `id="kw"` 定位。使用的是 `browser.type('kw', "内容")`

   4. 输入以后，再定位 ”百度一下“按钮

      ![1532488186218.png](https://upload-images.jianshu.io/upload_images/1430016-114d5722bff99852.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

      ```html
       
      ```

      这里又一个 `id="su"`，也使用了 `browser.click("su")`

2. 正常的使用

   1. 直接运行测试

      1. 如果你能访问 "http://192.168.1.251/ranzhi/www" 然之栗子程序，可以直接运行
      2. 打开 main.py
      3. 右键 | run main
      4. 如果不能访问的话，在用例修改栗子程序的网址。参考第3条

   2. 编写测试数据

      1. 首先要查看 runner\×××_runner.py 运行的是哪个测试运行器的数据

      2. 具体查看测试运行器的数据 在 runner\data\×××_data.csv

      3. 例如分析

         ```
         class,test,count
         RanzhiTest,test_01,1
         ```

         说明是 测试类是 RanzhiTest，测试方法是 test_01，运行次数是 1

      4. 再找到 RanzhiTest 类所在的文件，判断里面用的数据是哪个CSV

      5. 根据用例的逻辑，修改 CSV

      6. 运行 main 

      7. 右键 | run main

      8. 运行结果会生成两个

         1. runner\report\ 生成一个报告
         2. runner\log\ 生成一个日志

   3. 编写测试用例

      1. 在 case 中创建一个文件 tpshop_test.py， 类名是 TpshopTest

      2. 类需要继承 base.box(base\box.py文件) 这里的 TestCase 类

      3. 写 set_up() 和 tear_down()

         1. set_up() 实例化 BoxDriver

         2. set_up() 实例化被测试的 Page

            ```python
            self.base_driver = BoxDriver()
            
            # 必须把浏览器 self.base_driver 告诉业务，让业务操作在指定的浏览器中进行
            self.login_page = LoginPage(self.base_driver)
            
            # LoginPage类的构造方法 __init__(self, driver: BoxDriver)
            ```

            

      4. 写 test_ 开头的方法进行测试步骤和断言，假设 test_abc

         ```python
         self.login_page.login("admin", "123456")
         
         # 如果对当前的浏览器状态需要截图
         # 这里对当前步骤进行截图
         # 旧的方式
         self.images.append(self.base_driver.save_window_snapshot_by_io())
         # 新的方式
         self.snapshot()
         
         # 添加日志
         # 老的方式
         self.logger.info("刚刚进行了繁体语言切换截图")
         # 新的方式
         self.log("刚刚进行了繁体语言切换截图")
         
         # 读 CSV 作为字典
         csv_data = self.read_data_as_dict("./case/data/zone_test_02_zone_menu.csv")
         
         ```

         添加到 TestRunner 里面，运行 main

         添加一个 CSV 文件

         ```
         class,test,count
         TpshopTest,test_abc,5
         ```

         

      5. 右键 main | run main

   4. 编写测试业务

      1. 实际上是写 Page，主要用到的是 BoxDriver
         1. type
         2. click
         3. ...

   5. 修改底层封装

      1. 实际上是写 box.py

3. BoxDriver方法（下划线开头私有方法）

   | 方法名                       | 功能                                             | 参数                       |
   | :--------------------------- | :------------------------- | :------------------------- |
   | `__init__()`       | 构造方法,实例化对应的浏览器驱动                           | browser_type（浏览器类型） |
   | `clear_cookies`()              | 清除浏览器缓存                                   | 无                         |
   | `add_cookies`()                | 添加一组cookie                                   | cookies                    |
   | `add_cookie`()                 | 添加一个cookie                                   | cookie                     |
   | `remove_cookie`()              | 删除一个cookie                                   | cookie名                   |
   | `refresh`()                    | 刷新浏览器                                       | 无                         |
   | `maximize_window`()            | 窗口最大化                                       | 无                         |
   | `navigate()`                   | 打开网址                                         | url                        |
   | `close_browser()`              | 关闭浏览器                                       | 无                         |
   | `quit()`                         | 退出驱动                                         | 无                         |
   | `type()`                         | 清空输入框，输入文本信息                         | （selector定位，text）     |
   | `click()`                        | 点击                                             | selector定位               |
   | `click_by_enter`               | 输入回车                                         | selector定位               |
   | `submit()`                       | 提交表单                                         | selector定位               |
   | `move_to()`                      | 鼠标移动到指定元素                               | selector定位               |
   | `right_click()`                  | 鼠标右击元素                                     | selector定位               |
   | `count_elements()`               | 统计定位一组元素的个数                           | selector定位               |
   | `drag_element()`                 | 鼠标拖拽元素                                     | from_selector,to_selector  |
   | `lost_focus()`                   | 当前元素失去焦点                                 | 无                         |
   | `select_by_index()`              | Select通过下标选择元素                           | selector,index(下标)       |
   | `select_by_visible_text()`       | Select通过可见文本选择元素                       | selector,text(可见文本)    |
   | `select_by_value()`              | Select通过value选择元素                          | selector,value             |
   | `get_selected_text()`            | Select获取选中 文本信息                          | selector                   |
   | `execute_js()`                   | 执行js脚本                                       | 无                         |
   | `get_value()`                   | 获取元素的值                                     | selector                   |
   | `et_attribute()`                 | 获取元素的属性值                                 | selector,attribute         |
   | `get_text()`                     | 获取元素的文本信息                               | selector                   |
   | `get_displayed()`                | 判断元素是否存在                                 | selector                   |
   | `get_title()`                    | 获取网页标题                                     | 无                         |
   | `get_url()`                      | 获取当前网址                                     | 无                         |
   | `get_selected()`                 | 判断元素是否被勾选                               | selector                   |
   | `get_text_list()`                | 获取一组元素的文本                               | selector                   |
   | `accept_alert()`                 | 确定浏览器弹出框                                 | 无                         |
   | `dismiss_alert()`                | 取消浏览器弹出框                                 | 无                         |
   | `switch_to_frame()`              | 进入框体                                         | 框体selector               |
   | `switch_to_default()`            | 退出所有框体                                     | 无                         |
   | `switch_to_window_by_title()`    | 切换到指定标题的窗口                             | title                      |
   | `open_new_window()`              | selector打开新窗口,切换进入框体                  | selector                   |
   | `save_window_snapshot()`         | 截图                                             | 无                         |
   | `save_window_snapshot_by_io()`   | 保存截图为文件流                                 | 无                         |
   | `forced_wait()`                  | 强制等待                                         | seconds(秒数)              |
   | `implicitly_wait()`              | 智能等待                                         | seconds(秒数)              |
   | `explicitly_wait()`              | 显式等待s秒，直到元素加载出来                    | selector,seconds           |

   

#### 参与贡献

1. Fork 本项目
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request


#### 码云特技

1. 使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2. 码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3. 你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4. [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5. 码云官方提供的使用手册 [http://git.mydoc.io/](http://git.mydoc.io/)
6. 码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)