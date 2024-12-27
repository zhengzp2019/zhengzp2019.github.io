---
title: Qt消息机制和事件
comments: true
date: 2020-08-08 22:11:47
updated:
categories: Qt学习记录
tags: Qt
---
## `Qt`消息机制和事件



### 1、事件处理过程

>事件（`event`）是由系统或者 Qt 本身在不同的时刻发出的。当用户按下鼠标、敲下键盘，或者是窗口需要重新绘制的时候，都会发出一个相应的事件。
>
>一些事件在对用户操作做出响应时发出，如键盘事件等；另一些事件则是由系统自动发出，如计时器事件。

![](207211.JPG)
<!-- more -->
### 2、鼠标事件

> 使用：重写鼠标事件虚函数

```c++
virtual void mousePressEvent(QMouseEvent *event);//鼠标点击事件
virtual void mouseReleaseEvent(QMouseEvent *event);//鼠标抬起事件
virtual void mouseDoubleClickEvent(QMouseEvent *event);//鼠标双击事件
virtual void mouseMoveEvent(QMouseEvent *event);//鼠标移动事件
```

```c++
//.h
#ifndef WIDGET_H
#define WIDGET_H

#include <QWidget>

QT_BEGIN_NAMESPACE
namespace Ui { class Widget; }
QT_END_NAMESPACE

class Widget : public QWidget
{
    Q_OBJECT

public:
    Widget(QWidget *parent = nullptr);
    ~Widget();
protected:
    void mousePressEvent(QMouseEvent *event);//鼠标点击事件
    void mouseMoveEvent(QMouseEvent *event);//鼠标移动事件
private:
    Ui::Widget *ui;
};
#endif // WIDGET_H

//.cpp
#include "widget.h"
#include "ui_widget.h"
#include<QMouseEvent>
#include<QDebug>

Widget::Widget(QWidget *parent)
    : QWidget(parent)
    , ui(new Ui::Widget)
{
    ui->setupUi(this);
}

void Widget::mousePressEvent(QMouseEvent *event)
{
    qDebug()<<"鼠标点击"<<event->x()<<event->y();
    if(event->button()==Qt::LeftButton)
    {
        qDebug()<<"点击了左键";
    }
    else if(event->button()==Qt::RightButton)
    {
        qDebug()<<"点击了右键";
    }
}

void Widget::mouseMoveEvent(QMouseEvent *event)
{
     qDebug()<<"鼠标移动"<<event->x()<<event->y();
}

Widget::~Widget()
{
    delete ui;
}
```

### 3、滚轮事件

> 使用：重写滚轮事件虚函数

```c++
virtual void wheelEvent(QWheelEvent *event);//滚轮事件
```

```c++
//.h
#ifndef WIDGET_H
#define WIDGET_H

#include <QWidget>

QT_BEGIN_NAMESPACE
namespace Ui { class Widget; }
QT_END_NAMESPACE

class Widget : public QWidget
{
    Q_OBJECT

public:
    Widget(QWidget *parent = nullptr);
    ~Widget();
protected:
    void mousePressEvent(QMouseEvent *event);//鼠标点击事件
    void mouseMoveEvent(QMouseEvent *event);//鼠标移动事件
    void wheelEvent(QWheelEvent *event);//滚轮事件
private:
    Ui::Widget *ui;
};
#endif // WIDGET_H

//.cpp
#include "widget.h"
#include "ui_widget.h"
#include<QMouseEvent>
#include<QDebug>

Widget::Widget(QWidget *parent)
    : QWidget(parent)
    , ui(new Ui::Widget)
{
    ui->setupUi(this);
}

void Widget::mousePressEvent(QMouseEvent *event)
{
    qDebug()<<"鼠标点击"<<event->x()<<event->y();
    if(event->button()==Qt::LeftButton)
    {
        qDebug()<<"点击了左键";
    }
    else if(event->button()==Qt::RightButton)
    {
        qDebug()<<"点击了右键";
    }
}

void Widget::mouseMoveEvent(QMouseEvent *event)
{
     qDebug()<<"鼠标移动"<<event->x()<<event->y();
}

void Widget::wheelEvent(QWheelEvent *event)
{
    if(event->orientation()==Qt::Vertical)
    {
        qDebug()<<"滚轮事件"<<event->x()<<event->y();
    }
}

Widget::~Widget()
{
    delete ui;
}
```

