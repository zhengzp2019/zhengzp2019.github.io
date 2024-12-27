---
title: QMainWindow
comments: true
date: 2020-08-08 18:16:09
updated:
categories: Qt学习记录
tags: Qt
---
[参考文档](https://www.devbean.net/2012/08/qt-study-road-2-mainwindow/)

## $MainWindow$

`QMainWindow`是 Qt 框架带来的一个预定义好的主窗口类。所谓主窗口，就是一个普通意义上的应用程序（不是指游戏之类的那种）最顶层的窗口。比如你现在正在使用的浏览器，那么主窗口就是这个浏览器窗口。通常是由一个菜单栏，若干工具栏、一个状态栏、铆接部件（悬浮窗口）及中心窗口组成，是许多应用程序的基础 。

![](mainwindowlayout.png)

![](mw-struct.png)
<!-- more -->
- 主窗口的最上面是 Window Title，也就是标题栏，通常用于显示标题和控制按钮，比如最大化、最小化和关闭等。通常，各个图形界面框架都会使用操作系统本地代码来生成一个窗口。所以，你会看到在 KDE 上面，主窗口的标题栏是 KDE 样式的；在 Windows 平台上，标题栏是 Windows 风格的。如果你不喜欢本地样式，比如 $QQ$ 这种，它其实是自己将标题栏绘制出来，这种技术称为 $DirectUI$，也就是无句柄绘制

- Window Title 下面是 Menu Bar，也就是菜单栏，用于显示菜单。
- 窗口最底部是 Status Bar，称为状态栏。当我们鼠标滑过某些组件时，可以在状态栏显示某些信息，比如浏览器中，鼠标滑过带有链接的文字，你会在底部看到链接的实际 URL。
- 最外层称为 Tool Bar Area，用于显示工具条区域。之所以是矩形表示，是因为，Qt 的主窗口支持多个工具条。你可以将工具条拖放到不同的位置，因此这里说是 Area。我们可以把几个工具条并排显示在这里，就像 $Word2003$ 一样，也可以将其分别放置，类似 $Photoshop$。
- 在工具条区域内部是 Dock Widget Area，这是停靠窗口的显示区域。所谓停靠窗口，就像$Photoshop$的工具箱一样，可以停靠在主窗口的四周，也可以浮动显示。
- 主窗口最中间称为 Central Widget，就是我们程序的工作区。通常我们会将程序最主要的工作区域放置在这里，类似 Word 的稿纸或者$Photoshop$ 的画布等等。

对于一般的 Qt 应用程序，我们所需要做的，就是编写我们的主窗口代码，主要是向其中添加各种组件，比如菜单、工具栏等，当然，最重要的就是当中的工作区。当我们将这些都处理完毕之后，基本上程序的工具也可以很好地实现。



### 1、菜单栏($QMenuBar$)

```c++
#include "mainwindow.h"
#include<QMenuBar>
#include<QMenu>
#include<QAction>

MainWindow::MainWindow(QWidget *parent)
    : QMainWindow(parent)
{
    //取出菜单栏
    QMenuBar *menu_bar1 = this->menuBar();
    //向菜单栏添加菜单
    QMenu *file_menu = menu_bar1->addMenu("文件");
    QMenu *edit_menu = menu_bar1->addMenu("编辑");
    //向菜单中添加菜单项
    QAction *open_action = file_menu->addAction("打开");
    file_menu->addSeparator();//添加菜单项的分割线
    QAction *save_action = file_menu->addAction("保存");


}

MainWindow::~MainWindow()
{
}
```



### 2、工具栏($QToolBar$)

```c++
#include "mainwindow.h"
#include<QMenuBar>
#include<QMenu>
#include<QAction>
#include<QToolBar>

MainWindow::MainWindow(QWidget *parent)
    : QMainWindow(parent)
{
    //取出菜单栏
    QMenuBar *menu_bar1 = this->menuBar();
    //向菜单栏添加菜单
    QMenu *file_menu = menu_bar1->addMenu("文件");
    QMenu *edit_menu = menu_bar1->addMenu("编辑");
    //向菜单中添加菜单项
    QAction *open_action = file_menu->addAction("打开");
    file_menu->addSeparator();//添加菜单项的分割线
    QAction *save_action = file_menu->addAction("保存");

    //获取工具栏
    QToolBar *tool_bar = this->addToolBar("");
    //向工具栏中添加工具（获取菜单项）
    tool_bar->addAction(open_action);
    tool_bar->addAction(save_action);
}

MainWindow::~MainWindow()
{
}
```



### 3、状态栏($QStatusBar$)

```c++
#include "mainwindow.h"
#include<QMenuBar>
#include<QMenu>
#include<QAction>
#include<QToolBar>
#include<QStatusBar>
#include<QLabel>

MainWindow::MainWindow(QWidget *parent)
    : QMainWindow(parent)
{
    this->resize(400,300);
    //取出菜单栏
    QMenuBar *menu_bar1 = this->menuBar();
    //向菜单栏添加菜单
    QMenu *file_menu = menu_bar1->addMenu("文件");
    QMenu *edit_menu = menu_bar1->addMenu("编辑");
    //向菜单中添加菜单项
    QAction *open_action = file_menu->addAction("打开");
    file_menu->addSeparator();//添加菜单项的分割线
    QAction *save_action = file_menu->addAction("保存");

    //获取工具栏
    QToolBar *tool_bar = this->addToolBar("");
    //向工具栏中添加工具（获取菜单项）
    tool_bar->addAction(open_action);
    tool_bar->addAction(save_action);

    //取出状态栏
    QStatusBar *status = this->statusBar();
    status->addWidget(new QLabel("状态"));//向状态栏添加控件
}
```



### 4、铆接控件($QDockWidget$)

```c++
#include "mainwindow.h"
#include<QMenuBar>
#include<QMenu>
#include<QAction>
#include<QToolBar>
#include<QStatusBar>
#include<QLabel>
#include<QDockWidget>

MainWindow::MainWindow(QWidget *parent)
    : QMainWindow(parent)
{
    this->resize(400,300);
    //取出菜单栏
    QMenuBar *menu_bar1 = this->menuBar();
    //向菜单栏添加菜单
    QMenu *file_menu = menu_bar1->addMenu("文件");
    QMenu *edit_menu = menu_bar1->addMenu("编辑");
    //向菜单中添加菜单项
    QAction *open_action = file_menu->addAction("打开");
    file_menu->addSeparator();//添加菜单项的分割线
    QAction *save_action = file_menu->addAction("保存");

    //获取工具栏
    QToolBar *tool_bar = this->addToolBar("");
    //向工具栏中添加工具（获取菜单项）
    tool_bar->addAction(open_action);
    tool_bar->addAction(save_action);

    //取出状态栏
    QStatusBar *status = this->statusBar();
    status->addWidget(new QLabel("状态"));//向状态栏添加控件

    //创建一个铆接部件
    QDockWidget *dock_widget = new QDockWidget("这是一个铆接部件",this);
    //将浮动窗口添加到mainwindow
    this->addDockWidget(Qt::TopDockWidgetArea,dock_widget);
}
```



### 5、中心控件

```c++
#include "mainwindow.h"
#include<QMenuBar>
#include<QMenu>
#include<QAction>
#include<QToolBar>
#include<QStatusBar>
#include<QLabel>
#include<QDockWidget>
#include<QTextEdit>

MainWindow::MainWindow(QWidget *parent)
    : QMainWindow(parent)
{
    this->resize(400,300);
    //取出菜单栏
    QMenuBar *menu_bar1 = this->menuBar();
    //向菜单栏添加菜单
    QMenu *file_menu = menu_bar1->addMenu("文件");
    QMenu *edit_menu = menu_bar1->addMenu("编辑");
    //向菜单中添加菜单项
    QAction *open_action = file_menu->addAction("打开");
    file_menu->addSeparator();//添加菜单项的分割线
    QAction *save_action = file_menu->addAction("保存");

    //获取工具栏
    QToolBar *tool_bar = this->addToolBar("");
    //向工具栏中添加工具（获取菜单项）
    tool_bar->addAction(open_action);
    tool_bar->addAction(save_action);

    //取出状态栏
    QStatusBar *status = this->statusBar();
    status->addWidget(new QLabel("状态"));//向状态栏添加控件

//    创建一个铆接部件
//    QDockWidget *dock_widget = new QDockWidget("这是一个铆接部件",this);
//    将浮动窗口添加到mainwindow
//    this->addDockWidget(Qt::TopDockWidgetArea,dock_widget);
    QTextEdit *text_edit = new QTextEdit("文本编辑器",this);
    this->setCentralWidget(text_edit);
}
```



### 6、资源文件

> Qt的资源系统是一个跨平台机制，用于将程序运行时所需要的资源以二进制的形式存储与可执行文件内部。如果你的程序需要加载特定的资源(图标，文本翻译等)，那么，将其放置在资源文件中，就不需要担心那些文件的丢失。也就是说，如果你将资源以资源文件的形式存储，它会编译到可执行程序的内部。

> 使用Qt Creator创建资源文件:
>
> 右击项目$->$选择"添加新文件"$->$在Qt分类下找到"Qt资源文件"
>
> 生成了一个$.qrc$文件
>
> 注:本地文件必须在项目文件目录下,如下,在项目文件Menu下建立一个image文件夹存储图片

![](image-20200718171622030.png)

```c++
#include "mainwindow.h"
#include<QMenuBar>
#include<QMenu>
#include<QAction>
#include<QToolBar>
#include<QStatusBar>
#include<QLabel>
#include<QDockWidget>
#include<QTextEdit>
#include<QPixmap>
#include<QIcon>

MainWindow::MainWindow(QWidget *parent)
    : QMainWindow(parent)
{
    this->resize(400,300);
    //取出菜单栏
    QMenuBar *menu_bar1 = this->menuBar();
    //向菜单栏添加菜单
    QMenu *file_menu = menu_bar1->addMenu("文件");
    QMenu *edit_menu = menu_bar1->addMenu("编辑");
    //向菜单中添加菜单项
    QAction *open_action = file_menu->addAction("打开");
    file_menu->addSeparator();//添加菜单项的分割线
    QAction *save_action = file_menu->addAction("保存");

    //获取工具栏
    QToolBar *tool_bar = this->addToolBar("");
    //向工具栏中添加工具（获取菜单项）
    tool_bar->addAction(open_action);
    tool_bar->addAction(save_action);

    //取出状态栏
    QStatusBar *status = this->statusBar();
    status->addWidget(new QLabel("状态"));//向状态栏添加控件

//    创建一个铆接部件
//    QDockWidget *dock_widget = new QDockWidget("这是一个铆接部件",this);
//    将浮动窗口添加到mainwindow
//    this->addDockWidget(Qt::TopDockWidgetArea,dock_widget);
    QTextEdit *text_edit = new QTextEdit("文本编辑器",this);
    this->setCentralWidget(text_edit);

    QPixmap pic;//定义一个图片对象
//    :/new/prefix1/image/earth.jpg
    pic.load(":/new/prefix1/image/earth.jpg");//给图片对象加载图片
    open_action->setIcon(QIcon(pic));
}
```

