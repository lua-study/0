@[TOC]
# flutter
## 安装
	a,安装Android Studio 配置相关的sdk环境
	b,安装AS 插件 Dart、flutter
	c,安装flutterSDK https://flutter.dev/docs/development/tools/sdk/releases
	d,配置环境变量 ...\flutter\bin
## 创建flutter app(详情见官网 https://flutterchina.club/)
## 代码编写

### 需求一：
#### 创建一个在屏幕中居中的文字"hello",从左向右对齐
	import 'package:flutter/material.dart';
	void main(){
	  runApp(
		Center(
		  child: Text("hello",
		  textDirection: TextDirection.ltr,),
		)
	  );
	}

### 需求二：
#### 自定义小部件
	import 'package:flutter/material.dart';
	void main() => runApp(App());
	class App extends StatelessWidget{
	  // 需要修改数据的继承 StatefulWidget
	  // 不需要修改数据的继承 StatelessWidget
	  @override
	  Widget build(BuildContext context) {
		return Center(
		  child: Text("hello",
			textDirection: TextDirection.ltr,),
		);
	  }
	}

### 需求三：
#### 设置文字的样式:大小，粗细，颜色
	Text("hello",
        textDirection: TextDirection.ltr,
        style: TextStyle(
          fontSize: 40.0,
          fontWeight: FontWeight.bold,
          color:Colors.red
        ),)

### 需求四：
#### 编写一个Material风格的页面，主题色白色，标题“你好”居中显示，下方阴影2，内容同上
	import 'package:flutter/material.dart';
	void main() => runApp(App());
	class App extends StatelessWidget{
	  // 需要修改数据的继承 StatefulWidget
	  // 不需要修改数据的继承 StatelessWidget
	  @override
	  Widget build(BuildContext context) {
	    return MaterialApp(
	        home: Scaffold(
	          // 标题栏
	          appBar: AppBar(
	            // 设置标题
	            title: Text("你好"),
	            // 标题是否居中
	            centerTitle: true,
	            // 标题栏下的阴影
	            elevation: 2,
	          ),
	          body: Hello(),
	        ),
	      // 设置主题
	      theme: ThemeData(
	          primaryColor:Colors.white
	      ),
	    );
	  }
	}
	// Hello为一个小部件，显示方式同上

### 需求五：
#### 构建一个数据模型,创建一个文本列表视图
	1.创建一个文件post.dart
	class Post {
	  const Post({
	    this.title,
	    this.author,
	    this.imageUrl
	  });

	  final String title;
	  final String author;
	  final String imageUrl;
	}
	final List  posts = [
	  Post(
	    title: "图片1",
	    author: "作者1",
	    imageUrl: "https://preview.qiantucdn.com/58pic/35/00/89/66m58PICyRiUp9PKeViyx_PIC2018.jpg!w1024_small"
	  ),
	]
	2.构建一个文本列表
	import 'package:flutter/material.dart';
	import 'module/post.dart';
	void main() => runApp(App());
	class App extends StatelessWidget{
	  @override
	  Widget build(BuildContext context) {
	    return MaterialApp(
	        home: Scaffold(
	          // 标题栏
	          appBar: AppBar(
	            // 设置标题
	            title: Text("列表"),
	          ),
	          body:ListView.builder(
	              itemCount: posts.length,
	              itemBuilder: listItemBuilder
	          )
	        )
	    );
	  }
	  Widget listItemBuilder(BuildContext context,int index){
	    return Text(posts[index].title);
	  }
	}

### 需求六：
#### 构建一个有图片，文字的列表视图
	  Widget listItemBuilder(BuildContext context,int index){
	    return Container(
	      // 背景
	      color:Colors.white,
	      // 边距
	      margin: EdgeInsets.all(15.0),
	      // 内容竖直排列
	      child: Column(
	        // 内容数组
	        children:  [
	          // 网络图片
	          Image.network(posts[index].imageUrl),
	          // 间隔块
	          SizedBox(height: 15,),
	          // 设置文本 样式主标题样式
	          Text(
	            posts[index].title,
	            style: Theme.of(context).textTheme.title
	          ),
	          // 设置文本 样式副标题样式
	          Text(
	              posts[index].author,
	              style: Theme.of(context).textTheme.subhead
	          ),
	          SizedBox(height: 15,)
	        ],
	      ),
	    );
	  }