### 4、键盘事件

> 重写键盘事件虚函数

```C++
virtual void keyPressEvent(QKeyEvent *event);//键盘事件
```

```c++
//.h
#ifndef WIDGET_H
#define WIDGET_H

#include <QWidget>

QT_BEGIN_NAMESPACE
namespace Ui { class Widget; }
QT_END_NAMESPACE

class Widget : public QWidget
{
    Q_OBJECT

public:
    Widget(QWidget *parent = nullptr);
    ~Widget();
protected:
    void mousePressEvent(QMouseEvent *event);//鼠标点击事件
    void mouseMoveEvent(QMouseEvent *event);//鼠标移动事件
    void wheelEvent(QWheelEvent *event);//滚轮事件
    void keyPressEvent(QKeyEvent *event);//键盘事件
private:
    Ui::Widget *ui;
};
#endif // WIDGET_H

//.cpp
#include "widget.h"
#include "ui_widget.h"
#include<QMouseEvent>
#include<QDebug>
#include<QKeyEvent>

Widget::Widget(QWidget *parent)
    : QWidget(parent)
    , ui(new Ui::Widget)
{
    ui->setupUi(this);
}

void Widget::mousePressEvent(QMouseEvent *event)
{
    qDebug()<<"鼠标点击"<<event->x()<<event->y();
    if(event->button()==Qt::LeftButton)
    {
        qDebug()<<"点击了左键";
    }
    else if(event->button()==Qt::RightButton)
    {
        qDebug()<<"点击了右键";
    }
}

void Widget::mouseMoveEvent(QMouseEvent *event)
{
     qDebug()<<"鼠标移动"<<event->x()<<event->y();
}

void Widget::wheelEvent(QWheelEvent *event)
{
    if(event->orientation()==Qt::Vertical)
    {
        qDebug()<<"滚轮事件"<<event->x()<<event->y();
    }
}

void Widget::keyPressEvent(QKeyEvent *event)
{
    qDebug()<<event->key();
    if(event->modifiers() == Qt::ShiftModifier)
    {
        qDebug()<<"shift";
    }
    if(event->modifiers() == Qt::ControlModifier)
    {
        qDebug()<<"ctrl";
    }
}

Widget::~Widget()
{
    delete ui;
}

```

### 5、大小改变事件

> 重写大小改变事件虚函数

```c++
virtual void resizeEvent(QResizeEvent *event);//大小改变事件
```

