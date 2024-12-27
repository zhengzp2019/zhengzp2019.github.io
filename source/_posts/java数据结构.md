---
title: java数据结构
comments: true
date: 2023-03-29 10:33:33
updated:
categories:
- [编程语言,java]
- 数据结构
- 算法
tags:
- 数据结构
mathjax: true
---

数据结构是用于存储和组织数据的存储结构。它是一种在计算机上组织数据以便可以有效访问和更新数据的方法。下图展示了数据结构的分类

![Classification of Data Structure](https://media.geeksforgeeks.org/wp-content/uploads/20220520182504/ClassificationofDataStructure-660x347.jpg)

**线性数据结构：** 数据结构中的元素按照线性且连续的的方式存储，例如数组，栈，队列，列表等，而线性数据结构又分为静态数据结构和动态数据结构

**非线性数据结构：** 数据结构中元素不是按照线性且连续的方式存储的，例如树和图

<!-- more -->
## 数组

数组把元素存储在连续内存位置的集合，如下图所示。

![Array Data Structure](https://media.geeksforgeeks.org/wp-content/uploads/20220721080308/array.png)

### 数组的定义

数组在不同的语言中都是以基本的数据类型的形式存在的，所以在使用数组时，并不需要太复杂的构造方式，下面以java语言为例，展示数组的使用

```java
// 声明一个整型数组
int []a;
// 为上述整型数组分配五个内存
a = new int[5];
```

### 数组的优缺点

优点：

- 支持随机存取
- 缓存性能好
- 可以用于实现一些其他数据结构，例如链表，栈，队列，树，图等

缺点：

- 数组长度固定
- 数组存储空间在内存中是连续的，删除和插入效率低

### 常用操作及分析

#### 数组排序

**操作过程（以选择排序为例）**

- 依次遍历nums中每一个元素i
- 对于元素i，从i开始直至结束选择其中最大的元素位置k
- 判断k是否与i相等，不等则交换
- 直至nums结束

**时间复杂度：** $O(n^2)$

**空间复杂度：** $O(n)$

**示例**

```java
// 选择排序
void selectSort(int[] nums) {
    for (int i = 0; i < nums.length; i++) {
        int k = i;
        for (int j = i; j < nums.length; j++) {
            if (nums[j] > nums[k]) k = j;
        }
        if (k != i) {
            int tmp = nums[i];
            nums[i] = nums[k];
            nums[k] = tmp;
        }
    }
}
```

#### 搜索元素

**操作过程(以线性搜索为例)**

- 循环遍历数组nums
- 判断元素i与元素target是否相同
- 若相同返回target的位置，反之返回-1

**时间复杂度：** $O(N)$

**空间复杂度：** $O(1)$

**示例**

```java
// 线性搜索
int lineSearch(int[] nums, int target) {
    for (int e : nums) {
        for (int i = 0; i < nums.length; i++)
            if (nums[i] == target) return i;
    }
    return -1;
}
```

#### 插入元素

**操作过程**

- 找到需要插入的位置id
- 将id后面的元素后移一位
- 将元素插入id位置

**时间复杂度：** $O(N)$

**空间复杂度：** $O(1)$

**示例**

```java
//    在位置index插入一个元素k
void insert(int[] nums, int index, int k) {
    for (int i = nums.length - 1; i >= 1; i--) {
        nums[i] = nums[i - 1];
        if (i == index) {
            break;
        }
    }
    nums[index] = k;
}
```

#### 删除元素

**操作过程**

- 找到待删除元素
- 把待删除元素后面的元素前移一位

**时间复杂度：** $O(N)$

**空间复杂度：** $O(1)$

**示例**

```java
//    删除元素target，并返回待删除元素位置
int delete(int[] nums, int target) {
    int pos = lineSearch(nums,target);
    if(pos==-1) return pos;
    for(int i=pos;i<nums.length-1;i++)
        nums[i]=nums[i+1];
    return pos;
}
```

#### 数组转置

**操作过程**

- 使用双指针算法

**时间复杂度：** $O(N)$

**空间复杂度：** $O(1)$

**示例**

```java
void reverse(int[] nums) {
    int i = 0, j = nums.length-1;
    int tmp;
    while (i < j) {
        tmp = nums[i];
        nums[i] = nums[j];
        nums[j] = tmp;
        i++;
        j--;
    }
}
```

## 链表

链表是一种线性数据结构，其中的元素存储在不连续位置，元素与元素之间由指针连接，如下图所示：

![Linkedlist Data Structure](https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2013/03/Linkedlist.png)

### 链表的优缺点

优点

- 相当于是动态数组
- 容易插入和删除

缺点

- 不支持随机存取
- 需要额外的空间存储指针
- 缓存性能低
- 需要花更多的时间遍历和修改指针
- 搜索时间复杂度高
- 排序操作复杂，且性能差

### 链表类型

- 单链表
- 双链表
- 循环链表
- 双循环链表
- 头链表

### 单链表的定义

链表由一个头节点替代表示，每一个元素有一个节点构成，其中包括数据项和指向下一节点的指针，若链表为空，则头节点指向NULL，下面是java语言链表构造过程

```java
class LinkedList {
	Node head; // head of the list

	/* Linked list Node*/
	class Node {
		int data;
		Node next;

		// Constructor to create a new node
		// Next is by default initialized
		// as null
		Node(int d)
		{
			data = d;
			next = null;
		}
	}
}
```

### 使用数组定义链表

### 常用操作及分析

#### 链表遍历

**操作过程**

- 定义节点引用p，从头节点开始
- 输出当前节点内容
- 指向下一节点

**示例**

```java
void traverse(MyList list) {
    Node p = list.head;
    while(p != null) {
        System.out.print(p.data + " ");
        p = p.next;
    }
}
```

#### 插入指定元素

**操作过程**

- 检测前继节点是否为空
- 为待插入节点分配空间
- 让待插入节点的后继节点为前继节点的后继节点
- 让前继节点的后继节点为待插入节点

**示例**

```java
void insert(Node pre_node, int new_data) {
    if (pre_node == null) {
        System.out.println("前继节点不能为空");
        return;
    }
    Node node = new Node(new_data);
    node.next = pre_node.next;
    pre_node.next = node;
}
```

#### 删除指定元素

**操作过程**

- 找到给定元素位置
- 将元素的后继作为元素前继的后继
- 释放元素空间

**示例**

```java
void delete(MyList list, int data) {
    Node pre = head, cur = head.next;
    while (cur != null) {
        if (cur.data == data)
            pre.next = cur.next;
        pre = cur;
        cur = cur.next;
    }
}
```

## 栈