### 需求七：
#### 设置标题栏小部件
    // 标题栏
    appBar: AppBar(
      // 设置标题
      title: Text("列表"),
      centerTitle: true,
      // 设置左侧小部件
      leading: IconButton(icon: Icon(Icons.menu), tooltip: "Navigation",onPressed: ()=> debugPrint("Navigation is Pressed")),
      // 添加右侧小部件组
      actions:  [
        IconButton(icon: Icon(Icons.search), tooltip: "Search",onPressed: ()=> debugPrint("Search is Pressed")),
        IconButton(icon: Icon(Icons.more_vert), tooltip: "More",onPressed: ()=> debugPrint("More is Pressed")),
      ],
    ),

### 需求八：
#### TabBar 设置多标签
	1.需要三个控件 TabController,TabBar,TabBarView
	2.代码：
	import 'package:flutter/material.dart';

	void main() => runApp(App());

	class App extends StatelessWidget{
	  @override
	  Widget build(BuildContext context) {
	    return MaterialApp(
	        // 不显示debug的标签
	        debugShowCheckedModeBanner: false,
	        home: Home(),
	        theme: ThemeData(
	          primaryColor: Colors.yellow
	        ),
	    );
	  }
	}

	class Home extends StatelessWidget{
	  @override
	  Widget build(BuildContext context) {
	    // 脚手架
	    return DefaultTabController(
	        length: 3, child: TabWidget(),
	    );
	  }
	}

	class TabWidget extends StatelessWidget{
	  @override
	  Widget build(BuildContext context) {
	    return Scaffold(
	      // 背景色
	        backgroundColor: Colors.grey[100],
	        // 标题栏
	        appBar: AppBar(
	          // 设置标题
	          title: Text("列表"),
	          centerTitle: true,
	          // 设置左侧小部件
	          leading: IconButton(icon: Icon(Icons.menu), tooltip: "Navigation",onPressed: ()=> debugPrint("Navigation is Pressed")),
	          // 添加右侧小部件组
	          actions:  [
	            IconButton(icon: Icon(Icons.search), tooltip: "Search",onPressed: ()=> debugPrint("Search is Pressed")),
	            IconButton(icon: Icon(Icons.more_vert), tooltip: "More",onPressed: ()=> debugPrint("More is Pressed")),
	          ],
	          // 在标题栏下方设置3个Tab
	          bottom: TabBar(tabs:  [
	            Tab(icon: Icon(Icons.ac_unit),),
	            Tab(icon: Icon(Icons.access_alarm),),
	            Tab(icon: Icon(Icons.accessibility),)
	          ]),
	        ),
	        body:TabBarView(children:  [
	          // View的内容
	          Icon(Icons.ac_unit,size: 128,color: Colors.black12,),
	          Icon(Icons.access_alarm,size: 128,color: Colors.black12,),
	          Icon(Icons.accessibility,size: 128,color: Colors.black12,)
	        ])
	    );
	  }
	}

### 需求九：
#### 自定义指示器样式
	TabBar(tabs:  [
            Tab(icon: Icon(Icons.ac_unit),),
            Tab(icon: Icon(Icons.access_alarm),),
            Tab(icon: Icon(Icons.accessibility),)
          ],
          //未选择icon的颜色
          unselectedLabelColor: Colors.black26,
          // 指示器的颜色
          indicatorColor: Colors.black,
          // 指示器的宽度
          indicatorSize: TabBarIndicatorSize.label,
          // 指示器的高度
          indicatorWeight: 2,
          ),

### 需求十：
#### 自定义按钮点击样式，及水波纹效果
    theme: ThemeData(
      primaryColor: Colors.yellow,
        // 自定义按钮点击样式，及水波纹效果
      highlightColor: Color.fromRGBO(255, 255, 255, 0.5),
      splashColor: Colors.white70
    ),
