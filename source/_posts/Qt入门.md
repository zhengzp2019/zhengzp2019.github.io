---
title: Qt入门
comments: true
date: 2020-08-06 21:23:38
updated:
categories: Qt学习记录
tags: Qt

---

# QT入门

### 1、程序运行框架

```c++
#include <QApplication>

int main(int argc, char *argv[])
{
    //创建一个应用类的对象
    //有且仅有一个应用类的对象
    QApplication a(argc, argv);
    
    //创建一个窗口对象
    QWidget w;
    //窗口默认是隐藏的，需要用户手动显示
    w.show();
    //让程序一直执行下去，等待用户操作
    //即，等待事件的发生
    return a.exec();
}

```

<!-- more -->
### 2、qt的命名规则

- Qt构件(类)命名为首字母大写。

- 变量为以“_”联接小写单词。

- 默认文件名全部是小写。

- 宏全部是大写。

- 成员函数驼峰原则,第一个单词首字母小写,其余单词首字母大写

  > 骆驼式命名法（又称驼峰命名法），正如它的名称$CamelCase$所表示的那样，是指混合使用大小写字母来构成变量和函数的名字。

### 4、按钮的创建和属性设置

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
    //为了让按钮的生成期为程序结束，在这里定义一个按钮的指针
    QPushButton *button;
};
#endif // WIDGET_H
#include "widget.h"
#include<QPushButton>

Widget::Widget(QWidget *parent)
    : QWidget(parent)
{
    //button=new QPushButton("郑展鹏",this);//在创建对象的同时指定按钮文本和父类
    button=new QPushButton;
    button->show();//显示按钮，继承于QWidght
    //指定按钮的父类为窗口
    button->setParent(this);//指定按钮的父亲是窗口
    button->setText("郑展鹏");//指定按钮标签
    button->move(50,50);//指定按钮在窗口中位置
    button->resize(100,100);//指定按钮大小
    this->resize(400,300);//指定窗口大小
}

Widget::~Widget()
{
}
```



### 5、QT对象树

- 当创建一个对象时，系统会将新建的对象自动添加到其父对象的children()列表

- 当父对象被析构时，其children()列表中的所有对象都会被析构

- $Qwidget$继承自$QObject$，因此也继承了这种对象树关系，一个孩子自动的成为父组件的子组件

- 若删除子对象，则它会自动从父对象列表中删除

- 保证没有对象会被析构两次

- 局部对象的析构顺序于创建顺序相反

  ```C++
  //新建一个mybutton,继承自QPushButton
  #ifndef MYBUTTON_H
  #define MYBUTTON_H
  
  #include<QPushButton>
  
  class mybutton : public QPushButton
  {
  public:
      mybutton();
      ~mybutton();
  };
  
  #endif // MYBUTTON_H
  
  //.cpp
  #include "mybutton.h"
  #include<QDebug>
  using namespace std;
  
  mybutton::mybutton()
  {
  
  }
  
  mybutton::~mybutton()
  {
      qDebug()<<"mybutton的析构";
  }
  //注：在Qt下输出语句使用QDebug中的qDebug(),而不是iostream里的cout
  ```

  ### 6、QT的坐标体系

  > 窗口左上角为原点（0，0），X向右增加，Y向下增加
  >
  > 对于嵌套窗口其坐标时相对于父窗口来说的