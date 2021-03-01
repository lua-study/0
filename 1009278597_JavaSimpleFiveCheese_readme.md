# Java五子棋项目 #
该项目主要使用到了swing编程和ImageIO类。

- 游戏开始：清空棋盘，重新绘图
- 游戏设置：设置倒计时
- 游戏说明：说明游戏规则
- 认输：某一方放弃游戏，另一方直接获胜
- 关于：显示程序的作者、版本等
- 退出：结束程序

##五子棋游戏的功能##
1. 用户点击鼠标时，将棋子渲染到相应的位置；
2. 自动判断游戏是否结束。
3. 对游戏时间进行设置，判断是否超出规定时间。

## 实现步骤 ##
1. 渲染游戏界面（swing）。新建一个类`FiveCheeseFrame`继承`JFrame`并实现`MouseListener`接口。在构造方法中初始化界面（大小、位置等）。
2. 在鼠标事件的`mouseClick()`方法中响应相关事件。
3. 为了实现倒计时，需要单独引入一个线程。

# 该游戏的难点： #
## 1.如何让游戏界面居中显示？ ##
获取屏幕的宽高和游戏的宽高。设置显示位置为屏幕的宽高减去游戏的宽高除以2就行了。

	// 取得屏幕的宽高
	int screenWidth = Toolkit.getDefaultToolkit().getScreenSize().width;
	int screenHeight = Toolkit.getDefaultToolkit().getScreenSize().height;
	System.out.println("屏幕的尺寸是：" + screenWidth + "*" + screenHeight);
	// 设置游戏界面居中显示，jf是自定义的窗体类，继承自JFrame
	jf.setLocation((screenWidth - WIDTH) / 2, (screenHeight - HEIGHT) / 2);

## 2.在鼠标点击的位置显示棋子？ ##
MouseEvent的`getX()`和`getY()`方法可以获得点击的位置。黑子可以用实心的黑圆表示，白字可以用空心黑圆+实心白圆表示。`Graphics`类的`drawOval()`和`fillOval()`方法。

## 3.之前下过的棋子的位置如何保存？ ##
通过19*19的二维数组`allChess`保存每个交叉点的状态（黑子（填充1）、白子（填充2）、无子（填充0））。

## 4.在窗口中绘制网格和图像 ##
Graphics类，类似画笔，可以在窗口中绘制文字和图像。通过覆写JFrame中的`paint()`方法来使用，通过`repaint()`方法(表示重新执行一次paint方法)来调用。

	Graphics g;
	BufferedImage image;
	try {
		image = ImageIO.read(new File("images/title.jpg")); //解决窗体透明问题只需要在窗体中绘制一张图片，在此基础上绘制其他
		g.drawImage(image, 20, 40,this);
	} catch (IOException e) {
		e.printStackTrace();
	}

## 5.如何让棋子对齐到十字线？ ##
棋盘绘制完成后，实际上就建立了如下的一个坐标轴为0~18的坐标系坐标系。
![](http://i.imgur.com/Ow2MWWl.jpg)
对于每一个鼠标点击的点，我们可以取**离鼠标点击位置最近的点**。关键就是得到0~18的整数。将大坐标转换为小坐标。

**思考**：

每个单元格是25*25像素，我们惠子棋盘的时候采用的是for循环。

	for (int i = 0; i  = 5) {
		flag = true; // flag表示是否有5子相连
	}
同理，垂直方向仅仅是x坐标不变，y的坐标每次加1，减1。和上面的算法几乎一样

左上-右下方向：如果判断方向是“左上--->右下”，则x和y的坐标每次都加1；如果从右下判断到左上，则x和y的坐标每次加1，这里同样要注意**变量i要复位。**

	// 左下-右上判断
	int i3 = 1;
	int count3 = 1;
	while (color==allChess[x+i3][y-i3]) { // 左下--->右上---> allChess[x+i3][y-i3]
		count3++;
		i3++;
	}
	i3 = 1; // i3归位
	while (color == allChess[x-i3][y+i3]) { // 右上--->左下---> allChess[x-i3][y+i3]
		count3++;
		i3++;
	}
	if (count3 >= 5) {
		flag = true;
	}
右上-左下方向的判断和左上-右下的判断类似，只是x，y的变化是异号的。

### 思考 ###
上面的4个方向的算法大体类似，我们可以将其抽象为一个方法。观察到以上4方向上的算法的不同之处就是x坐标和y轴的变化率，同时它们都需要判断当前棋子的颜色`color`,得到当前相同棋子相连的最大数`count`，将算法加以抽象得到如下的方法：

	/**
	 * 得到相同的棋子连接的数量,由上面的4次判断抽象出来的
	 * @param xChange:x的变化
	 * @param yChange：y的变化
	 * @param color：当前棋子状态（黑？白）
	 * @return
	 */
	private int checkCount(int xChange,int yChange,int color){
		
		int count = 1;
		int tempX = xChange, tempY = yChange; // 保存传过来的xChange和yChange，复位的时候需要用到
		// 首先要检查数组下标是否越界
		while (x + xChange >= 0 && x + xChange  = 0 && y + yChange   0) {
					yChange++;
				}else {
					yChange--;
				}
			}
		}
		
		xChange = tempX; // 复位
		yChange = tempY;
		// 首先要检查数组下标是否越界
		while (x - xChange >= 0 && x - xChange  = 0 && y - yChange   0) {
					yChange++;
				}else {
					yChange--;
				}
			}
		}
		return count;
	}
得到棋子数只需要这样调用以上的方法：

	/* 判断4个方向上的棋子数，判断的顺序不重要 */
	count = checkCount(1, 0, color); // 横向的棋子数
	if (count >= 5) {
		flag = true;
	}else {
		count = checkCount(0, 1, color); // 纵向的棋子数
		if (count >= 5) {
			flag = true;
		}else {
			count = checkCount(1, -1, color); // 左下-右上的棋子数
			if (count >= 5) {
				flag = true;
			}else{
				count = checkCount(1, 1, color); // 左上-右下的棋子数
				if (count >= 5) {
					flag = true;
				}
			}
		}
	}
## 7. 如何设置倒计时##
让窗体类实现`Runnable`接口，在构造方法中启动线程，并将其挂起。因为游戏刚刚启动的时候并不需要倒计时，只需要用户点击设置游戏时间之后倒计时才开始生效。声明两个全局变量`blackTime`和`whiteTime`分别保存黑方和白方额度剩余时间（初始值为0）。用户点击”游戏设置“按钮后，将时间赋值给这两个变量，重新开始游戏（清空棋盘），并将挂起的线程恢复(`resume()`方法)。在`run()`方法中首先判断是否有时间的限制，再进一步判断，当前棋子的状态，给对应的时间每隔1秒减去1，当时间变为0的时候，给用户提示，显示输赢信息，并设置不能够再次下棋。需要将时间同步显示到界面。

## 8.背景音乐的控制 ##
新引入一个背景音乐的线程，在主界面渲染（窗体的构造方法中）的时候启动线程。引入一个全局变量布尔控制背景音乐的开关，当用户点击音乐的时候改变状态，并将背景音乐挂起或者恢复。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)