### 需求十一：
#### 在脚手架中添加drawer组件，并设置视图
	    // 如果没有覆盖leading 会自动生成一个菜单icon,如果覆盖了，则自定义leading 点击事件
        drawer: Drawer(
          elevation: 10.0,
          // 列表组件
          child: ListView(
            padding: EdgeInsets.all(0),
            children:  [
              // 抽屉头
              DrawerHeader(
                child: Text(
                  "header".toUpperCase(),
                  style: TextStyle(
                    color: Colors.white
                  ),
                ),
                // 设置背景色
                decoration: BoxDecoration(
                    color: Colors.red
                ),
              ),
              ListTile(
                title: Text("Message", textAlign: TextAlign.right,),
                // 文字右边 icon
                trailing: Icon(Icons.message, color: Colors.blue, size: 22,),
                // 设置点击事件
                onTap: () => Navigator.pop(context),
              ),
              ListTile(
                title: Text("Favorite", textAlign: TextAlign.right,),
                trailing: Icon(Icons.favorite, color: Colors.blue, size: 22,),
                onTap: () => Navigator.pop(context),
              ),
              ListTile(
                title: Text("Settings", textAlign: TextAlign.right,),
                trailing: Icon(Icons.settings, color: Colors.blue, size: 22,),
                onTap: () => Navigator.pop(context),
              )
            ],
          ),
        )

### 需求十二：
#### 设置UserAccountDrawer属性
	// 抽屉头
	UserAccountsDrawerHeader(
	  accountName: Text("张三"),
	  accountEmail: Text("zhangsan@163.com"),
	  currentAccountPicture: CircleAvatar(
	    backgroundImage: NetworkImage("https://resources.ninghao.org/images/wanghao.jpg"),
	  )
	),
### 需求十三：
#### 设置底部导航栏
	1.在脚手架中添加底部导航栏部件
	bottomNavigationBar: BottomNavigationBarDemo(),
	2.创建底部导航栏部件
	// 因为点击后数据会发生变化 继承 StatefulWidget
	class BottomNavigationBarDemo extends StatefulWidget {
	  @override
	  State  createState() {
	    return _BottomNavigationBarDemoState();
	  }
	}
	3.创建部件视图
	class _BottomNavigationBarDemoState extends State  {
	  // 当前角标位置
	  int _currentIndex = 0;
	  // 点击icon的回调方法
	  void _onTapHandler(int index) {
	    setState(() {
	      _currentIndex = index;
	    });
	  }
	  @override
	  Widget build(BuildContext context) {
	    return BottomNavigationBar(
	      items:  [
	        BottomNavigationBarItem(
	          icon: Icon(Icons.explore),
	          title: Text('Explore'),
	        ),
	        BottomNavigationBarItem(
	          icon: Icon(Icons.history),
	          title: Text('History'),
	        ),
	        BottomNavigationBarItem(
	          icon: Icon(Icons.list),
	          title: Text('List'),
	        ),
	        BottomNavigationBarItem(
	          icon: Icon(Icons.person),
	          title: Text('My'),
	        ),
	      ],
	      // 当前角标位置
	      currentIndex: _currentIndex,
	      // 显示类型
	      type: BottomNavigationBarType.fixed,
	      // 选中icon和文字的颜色，如果不设置，就和主题色相同
	      fixedColor: Colors.green,
	      // tab点击事件
	      onTap: _onTapHandler,
	    );
	  }
	}

### 需求十四：
#### 普通文本和富文本
	/// 富文本
	class RichTextDemo extends StatelessWidget {
	  @override
	  Widget build(BuildContext context) {
	    return RichText(
	      text: TextSpan(
	          text: "张三",
	          style: TextStyle(
	              color: Colors.red,
	              fontStyle: FontStyle.italic,
	              fontWeight: FontWeight.bold,
	              fontSize: 20
	          ),
	          children:  [
	            TextSpan(
	              text: "是一个",
	              style: TextStyle(
	                  color: Colors.yellow,
	                  fontStyle: FontStyle.normal,
	                  fontWeight: FontWeight.normal,
	                  fontSize: 13

	              ),
	            ),
	            TextSpan(
	              text: "人",
	              style: TextStyle(
	                  color: Colors.blue
	              ),
	            )
	          ]
	      ),
	    );
	  }
	}


	/// 普通文本
	class OrdinaryTextDemo extends StatelessWidget {
	  // 设置文本替换的内容
	  final String title = "将进酒";
	  final String author = "李白";

	  @override
	  Widget build(BuildContext context) {
	    return Text("《$title》 --- $author 君不见，黄河之水天上来，奔流到海不复回。君不见，高堂明镜悲白发，"
	        "朝如青丝暮成雪。人生得意须尽欢，莫使金樽空对月。天生我材必有用，千金散尽还复来。"
	        "烹羊宰牛且为乐，会须一饮三百杯。岑夫子，丹丘生，将进酒，杯莫停。与君歌一曲，请君为我倾耳听。"
	        "钟鼓馔玉不足贵，但愿长醉不复醒。古来圣贤皆寂寞，惟有饮者留其名。陈王昔时宴平乐，斗酒十千恣欢谑。"
	        "主人何为言少钱，径须沽取对君酌。五花马，千金裘，呼儿将出换美酒，与尔同销万古愁。",
	      // 最大显示3行
	      maxLines: 3,
	      // 超出的文本用...显示
	      overflow: TextOverflow.ellipsis,
	      style: TextStyle(
	          fontSize: 17
	      ),
	    );
	  }
	}

