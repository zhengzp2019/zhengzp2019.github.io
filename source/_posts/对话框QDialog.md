---
title: 对话框QDialog
comments: true
date: 2020-08-08 22:08:00
updated:
categories: Qt学习记录
tags: Qt
---

[基本概念参考](https://www.devbean.net/2012/09/qt-study-road-2-dialogs-intro/)

[标准对话框参考](https://www.devbean.net/2012/09/qt-study-road-2-standard-dialogs-qmessagebox/)

## 对话框QDialog

### 1、基本概念

> 对话框是GUI程序中不可或缺的组成部分.很多不能或者不适合放在主窗口的功能组件都必须放在对话框中设置。对话框通常是一个顶层窗口,出现在程序最上层,用于实现短期任务或者简洁的用户交互。
>
> QT中使用`ＱDialog`类实现对话框。就像主窗口一样，我们通常会设计一个类继承`QDialog`。`QDialog`（及其子类，以及所有`Qt::Dialog`类型的类）的对于其 parent 指针都有额外的解释：如果 parent 为 NULL，则该对话框会作为一个顶层窗口，否则则作为其父组件的子对话框（此时，其默认出现的位置是 parent 的中心）。顶层窗口与非顶层窗口的区别在于，顶层窗口在任务栏会有自己的位置，而非顶层窗口则会共享其父组件的位置。



> 对话框分为模态对话框和非模态对话框。
>
> - 模态对话框，就是会阻塞同一应用程序中其它窗口的输入。
>
>   比如“打开文件”功能。你可以尝试一下记事本的打开文件，当打开文件对话框出现时，我们是不能对除此对话框之外的窗口部分进行操作的。
>
> - 与此相反的是非模态对话框，例如查找对话框，我们可以在显示着查找对话框的同时，继续对记事本的内容进行编辑。

<!-- more -->
### 2、标准对话框

> 所谓标准对话框，是 Qt 内置的一系列对话框，用于简化开发。事实上，有很多对话框都是通用的，比如打开文件、设置颜色、打印设置等。这些对话框在所有程序中几乎相同，因此没有必要在每一个程序中都自己实现这么一个对话框。



Qt 的内置对话框大致分为以下几类：

- `QColorDialog`：选择颜色；
- `QFileDialog`：选择文件或者目录；
- `QFontDialog`：选择字体；
- `QInputDialog`：允许用户输入一个值，并将其值返回；
- `QMessageBox`：模态对话框，用于显示信息、询问问题等；
- `QPageSetupDialog`：为打印机提供纸张相关的选项；
- `QPrintDialog`：打印机配置；
- `QPrintPreviewDialog`：打印预览；
- `QProgressDialog`：显示操作过程。

```c++
#ifndef WIDGET_H
#define WIDGET_H

#include <QWidget>
#include<QPushButton>

class Widget : public QWidget
{
    Q_OBJECT

public:
    Widget(QWidget *parent = nullptr);
    ~Widget();
    QPushButton *button;
};
#endif // WIDGET_H

//.cpp
#include "widget.h"
#include<QFileDialog>
#include<QDebug>

Widget::Widget(QWidget *parent)
    : QWidget(parent)
{
    this->resize(400,300);
    button = new QPushButton("选择文件",this);
    button->resize(100,100);
    button->move(50,50);
    connect(button,&QPushButton::clicked,this,[](){
//        返回一个已打开文件的绝对路径，并输出
//        QString str = QFileDialog::getOpenFileName();
//        qDebug()<<str;
//        返回多个已打开文件的绝对路径，并输出
        QStringList str = QFileDialog::getOpenFileNames();
        qDebug()<<str;
    });
}

```



### 3、模态对话框

>模态对话框分为如下两种对话框：
>
>- 默认是应用程序级别的模态。应用程序级别的模态是指，当该种模态的对话框出现时，用户必须首先对对话框进行交互，直到关闭对话框，然后才能访问程序中其他的窗口
>- 窗口级别的模态是指，该模态仅仅阻塞与对话框关联的窗口，但是依然允许用户与程序中其它窗口交互。窗口级别的模态尤其适用于多窗口模式



```c++
#include "widget.h"
#include<QFileDialog>
#include<QDebug>
#include<QDialog>

Widget::Widget(QWidget *parent)
    : QWidget(parent)
{
    this->resize(400,300);
    button = new QPushButton("选择文件",this);
    button->resize(100,100);
    button->move(50,50);
    connect(button,&QPushButton::clicked,this,[](){
//        返回一个已打开文件的绝对路径，并输出
//        QString str = QFileDialog::getOpenFileName();
//        qDebug()<<str;
//        返回多个文件的绝对路劲，并输出
        QStringList str = QFileDialog::getOpenFileNames();
        qDebug()<<str;
    });

    QPushButton *button1 = new QPushButton("模态对话框",this);
    button1->resize(100,100);
    button1->move(200,50);
    connect(button1,&QPushButton::clicked,this,[](){
//        定义一个对话框
        QDialog dialog;
        dialog.setWindowTitle(tr("hello,dialog!"));//设置对话框标题
        dialog.exec();//阻塞对话框
    });
}

```



### 4、非模态对话框

```c++
#include "widget.h"
#include<QFileDialog>
#include<QDebug>
#include<QDialog>

Widget::Widget(QWidget *parent)
    : QWidget(parent)
{
    this->resize(800,600);
    button = new QPushButton("选择文件",this);
    button->resize(100,100);
    button->move(50,50);
    connect(button,&QPushButton::clicked,this,[](){
        //返回一个已打开文件的绝对路径，并输出
        //QString str = QFileDialog::getOpenFileName();
        //qDebug()<<str;
        //返回多个文件的绝对路劲，并输出
        QStringList str = QFileDialog::getOpenFileNames();
        qDebug()<<str;
    });

    QPushButton *button1 = new QPushButton("模态对话框",this);
    button1->resize(100,100);
    button1->move(200,50);
    connect(button1,&QPushButton::clicked,this,[](){
        //定义一个对话框
        QDialog dialog;
        dialog.setWindowTitle(tr("hello,dialog!"));//设置对话框标题
        dialog.exec();//阻塞对话框
    });

    QPushButton *button2 = new QPushButton("非模态对话框",this);
    button2->resize(100,100);
    button2->move(350,50);
    connect(button2,&QPushButton::clicked,this,[](){
        //定义一个对话框
        QDialog *dialog=new QDialog;
        dialog->setAttribute(Qt::WA_DeleteOnClose);//关闭时会自动释放内存
        dialog->setWindowTitle(tr("非模态，dialog"));//设置对话框标题
        dialog->show();//显示对话框
    });
}

```



### 5、消息对话框

```c++
#include "widget.h"
#include<QFileDialog>
#include<QDebug>
#include<QDialog>
#include<QMessageBox>

Widget::Widget(QWidget *parent)
    : QWidget(parent)
{
    this->resize(400,300);
    button = new QPushButton("关于",this);
    button->resize(100,100);
    button->move(50,50);
    connect(button,&QPushButton::clicked,this,[this](){
        //显示关于对话框
        QMessageBox::about(this,"标题","这是一个关于对话框！");
    });

    QPushButton *button1 = new QPushButton("询问",this);
    button1->resize(100,100);
    button1->move(200,50);
    connect(button1,&QPushButton::clicked,this,[this](){
        //显示关于对话框
        int ret = QMessageBox::question(this,"标题","你需要吗？",QMessageBox::Open|QMessageBox::Save);
        if(ret==QMessageBox::Open)
        {
            qDebug()<<"open";
        }
        else
        {
            qDebug()<<"save";
        }
    });
}

```