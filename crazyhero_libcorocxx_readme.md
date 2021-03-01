#libcorocxx

1. c++的协程库，参考libcoro库。
2. 支持MacOS，Windows，Linux三个平台。
3. 使用cmake进行项目编译管理。

```cpp
class Hi : public CoroFunc {
public:
	Hi(const std::string msg)
		: _msg(msg) { }

	void operator()(const Coro &coro) {
		std::cout << "first hello:" << _msg << std::endl;
		coro.yield(Coro::getMainCoro());
		std::cout << "second hello:" << _msg << std::endl;
		coro.stop(Coro::getMainCoro());
		std::cout << "??? :" << _msg << std::endl;
	}
private:
	std::string _msg;
};

int main() {
	{
		
		Hi china("China");

		Coro chinaCoro(&china);

		std::cout << "main start" << std::endl;
		Coro::getMainCoro().yield(chinaCoro);
		std::cout << "main restore" << std::endl;
		Coro::getMainCoro().yield(chinaCoro);
		std::cout << "main end" << std::endl;
	}
#ifdef _WIN32
	getchar();
#endif
	return EXIT_SUCCESS;
}
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)