### 需求十五：
#### 容器的属性：背景图片，圆角，阴影，渐变色...
	class BasicDemo extends StatelessWidget {
	  @override
	  Widget build(BuildContext context) {
	    return Container(
	      // 背景图片
	        decoration: BoxDecoration(
	          image: DecorationImage(image: NetworkImage(
	              "https://resources.ninghao.org/images/candy-shop.jpg"),
	              fit: BoxFit.contain,
	              repeat: ImageRepeat.repeat,
	              // 第二个参数是混合模式
	              colorFilter: ColorFilter.mode(Colors.yellow, BlendMode.lighten)
	          ),
	        ),
	        child: Column(
	          children:  [
	            OrdinaryTextDemo(),
	            RichTextDemo(),
	            Container(
	              // 容器
	//          color: Color.fromRGBO(10, 233, 255, 0.5),
	                padding: EdgeInsets.all(20),
	                margin: EdgeInsets.only(top: 10, bottom: 10),
	                child: Icon(
	                  Icons.poll,
	                  color: Colors.white,
	                  size: 30,
	                ),
	                width: 90,
	                height: 60,
	                // 设置容器的装饰盒子
	                decoration: BoxDecoration(
	                    color: Color.fromRGBO(10, 233, 255, 0.2),
	                    // 设置边框
	                    border: Border.all(
	                      color: Colors.red,
	                      width: 5,
	                      style: BorderStyle.solid,
	                    ),
	                    // 设置容器的圆角
	                    borderRadius: BorderRadius.circular(8),
	                    // 设置容器的阴影
	                    boxShadow:  [
	                      BoxShadow(
	                          color: Colors.red,
	                          // 偏移
	                          offset: Offset(2, 2),
	                          // 模糊程度
	                          blurRadius: 10,
	                          //传播半径
	                          spreadRadius: 5
	                      )
	                    ],
	                    // 设置盒子的形状 circle时 不能设置圆角
	                    shape: BoxShape.rectangle,
	                    // 设置渐变色
	                    gradient: LinearGradient(colors:  [
	                      Colors.red,
	                      Colors.black
	                    ],
	                        begin: Alignment.topCenter,
	                        end: Alignment.bottomCenter
	                    )
	                )
	            ),
	          ],
	        )
	    );
	  }
	}

### 需求十六：
#### 创建一个icon小部件
	class IconBadge extends StatelessWidget {
	  final IconData iconData;
	  final double size;

	  IconBadge(this.iconData, {
	    this.size = 32
	  });

	  @override
	  Widget build(BuildContext context) {
	    return Container(
	      child: Icon(iconData, color: Colors.white, size: size,),
	      width: size + 30,
	      height: size + 30,
	      color: Colors.blue,
	    );
	  }
	}

### 需求十七：
#### 排列功能Row/Column(主轴，交叉轴)
	Container(
      child: Column(
        children:  [
          IconBadge(Icons.poll,size: 64,),
          IconBadge(Icons.repeat,size: 64,),
          IconBadge(Icons.repeat,size: 64,),
          IconBadge(Icons.print,size: 64,),
          IconBadge(Icons.repeat,size: 64,),
        ],
        // 主轴 spaceEvenly 多余空间平分(包括两边) spaceAround 多余空间平分四周 spaceBetween 多余空间平分(不包括两边)
        mainAxisAlignment:MainAxisAlignment.spaceBetween ,
        // 交叉轴 stretch 拉伸对齐
        crossAxisAlignment: CrossAxisAlignment.start,
      ),
    );

