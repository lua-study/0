# BorderlessWindow for Qt
Native borderless window for Windows OS. Allows to create gui like in Office 2013 or Visual Studio 2012.
 
 
![ScreenShot](https://raw.githubusercontent.com/deimos1877/BorderlessWindow/master/Screenshots/MainWindow.png)
 
 

### Difference from Qt:FramelessWindowHint
* Resizable
* Draggable
* Minimize animation
* Aero snap support
* Aero shake support
* ALT+Space system menu works
* System shadow support
 
 

### General Info
Creates a simple borderless WinAPI window, like [this one](http://stackoverflow.com/questions/16765561/borderless-window-using-areo-snap-shadow-minimize-animation-and-shake). Then adds QWinWidget from QtWinMigrate and fills window with it.

Then you can use that QWinWidget to create your Qt gui.

Resizable edges of the window is drawn by WinAPI, everything else is handled by QWinWidget.

Application has two event loops: one from WinApi, one from QApplication. You should use appropriate event loop, depending on what event you trying to catch.

For simplicity, my example uses only one QWinWidget. Keep in mind, that you can add multiple QWinWidgets, if necessary.

Code obviously works only on Windows OS. Should work fine with both Qt4 and Qt5. Tested with Visual Studio 2012 Compiler (Qt 4.8.5 and Qt 5.3.)

If you use Visual Studio, you'll need to import BorderlessWindow.pro file (VS Main menu -> Qt -> open Qt Project file).
 
 

### Usage
* main.cpp -> Example
* MainWindow.cpp -> WinAPI Window
* QMainPanel.cpp -> QWinWidget, add your widgets here

Controls:
* F5 - Toggle resizable
* F6 - Toggle borderless/normal window
* F7 - Toggle shadow

```
BorderlessWindow( QApplication *app, HBRUSH windowBackground, const int x, const int y, const int width, const int height );
```

Toggle functions
```
void toggleBorderless();
void toggleShadow();
void toggleResizeable();
bool isResizeable();
```
  
Size constrains
```
void setMinimumSize( const int width, const int height );
bool isSetMinimumSize();
void removeMinimumSize();
int getMinimumHeight();
int getMinimumWidth();

void setMaximumSize( const int width, const int height );
bool isSetMaximumSize();
int getMaximumHeight();
int getMaximumWidth();
void removeMaximumSize();
```





 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)