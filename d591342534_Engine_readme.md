# Engine
C++服务器编程底层库

## 特点
1. Windows，Linux双平台（Windows下为静态库，主要方便开发者调试；Linux下为动态库，用于生产环境部署）
2. 基本包含集成服务器常用模块（数学、文件系统、配置、日志、网络、脚本、时间、多线程等）
3. 二次开发无平台配置，无其他依赖
4. 基于C++11开发

## 使用

1. Windows下直接使用VS2017打开工程编译生成：`build/Engine.lib`与`build/Engined.lib`静态库
2. Linux下使用make生成`libengine.so`动态库

> 注：Linux下建议使用GCC的`-Wl,-rpath,XXX`连接选项指定运行期动态连接库的优先查找目录，以方便分发部署

## 集成第三方说明
1. Zip使用[miniz](https://storage.googleapis.com/google-code-archive-downloads/v2/code.google.com/miniz/miniz_v115_r4.7z) v1.15 r4.
2. [Lua](http://www.lua.org/ftp/lua-5.3.4.tar.gz) v5.3.4.
3. 集成[Jsoncpp](https://github.com/open-source-parsers/jsoncpp)

## 模块

### 程序模型

```cpp
#include	 

class GameApp : public Application {
public:
	GameApp() {}

	virtual bool	OnInit(Command & rCmd) override {
		if (rCmd.Has("--debug")) {
			Logger::Instance().Init("game", "logs", 1024 * 1024 * 4, ELog::Debug);
		} else {
			Logger::Instance().Init("game", "logs", 1024 * 1024 * 4, ELog::Info);
		}

		/// 锁帧
		LockFPS(20);

		/// 填写其他初始化逻辑，当返回false时程序直接退出
		return true;
	}

	virtual void	OnBreath() override {
		/// 这里填写需要每帧更新的逻辑
	}
};

RUN_APP(GameApp)
```

### 网络模型

> 1. 头文件 : Network.h
> 2. 客户端继承IConnector，服务器继承IService
> 3. 需要在主线程中调用Breath()来触发一次累计接收信息的处理(如果使用Application类，则不需要)
> 4. Windows平台目的是开发期调试，采用了select模型；Linux下则采用了epoll模型

以客户端为例：

```cpp
#include	 
#include	 

#define		GServer	ServerConnect::Instance()

class ServerConnect : public IConnector, public ISingleton  {
public:
	ServerConnect() {}

	...
}

/// 在主线程的初始化
bool GameApp::OnInit(Command & rCmd) {
	...

	GServer.Connect(...);

	...
}

/// 在主线程Breath中调用
void GameApp::OnBreath() {
//	Application 模型中不需要手动调用Breath，底层自动调用
//	GServer.Breath();	//! 触发一次累计已接收消息的处理。自动回调OnReceive
}

```

### 脚本

> 1. 设计原则：Lua只负责逻辑，对象生存管理交由C++（可以注册管理到Lua）
> 2. 涉及到Get操作，需要try...catch以捕获类型异常（C++注册到Lua的接口内Get不需要，调用函数不需要）
> 3. Property可以为地址方式，也可以为Getter(T (void))、Setter(void (reference type T))方式注册
> 4. Method必须为`int (*f)(LuaState &)`
> 5. Lua不可用于多线程，只能在主线程中使用，但可以使用协程。

```cpp
#include	 

/// 注册公共变量或函数到Lua
GLua.Register("GameSetting")	//! 所有下面注册的属性或函数放在GameSetting中
	.Property("nPlayerCounter", &GPlayerCount, false)	//! 以地址方式注册属性，同时设置不可写
	.Property("nTime", &GetTime)	//! 以Getter方式注册属性，同时不注册属性的写方法（不可写）
	.Method("GetAById", &GetAById);	//! 注册全局Lua方法

/// 注册C++类到Lua
GLua.Register ("LuaA")
	.Property("nId", &A::nId, false)
	.Property("sName", &A::GetName, &A::SetName)
	.Method("Msg", &A::SendMessage);

try {
	A * p = GLua.Get ("me");	// 需要使用try，因为可能类型不匹配
} catch (...) {}

if (GLua.Is ("me")) {} // 不需要try
GLua.Set ("me", new A) // 不需要try
GLua.Call("GameSetting", "GetAById", 100); // 不需要try

int GetAById(LuaState & r) {
	int n = r.Get (1);	// 不需要try
	...
}
```

LUA中扩展C++注册的类或名空间（注只能扩展方法，不可扩展属性）
```lua
local tbClass = extends("LuaA")

function tbClass:Test()
	print("hehe")
end
```

### 内存池

> 1. 由于本人能力有限，经实际效率测试，目前仅保留非线程安全的对象Pool（Pool.h）
> 2. Pool加锁后可用于多线程，但经测试效率还不及系统的new，但Linux下相差不大，如果考虑到无内存碎片的优点，可以自行添加。
> 3. 如果采用Application的模型，Pool基本上是够用的。因为逻辑主要在主线程的Tick中触发

### 线程池模型

First. 编写线程内的具体工作类，继承IRunnable.

```cpp
#include	 

class DemoTask : public IRunnable {
public:
	DemoTask(...) { ... }			//! 这里为该工作参数初始化
	virtual ~DemoTask() { ... }		//! 这里为工作结束时清理操作

	virtual void	Run() { ... }	//! 工作的具体内容

private:
	...		//! 参数声明
};
```

Second. 对于单一工作的线程池，推荐使用容器Runnable 

```cpp
int main() {
	Runnable 	iMgr(4);	//! 创建含有一个4个工作线程的容器

	/// 增加100个并发任务（多余的会暂时等待空闲线程）
	for (int i = 0; i < 100; ++i) {
		iMgr.Create(...);	// 传入工作需要的参数，这里自动调用 new DemoTask(...);
	}

	/// 等待所有的工作结束，如果不执行该操作，iMgr超出生存期时会放弃未执行的任务。
	iMgr.WaitAll();
	return 0;
}
```

Another. 对于多种类型任务共用一个线程池时，请使用ThreadPool.

```cpp
int main() {
	ThreadPool iMgr(4);

	/// 添加一种任务
	for (int i = 0; i < 50; ++i) {
		iMgr.AddRunnable(new DemoTask(...));	//! 请务必使用new，因为当工作结束时会自动调用delete
	}

	/// 添加另一种任务
	for (int j = 0; j < 50; ++j) {
		iMgr.AddRunnable(new DemoTask2(...));
	}

	iMgr.WaitAll();
	return 0;
}
```

### 日志

1. 多线程安全
2. 日志使用之前可以初始化（不是必要的，但建议初始化—）

日志生成的结构说明

	RootOfLogs						指定的日志根目录
	|-- 20160803					首先日志会根据“年月日”分文件夹
	|	|-- main_01_00_00.000.log	其次日志会按指定大小分文件记录，文件名为指定的"Name_时_分_秒.毫秒.log"
	|	|-- main_01_27_18.193.log

```cpp
/// 初始化日志。日志名为main, 放在logs目录下，每个文件最大为4M，输出等级为DEBUG，写文件的同时输出到终端
Logger::Instance().Init("main", "logs", 4 * 1024 * 1024, ELog::Debug, true);

/// 写日志
LOG_INFO("Hello");
LOG_DEBUG("Hello %d", 2);
LOG_ERR("Error : %s", "Test");
LOG_WARN("You have a warning");
```

### 工具库

1. 单例模型：ISingleton(Singleton.h)
2. 生存域模型：Guard(Guard.h)
3. 其他：Utils.h

### 配置库

1. CSV文件的读取见：CsvFile（CsvFile.h）
2. INI文件的读取见：IniFile（IniFile.h）
3. 命令行参数解析：Command（Command.h）
4. JSON文件，使用jsoncpp：Json::Value, Json::Reader (Json.h)

### 数学

1. CRC32算法：CalcCRC（Crypto.h）
2. BKDRHash算法：CalcHash（Crypto.h）
3. MD5工具：MD5（Crypto.h）
4. ZIP压缩/解压缩算法：Zip（Compress.h）

### 系统相关

1. 高精度时间。DateTime.h
2. 文件系统。Path.h


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)