### 需求十八：
#### 固定宽高的盒子（不设置背景可以作为控件间的间隔）
      Container(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children:  [
            SizedBox(
              width: 100,
              height: 100,
              child: Container(
              	// 设置内部控件底部居中
              	alignment: Alignment.bottomCenter,
                child: Icon(Icons.poll, color: Colors.white,),
                decoration: BoxDecoration(
                  borderRadius: BorderRadius.circular(8),
                  color: Colors.blue,
                ),
              ),
            ),
            SizedBox(
              width: 20,
              height: 20,
            ),
            SizedBox(
              width: 100,
              height: 100,
              child: Container(
                child: Icon(Icons.poll, color: Colors.white,),
                decoration: BoxDecoration(
                  borderRadius: BorderRadius.circular(8),
                  color: Colors.blue,
                ),
              ),
            )
          ],
        ),
      );

### 需求十九：
#### 控件的叠加相对位置 Stack + Positioned
    Stack(
      children:  [
        SizedBox(
          width: 100,
          height: 100,
          child: Container(
            alignment: Alignment.bottomCenter,
            child: Icon(Icons.poll, color: Colors.white,),
            decoration: BoxDecoration(
              borderRadius: BorderRadius.circular(8),
              color: Colors.blue,
            ),
          ),
        ),
        SizedBox(
          width: 20,
          height: 20,
        ),
        SizedBox(
          width: 50,
          height: 50,
          child: Container(
            child: Icon(Icons.poll, color: Colors.white,),
            decoration: BoxDecoration(
              borderRadius: BorderRadius.circular(8),
              color: Colors.red,
            ),
          ),
        ),
        // 设置控件的相对位置
        Positioned(
          child: Icon(Icons.settings,color: Colors.white,),
          top: 30,
          right: 20,
        )
      ],
    ),

### 需求二十：
#### 宽高比容器
    // 宽高比的容器
    AspectRatio(
      child: Container(
        color: Colors.red,
      ),
        aspectRatio:2/1
    ),

### 需求二十一：
#### PageView的属性分析
	Container(
      child: PageView(
        // 滑动的方向，默认横向
        scrollDirection: Axis.horizontal,
        // 反转
        reverse: true,
        // 滑动的效果 默认开启
        pageSnapping: false,
        // 滑动监听 页面 切换时返回显示超过百分之五十页面的角标
        onPageChanged: (currentPage) => debugPrint("currentPage:$currentPage"),
        controller: PageController(
          // 初始角标
          initialPage: 1,
          // 是否记录用户操作的位置
          keepPage: false,

        ),
        children:  [
          Container(
            color: Colors.red,
            alignment: Alignment(0, 0),
            child: Text(
              "ONE",
              style: TextStyle(
                color:Colors.white,
                fontSize: 20
              ),
            ),
          ),
          Container(
            color: Colors.green,
            alignment: Alignment(0, 0),
            child: Text(
              "TWO",
              style: TextStyle(
                  color:Colors.white,
                  fontSize: 20
              ),
            ),
          ),
          Container(
            color: Colors.blue,
            alignment: Alignment(0, 0),
            child: Text(
              "Three",
              style: TextStyle(
                  color:Colors.white,
                  fontSize: 20
              ),
            ),
          ),
        ],
      ),
    )

### 需求二十二
#### 创建一个可以滑动的图片画廊，图片居中铺满，左下角显示标题和作者，标题加粗，
	class ViewDemo extends StatelessWidget {
	  Widget _pageItemBuilder(BuildContext context, int position) {
	    return Stack(
	      children:  [
	        // 铺满整个页面
	        SizedBox.expand(
	          child: Image.network(
	            posts[position].imageUrl,
	            fit: BoxFit.cover,
	          ),
	        ),
	        Positioned(
	          left: 8,
	          bottom: 8,
	          child: Column(
	            crossAxisAlignment: CrossAxisAlignment.start,
	            children:  [
	              Text(
	                posts[position].title,
	                style: TextStyle(
	                    fontWeight:FontWeight.bold
	                ),
	              ),
	              Text(
	                posts[position].author
	              )
	            ],
	          ),
	        )
	      ],
	    );
	  }
	  @override
	  Widget build(BuildContext context) {
	    return PageView.builder(
	      itemCount: posts.length,
	      itemBuilder: _pageItemBuilder,
	    );
	  }
	}

