#### C++实现五子棋项目
***
##### 开发时间：2019.07.26
##### 开发者：Summer
##### 开发工具：Visual studio 2019
***
[一、演示效果](#1)

[二、头文件](#2)

[三、主函数](#3)

[四、画出棋盘](#4)

[五、下棋](#5)

[六、判断输赢](#6)

***
 一、演示效果 

![Alt](./demo.gif)

***
 二、头文件 

```cpp
#include 
#include 	//图形库头文件
#include 	//播放音乐头文件
#include 

#pragma comment(lib, "winmm.lib")	//播放音乐库文件

int flag = 0;	//表示下棋次数
int board[20][20] = { 0 };	//0表示棋盘没有棋子状态

void initGame();
int judge(int a, int b);
void playChess();
```
***
 三、主函数 

```cpp
int main() {

	initGame();
	playChess();

	getchar();
	return 0;
}
```
***
 四、画出棋盘 

```cpp
//1.画出棋盘
void initGame() {		//初始化游戏

	//1.1 绘图环境 库函数
	//默认调用系统的窗口
	initgraph(600, 500);	//创建自定义窗口
	//setbkcolor(BLUE);	//设置窗口背景颜色
	//cleardevice();	//刷新

	//1.2 贴图
	loadimage(NULL, "./src/bg.jpg");

	//1.3 背景音乐	mci 多媒体控制结口
	mciSendString("open ./src/skyCity.mp3", 0, 0, 0);
	//mciSendString("play ./src/skyCity.mp3", 0, 0, 0);

	//setlinecolor(BLACK);
	//1.4 绘制棋盘
	//画线 20 20 25 25 500 500
	for (int i = 0; i  五、下棋 

```cpp
//2.下棋
void playChess() {
	//鼠标
	MOUSEMSG m;	//保存鼠标消息
	int x=0, y=0;	//坐标
	int a=0, b=0;	//行列

	//持续下棋
	while (1) {
		m = GetMouseMsg();	//获取一个鼠标消息

		//获取离鼠标最近的点的坐标信息
		for (int i = 1; i  六、判断输赢 

```cpp
//3.判断输赢
int judge(int a, int b) {
	int i, j;
	int t = 2 - flag % 2;	//1 判断黑子是否赢	2 判断白子是否赢

	//横向
	for (i = a - 4, j = b; i   0 && i   0 && j   0 && i   0 && j  = b; i++, j--) {
		if (i > 0 && i   0 && j < 16 && t == board[i][j] && t == board[i + 1][j - 1] && t == board[i + 2][j - 2] && t == board[i + 3][j - 3] && t == board[i + 4][j - 4]) {
			return 1;
		}
	}

	return 0;
}
```
***


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)