```c++
//.h
#ifndef WIDGET_H
#define WIDGET_H

#include <QWidget>

QT_BEGIN_NAMESPACE
namespace Ui { class Widget; }
QT_END_NAMESPACE

class Widget : public QWidget
{
    Q_OBJECT

public:
    Widget(QWidget *parent = nullptr);
    ~Widget();
protected:
    void mousePressEvent(QMouseEvent *event);//鼠标点击事件
    void mouseMoveEvent(QMouseEvent *event);//鼠标移动事件
    void wheelEvent(QWheelEvent *event);//滚轮事件
    void keyPressEvent(QKeyEvent *event);//键盘事件
    void resizeEvent(QResizeEvent *event);//大小改变事件
private:
    Ui::Widget *ui;
};
#endif // WIDGET_H
//.cpp
#include "widget.h"
#include "ui_widget.h"
#include<QMouseEvent>
#include<QDebug>
#include<QKeyEvent>

Widget::Widget(QWidget *parent)
    : QWidget(parent)
    , ui(new Ui::Widget)
{
    ui->setupUi(this);
}

void Widget::mousePressEvent(QMouseEvent *event)
{
    qDebug()<<"鼠标点击"<<event->x()<<event->y();
    if(event->button()==Qt::LeftButton)
    {
        qDebug()<<"点击了左键";
    }
    else if(event->button()==Qt::RightButton)
    {
        qDebug()<<"点击了右键";
    }
}

void Widget::mouseMoveEvent(QMouseEvent *event)
{
     qDebug()<<"鼠标移动"<<event->x()<<event->y();
}

void Widget::wheelEvent(QWheelEvent *event)
{
    if(event->orientation()==Qt::Vertical)
    {
        qDebug()<<"滚轮事件"<<event->x()<<event->y();
    }
}

void Widget::keyPressEvent(QKeyEvent *event)
{
    qDebug()<<event->key();
    if(event->modifiers() == Qt::ShiftModifier)
    {
        qDebug()<<"shift";
    }
    if(event->modifiers() == Qt::ControlModifier)
    {
        qDebug()<<"ctrl";
    }
}

void Widget::resizeEvent(QResizeEvent *event)
{
    qDebug()<<event->oldSize();
    qDebug()<<event->size();
}

Widget::~Widget()
{
    delete ui;
}
```

### 6、进入离开事件

> 重写进入离开事件虚函数



```c++
virtual void enterEvent(QEvent *event);//进入事件
virtual void leaveEvent(QEvent *event);//离开事件
```

```c++
//.h
#ifndef WIDGET_H
#define WIDGET_H

#include <QWidget>

QT_BEGIN_NAMESPACE
namespace Ui { class Widget; }
QT_END_NAMESPACE

class Widget : public QWidget
{
    Q_OBJECT

public:
    Widget(QWidget *parent = nullptr);
    ~Widget();
protected:
    void mousePressEvent(QMouseEvent *event);//鼠标点击事件
    void mouseMoveEvent(QMouseEvent *event);//鼠标移动事件
    void wheelEvent(QWheelEvent *event);//滚轮事件
    void keyPressEvent(QKeyEvent *event);//键盘事件

    void resizeEvent(QResizeEvent *event);//大小改变事件
    void enterEvent(QEvent *event);//进入事件
    void leaveEvent(QEvent *event);//离开事件
private:
    Ui::Widget *ui;
};
#endif // WIDGET_H
//.cpp
#include "widget.h"
#include "ui_widget.h"
#include<QMouseEvent>
#include<QDebug>
#include<QKeyEvent>

Widget::Widget(QWidget *parent)
    : QWidget(parent)
    , ui(new Ui::Widget)
{
    ui->setupUi(this);
}

void Widget::mousePressEvent(QMouseEvent *event)
{
    qDebug()<<"鼠标点击"<<event->x()<<event->y();
    if(event->button()==Qt::LeftButton)
    {
        qDebug()<<"点击了左键";
    }
    else if(event->button()==Qt::RightButton)
    {
        qDebug()<<"点击了右键";
    }
}

void Widget::mouseMoveEvent(QMouseEvent *event)
{
     qDebug()<<"鼠标移动"<<event->x()<<event->y();
}

void Widget::wheelEvent(QWheelEvent *event)
{
    if(event->orientation()==Qt::Vertical)
    {
        qDebug()<<"滚轮事件"<<event->x()<<event->y();
    }
}

void Widget::keyPressEvent(QKeyEvent *event)
{
    qDebug()<<event->key();
    if(event->modifiers() == Qt::ShiftModifier)
    {
        qDebug()<<"shift";
    }
    if(event->modifiers() == Qt::ControlModifier)
    {
        qDebug()<<"ctrl";
    }
}

void Widget::resizeEvent(QResizeEvent *event)
{
    qDebug()<<event->oldSize();
    qDebug()<<event->size();
}

void Widget::enterEvent(QEvent *event)
{
    qDebug()<<"进入";
}

void Widget::leaveEvent(QEvent *event)
{
    qDebug()<<"离开";
}

Widget::~Widget()
{
    delete ui;
}

```