### 需求二十三：
#### GridView的三种构造方法 count,extent,build
##### count
	class GridViewCountDemo extends StatelessWidget {
	  List  _buildListWidget(int length) {
	    return List.generate(length, (position) {
	      return Container(
	        color: Colors.grey,
	        alignment: Alignment(0, 0),
	        child: Text("Item $position", style: TextStyle(
	            color: Colors.red
	        ),),
	      );
	    });
	  }
	  @override
	  Widget build(BuildContext context) {
	    return GridView.count(
	      // 主轴间距
	      mainAxisSpacing: 9,
	      // 交叉轴间距
	      crossAxisSpacing: 9,
	      // 滑动方向
	      scrollDirection: Axis.horizontal,
	      // 网格滑动交叉方向item个数
	      crossAxisCount: 3,
	      children: _buildListWidget(100),
	    );
	  }
	}
##### extent
	class GridViewExtentDemo extends StatelessWidget {
	  List  _buildListWidget(int length) {
	    return List.generate(length, (position) {
	      return Container(
	        color: Colors.grey,
	        alignment: Alignment(0, 0),
	        child: Text("Item $position", style: TextStyle(
	            color: Colors.red
	        ),),
	      );
	    });
	  }
	  @override
	  Widget build(BuildContext context) {
	    return GridView.extent(
	      mainAxisSpacing: 9,
	      crossAxisSpacing: 9,
	      scrollDirection: Axis.vertical,
	      maxCrossAxisExtent: 60,
	      children: _buildListWidget(100),
	    );
	  }
	}
##### build
	class GridViewBuildDemo extends StatelessWidget {
	  Widget _itemBuildView(BuildContext context, int position) {
	    return Container(
	      child: Image.network(
	        posts[position].imageUrl,
	        fit: BoxFit.cover,
	      ),
	    );
	  }
	  @override
	  Widget build(BuildContext context) {
	    return GridView.builder(
	      // 网格相关的属性
	      gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
	        crossAxisCount: 2,
	        mainAxisSpacing: 8,
	        crossAxisSpacing: 8,
	      ),
	      // item视图
	      itemBuilder: _itemBuildView,
	      // 内间距
	      padding: EdgeInsets.symmetric(vertical: 10,horizontal: 15),
	      // 总个数
	      itemCount: posts.length,
	    );
	  }
	}

### 需求二十四
#### Sliver/SliverList/SliverGrid
##### Sliver
	Scaffold(
        body: CustomScrollView(
          slivers:  [
          	// 标题栏
            SliverAppBar(
              title: Text(
                "Hello",
                textDirection: TextDirection.ltr,
                style: TextStyle(color: Colors.red),
              ),
              centerTitle: true,
              // 是否固定在顶部
              pinned: true,
              // 标题栏跟随列表上滑和下滑
              floating: true,
              // 扩展空间
              expandedHeight: 180,
              flexibleSpace: Image.network(
                posts[0].imageUrl,
                fit: BoxFit.cover,
              ),
            ),
            // 显示在安全区域，刘海屏
            SliverSafeArea(
              // 内间距
              sliver: SliverPadding(
                padding: EdgeInsets.symmetric(horizontal: 15, vertical: 10),
                sliver: SliverListDemo(),),
            )
          ],
        )
    );
##### SliverList
	class SliverListDemo extends StatelessWidget {
	  @override
	  Widget build(BuildContext context) {
	    return SliverList(
	      delegate: SliverChildBuilderDelegate(
	              (BuildContext context, int index) {
	            return Padding(
	                padding: EdgeInsets.only(bottom: 32),
	                child: Material(
	                  // Material 自带的圆角属性 与 Image 在华为手机上不显示，所以写了两层圆角
	                  child: ClipRRect(
	                    child: Stack(
	                      children:  [
	                        AspectRatio(
	                          child: Image.network(
	                            posts[index].imageUrl,
	                            fit: BoxFit.cover,
	                          ),
	                          aspectRatio: 16 / 9,
	                        ),
	                        Positioned(
	                          top: 15,
	                          left: 15,
	                          child: Column(
	                            crossAxisAlignment: CrossAxisAlignment.start,
	                            children:  [
	                              Text(
	                                posts[index].title,
	                                style: TextStyle(
	                                    fontSize: 20,
	                                    color: Colors.white
	                                ),
	                              ),
	                              Text(
	                                posts[index].author,
	                                style: TextStyle(
	                                    fontSize: 13,
	                                    color: Colors.white
	                                ),
	                              )
	                            ],
	                          ),
	                        )
	                      ],
	                    ),
	                    borderRadius: BorderRadius.circular(12),
	                  ),
	                  borderRadius: BorderRadius.circular(12),
	                  elevation: 14,
	                  shadowColor: Colors.grey.withOpacity(0.5),
	                )
	            );
	          },
	          childCount: posts.length
	      ),
	    );
	  }
	}
##### SliverGrid
	class SliverGridDemo extends StatelessWidget {
	  @override
	  Widget build(BuildContext context) {
	    return SliverGrid(
	      gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
	          crossAxisCount: 2,
	          mainAxisSpacing: 8.0,
	          crossAxisSpacing: 8.0,
	          childAspectRatio: 0.8
	      ),
	      delegate: SliverChildBuilderDelegate(
	              (BuildContext context, int index) {
	            return Container(
	              child: Image.network(
	                posts[index].imageUrl,
	                fit: BoxFit.cover,
	              ),
	            );
	          },
	          childCount: posts.length
	      ),
	    );
	  }
	}

### 需求二十五
#### 路由（页面切换）
##### push
	class NavigationDemo extends StatelessWidget {
	  @override
	  Widget build(BuildContext context) {
	    return Scaffold(
	      body: Center(
	        child: Row(
	          mainAxisAlignment: MainAxisAlignment.center,
	          children:  [
	            FlatButton(
	              child: Text("Home"),
	              onPressed: null,
	            ),
	            FlatButton(
	              child: Text("About"),
	              onPressed: () {
	               Navigator.of(context).push(MaterialPageRoute(
	                   builder: (BuildContext context) => Page(title: "About")
	                ));
	              },
	            )
	          ],
	        ),
	      ),
	    );
	  }
	}
	class Page extends StatelessWidget {
	  final String title;
	  Page({
	    this.title
	  });
	  @override
	  Widget build(BuildContext context) {
	    return Scaffold(
	      appBar: AppBar(
	        title: Text(title),
	        centerTitle: true,
	      ),
	      floatingActionButton: FloatingActionButton(
	        onPressed: () {
	          Navigator.of(context).pop(context);
	        },
	        child: Icon(Icons.arrow_back),
	      ),
	    );
	  }
	}
##### pushNamed
	class App extends StatelessWidget {
	  @override
	  Widget build(BuildContext context) {
	    return MaterialApp(
	      // 不显示debug的标签
	      debugShowCheckedModeBanner: false,
	//      home: NavigationDemo(),
	      // 初始路由
	      initialRoute: "/about",
	      // 定义有名字的路由
	      routes: {
	        "/": (BuildContext context) => NavigationDemo(),
	        "/about": (BuildContext context) => Page(title: "About"),
	      },
	    );
	  }
	}

### 需求二十六
#### 水波纹效果
	Stack(
	  children:  [
	    ... ,
	    Positioned.fill(
	      // 水波纹效果
	        child: Material(
	          color: Colors.transparent,
	          child: InkWell(
	            splashColor: Colors.white.withOpacity(0.3),
	            highlightColor: Colors.white.withOpacity(0.1),
	            onTap: () {
	              debugPrint("Press Tab");
	            },
	          ),
	        )
	    ),
	  ],
	)

### 需求二十七
#### 点击跳转至详情
##### 点击事件
    onTap: () {
      Navigator.of(context).push(MaterialPageRoute(
          builder: (BuildContext context) =>
              ShowView(post: posts[index],)));
    }
##### 详情页
	class ShowView extends StatelessWidget {
	  final Post post;
	  ShowView({this.post});
	  @override
	  Widget build(BuildContext context) {
	    return Scaffold(
	      appBar: AppBar(
	        title: Text("${post.title}"),
	        centerTitle: true,
	        elevation: 0,
	      ),
	      body: Column(
	        children:  [
	          Image.network(post.imageUrl),
	          Container(
	            padding:EdgeInsets.all(10) ,
	            child: Column(
	              crossAxisAlignment: CrossAxisAlignment.start,
	              children:  [
	                Text(post.title,style: Theme.of(context).textTheme.title,),
	                Text(post.author,style: Theme.of(context).textTheme.subhead,),
	                SizedBox(height: 32,),
	                Text(post.description,style: Theme.of(context).textTheme.body1,)
	              ],
	            ),
	          )
	        ],
	      ),
	    );
	  }
	}


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)