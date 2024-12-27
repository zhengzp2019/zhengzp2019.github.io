---
title: java基础
comments: true
date: 2023-03-24 16:05:26
updated:
categories:
- [编程语言, java]
tags:
- 编程
---

## 基本术语

1. **类(class)：** 类的实例的蓝图，描述实例对象行为和状态的模板

2. **对象(object)：** 类的实例化，具有行为和状态。

3. **方法(Method)：** 对象的行为

4. **实例变量(instance variable)：** 对象的状态

   **例如：**

   一辆车的设计图纸——类

   具体的一辆车(大众)——对象

   车的一些行为(加速，启动，打开车门，打开车窗)——方法

   车的具体的部件(发动机，车门，车窗)——实例变量
<!-- more -->
## 注释与命名规范

**注释**：

- 单行注释——//
- 多行注释——/*  */
- 文档注释——/** */

**源文件名：** 源文件名要与源文件中的公有类名完全相同，若源文件中无公有类，则两者可以不同

**大小写敏感：** Java中大小写字母视为不同的字符，Student与student视为不同的标识符

**类名：** 一般首字母大写，若有多个单词则每个单词的首字母都要大写

## Hello world程序解释

**public static void main(String []args)：**

- public：方法作用域
- static：方法属性
- void：方法返回值
- main：方法名，Java程序的进入点，Java程序从这里开始，类似于C/C++中main函数
- String []args：操作系统传递给Java程序的参数

**方法名：** 一般首字母小写，若有多个单词，则处第一个单词外其余单词首字母大写

## Java标识符命名规则

**Java标识符：** 包括局部变量，实例，类变量，标签，类名，包名，模块，方法。所有的标识符中的字符都可以以字母，\$，下划线，数字定义，但是首字符不可以是数字。下划线一般不推荐使用（这里与python规范不同）

- 不能以数字开头
- 大小写敏感
- 无长度要求，但不推荐过长
- 保留字不能作为标识符

## Java数据类型

数据类型可以根据语言特性分为静态数据类型和动态数据类型。

- 静态数据类型：在编译时已经知道变量和表达式类型，变量一旦被声明为一种数据类型，就不能被在被声明为其他数据类型，例如C，C++，Java

- 动态数据类型：变量可以不同时间接受不同的数据类型，例如Ruby，Python

Java是静态类型的，并且是一种强类型的语言。在Java中每中数据类型在使用前都必须预先定义，并且所有的常量或变量都必须使用一种数据类型描述。

Java中有两种数据类型，一种是原始数据类型一种是非原始数据类型也叫引用数据类型。类型示意图如下：

![Java Data Types](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20191105111644/Data-types-in-Java.jpg)

**原始数据类型：** 一共有八类，在Java中预定义好的数据类型，具体类型以及每种类型的一些描述和字长如下：

![Java Primitive Data Type](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20191105122725/Primitive-Data-Types-in-Java-4.jpg)

**非原始数据类型或引用数据类型：** 包含变量的内存地址，并且引用类型在内存中不直接存储变量的值。下面列出一些常用的引用数据类型

- String

  > 类似于字符数组，但是String类型不以空字符结尾
  >
  > 声明String的语法：
  >
  > <String_type> <string_variable> = "sequence_of_string";

- Class

  > 类的声明包括如下内容：
  >
  > 修饰符：一个类可以是public或者default的
  >
  > 类名：
  >
  > 父类，超类：可有可无
  >
  > 接口：可有可无
  >
  > 主体：由{}包含

- Object

  > 类的实体部分，一个对象包含如下内容：
  >
  > 状态，行为，标识符

- Interface

  > 像类一样，接口有自己的方法和变量，方法声明在接口内部但不定义，即接口内部的方法事抽象的

- Array

  > 数组是一组相似类型的变量，数组在Java中的工作方式与c，cpp是不同的
  >
  > - java中所有数组是动态分配的
  > - Array在java中是一个对象，所以可以直接获得成员长度（这里与c，cpp不一样）
  > - Java数组对象也可以在其他数据类型后面加[]的方式声明
  > - 索引从0开始
  > - 数组可以被当作静态变量，局部变量或者方法参数使用
  > - 数组长度必须使用int值指定，而不能是long或者short的
  > - 数组的直接超类是Object
  > - 每个数组都实现了接口Cloneable

## Java变量

### 声明一个变量

![img](https://media.geeksforgeeks.org/wp-content/uploads/20191110223008/java-declare.jpeg)

### 初始化变量

![img](http://media.geeksforgeeks.org/wp-content/uploads/Variables-in-Java.png)

### Java中的变量类型

![img](https://media.geeksforgeeks.org/wp-content/uploads/20220216012050/variabletypes.png)

- 局部变量：定义在块，方法或者构造函数中，作用域也在这些范围内
- 实例变量：非静态变量，声明在类内，块，方法或者构造函数之外
- 静态变量：也叫做类变量，声明方式与实例变量形似，需要用static关键字声明，每个类只有一个静态变量的拷贝，不论有多少对象被创建，如果使用对象名访问静态变量，则编译器会自动把对象名替换为类名

### 静态变量在java和cpp中的不同与相同

**相同点**

- 二者都可以声明静态变量
- 二者都可以声明静态方法
- 访问静态成员都不需要创建对象，而可以直接使用类名访问

**不同点**

|         C++          |               java               |
| :------------------: | :------------------------------: |
|     不支持静态块     | 支持静态块，一般用于静态初始化类 |
| 可以声明静态局部变量 |        不支持静态局部变量        |

## Java中的Wrapper类

Wrapper是在java中是其对象包装的类或者包含原始数据类型。当我们为Wrapper类创建一个对象时，它包含一个字段，我峨嵋你可以存储原始数据类型。也就是我们可以将原始数据类型包装到Wrapper类对象中。

### 需要Wrapper类的场景

- 将原始数据类型转换为对象时
- 一些集合框架中的数据结构，例如ArrayLsit和Vector中只存储对象，而不存储原始数据类型
- java.util中包含一些只处理对象的类
- 在多线程中需要支持同步的对象

### 原始数据与相应的Wrapper类

![Wrapper-Class-in-Java](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20200806191733/Wrapper-Class-in-Java.png)

### 自动包装(autoboxing)与解包(unboxing)

**Autoboxing：** 将原始数据类型自动转化为Wrapper类型

示例如下：

```java
// Java program to demonstrate Autoboxing

import java.util.ArrayList;
class Autoboxing {
	public static void main(String[] args)
	{
		char ch = 'a';

		// Autoboxing- primitive to Character object
		// conversion
		Character a = ch;

		ArrayList<Integer> arrayList
			= new ArrayList<Integer>();

		// Autoboxing because ArrayList stores only objects
		arrayList.add(25);

		// printing the values from object
		System.out.println(arrayList.get(0));
	}
}
```

**unboxing：** `autoboxing`的逆过程，将Wrapper类型自动转换为原始数据类型

示例如下：

```java
// Java program to demonstrate Unboxing
import java.util.ArrayList;

class Unboxing {
	public static void main(String[] args)
	{
		Character ch = 'a';

		// unboxing - Character object to primitive
		// conversion
		char a = ch;

		ArrayList<Integer> arrayList
			= new ArrayList<Integer>();
		arrayList.add(24);

		// unboxing because get method returns an Integer
		// object
		int num = arrayList.get(0);

		// printing the values from primitive data types
		System.out.println(num);
	}
}
```



## 变量的作用域

### 成员变量（类层次的作用域）

这些变量声明在类内方法外，他们可以在类内任何地方声明和访问，只需要保证在访问前声明即可

```java
public class Test
{
    // All variables defined directly inside a class 
    // are member variables
    int a;
    private String b;
    void method1() {....}
    int method2() {....}
    char c;
}
```

- 成员变量的访问权限不影响类内的作用域
- 成员变量在类外可以按照如下规则访问

|      修饰符       | 包内 | 子类 | 全局 |
| :---------------: | :--: | :--: | :--: |
|      public       |  Y   |  Y   |  Y   |
|     protected     |  Y   |  Y   |  N   |
| Default(无修饰符) |  Y   |  N   |  N   |
|      private      |  N   |  N   |  N   |

### 局部变量(方法层次的作用域)

变量声明在方法内，具有方法层次的作用域，不可以在方法外访问

```java
class Test
{
    private int x;
    public void setX(int x)
    {
        this.x = x;
    }
}
```

这里使用this关键字区别局部变量和成员变量

### 循环变量(块层级的作用域)

声明在一对大括号内部的变量，其作用域在大括号内部，不可在括号外部访问，如下错误实例

```java
class Test
{
	public static void main(String args[])
	{
		for (int x = 0; x < 4; x++)
		{
			System.out.println(x);
		}

		// Will produce error
		System.out.println(x);
	}
}
```

但是下述代码就是成立的

```java
class Test {
	public static void main(String args[])
	{
		for (int i = 1; i <= 10; i++) {
			System.out.println(i);
		}
		int i = 20;
		System.out.println(i);
	}
}
```

**Java与cpp的关于循环变量的区别**

在cpp中外部作用域和内部作用域可以声明同名的变量，但是在java中外部作用域和内部作用域不可以声明同名的变量。~~这种区别来自于Java和cpp存储变量的方式不同。~~

## Java标准输入输出

### 输入

Java标准I/O包中提供两种用于读取用户输入的类：BufferReader，Scanner

**BufferReader**

该类可以用于读取字符序列，它包含一些读取字符和字符行的方法，**read**和**readline**。**InputStreamReader**是一个将字节流转化为字符流的函数，以至于它的输出可以被**BufferReader**类读取，并且**BufferReader**可以抛出异常。

```java
// Java Program for taking user
// input using BufferedReader Class
import java.io.*;

class GFG {

	// Main Method
	public static void main(String[] args)
		throws IOException
	{
		// Creating BufferedReader Object
		// InputStreamReader converts bytes to
		// stream of character
		BufferedReader bfn = new BufferedReader(
			new InputStreamReader(System.in));

		// String reading internally
		String str = bfn.readLine();

		// Integer reading internally
		int it = Integer.parseInt(bfn.readLine());

		// Printing String
		System.out.println("Entered String : " + str);

		// Printing Integer
		System.out.println("Entered Integer : " + it);
	}
}
```

**Scanner**

这是BufferReader的高级版本，可以读取格式化输入，其针对于不同的数据格式有不同的读取函数

- 整型：nextInt()
- 浮点型：nextFloat()
- 字符型：next()或nextLine()

代码实例如下

```java
// Java Program to show how to take
// input from user using Scanner Class

import java.util.*;

class GFG {

	public static void main(String[] args)
	{
		// Scanner definition
		Scanner scn = new Scanner(System.in);

		// input is a string ( one word )
		// read by next() function
		String str1 = scn.next();

		// print String
		System.out.println("Entered String str1 : " + str1);

		// input is a String ( complete Sentence )
		// read by nextLine()function
		String str2 = scn.nextLine();

		// print string
		System.out.println("Entered String str2 : " + str2);

		// input is an Integer
		// read by nextInt() function
		int x = scn.nextInt();

		// print integer
		System.out.println("Entered Integer : " + x);

		// input is a floatingValue
		// read by nextFloat() function
		float f = scn.nextFloat();

		// print floating value
		System.out.println("Entered FloatValue : " + f);
	}
}
```

**BufferReader与Scanner的区别**

- BufferReader是读取字符流最基本的一种形式，它比BufferReader读取速度更快，因为Scanner在读取前做了很多预处理内容
- BufferReader更灵活，可以指定读取的字节数，通常BufferReader用于读取大量的数据
- BufferReader的同步性更好，更适合处理多线程问题
- Scanner的输入代码量和可读性方面更好

### 输出

Java中使用常用System.out.println()和System.out.print()输出用户想要输出的信息，该函数可以被分解为如下三个部分，如图所示

![img](https://media.geeksforgeeks.org/wp-content/uploads/20191126171503/println1.png)

其中println()和print()的区别如下:

- println()是同步方法，当传递多个线程时可能导致低性能问题
- println()是较高层次的IO函数，性能较低

## Java中的字符串——String

## Java中的数组——Array

Java数组的一些特性：

- Java中，数组是动态分配的
- 数组存储在一片连续的内存中
- 数组在java中作为对象存在，所以可以直接使用length属性返回数组长度
- 索引从0开始
- 数组长度必须指定为int或者short而不能式long
- 直接子类式Object
- 数组的长度不能被改变，但是引用可以指向其他数组
- 数组可以作为函数传入参数，也可以作为输出参数

![Arrays](https://media.geeksforgeeks.org/wp-content/uploads/Arrays1.png)

### 数组的声明，初始化，存取

**声明**

```java
type var-name[];
OR
type[] var-name;
```

**type:** 定义了数组中存储元素的类型，可以式原始数据类型，也可以是引用数据类型

**实例化**

当数组被声明时，只有数组的引用被创建，为了给数组分配内存，需要使用new关键字，如下：

```java
var-name = new type [size];
int[] intArray = new int[20]; // combining both statements in one
```

**存取**

```java
 // accessing the elements of the specified array
for (int i = 0; i < arr.length; i++)
  System.out.println("Element at index " + i + 
                                " : "+ arr[i]);
```

**对象数组**

声明一个Student对象数组，此时数组中每个元素存储的为对象的引用

```java
Student[] arr = new Student[5]; //student is a user-defined class
```

为对象数组分类内存

```java
// Java program to illustrate creating
// an array of objects

class Student {
	public int roll_no;
	public String name;
	Student(int roll_no, String name)
	{
		this.roll_no = roll_no;
		this.name = name;
	}
}

// Elements of the array are objects of a class Student.
public class GFG {
	public static void main(String[] args)
	{
		// declares an Array of integers.
		Student[] arr;

		// allocating memory for 5 objects of type Student.
		arr = new Student[5];

		// initialize the first elements of the array
		arr[0] = new Student(1, "aman");

		// initialize the second elements of the array
		arr[1] = new Student(2, "vaibhav");

		// so on...
		arr[2] = new Student(3, "shikar");
		arr[3] = new Student(4, "dharmesh");
		arr[4] = new Student(5, "mohit");

		// accessing the elements of the specified array
		for (int i = 0; i < arr.length; i++)
			System.out.println("Element at " + i + " : "
							+ arr[i].roll_no + " "
							+ arr[i].name);
	}
}
```

### 多维数组

**声明**

```java
// 声明语法：
// datatype [][] arrayrefvariable;
// datatype arrayrefvariable[][];
// 三维数组的声明
// int[][][] intArray = new int[10][20][10];
import java.io.*;
  
class GFG {
    public static void main (String[] args) {
      // Syntax 
       int [][] arr= new int[3][3];
      // 3 row and 3 column
    }
}
```

多维数组也叫数组的数组，在内存中的存储如下所示

![Blank Diagram - Page 1 (13)](https://media.geeksforgeeks.org/wp-content/cdn-uploads/Blank-Diagram-Page-1-13.jpeg)

**锯齿形数组(Jagged array)**

这是一个二维数组，只是每一维的数组长度都不是固定的，如下图

![img](https://media.geeksforgeeks.org/wp-content/uploads/20201202202711/Untitled4-660x306.png)

声明方法

结构与二维数组相同，不指定列数，在后续动态指定。下例展示了一个锯齿形创建，初始化和存取的实例

```java
// Another Java program to demonstrate 2-D jagged
// array such that first row has 1 element, second
// row has two elements and so on.
class Main {
	public static void main(String[] args)
	{
		int r = 5;

		// Declaring 2-D array with 5 rows
		int arr[][] = new int[r][];

		// Creating a 2D array such that first row
		// has 1 element, second row has two
		// elements and so on.
		for (int i = 0; i < arr.length; i++)
			arr[i] = new int[i + 1];

		// Initializing array
		int count = 0;
		for (int i = 0; i < arr.length; i++)
			for (int j = 0; j < arr[i].length; j++)
				arr[i][j] = count++;

		// Displaying the values of 2D Jagged array
		System.out.println("Contents of 2D Jagged Array");
		for (int i = 0; i < arr.length; i++) {
			for (int j = 0; j < arr[i].length; j++)
				System.out.print(arr[i][j] + " ");
			System.out.println();
		}
	}
}
```

结果如下

```mathematica
Contents of 2D Jagged Array
0 
1 2 
3 4 5 
6 7 8 9 
10 11 12 13 14 
```

锯齿形数组的一些优点

- 可以动态分类内存，使用起来更加灵活
- 空间利用率高
- 提高存取性能，锯齿形数组在内存中排列更加紧凑，存取性能比矩阵更高

### 数组的成员

- length：数组长度
- 所有的数组都继承自Object类，除了clone方法没有继承
- clone()方法重载了Object类

### 数组的拷贝

**一维数组的拷贝**

一维数组使用clone()拷贝时，进行的时深拷贝(deep copy)，不仅复制引用，还分配了新的内存，如下例：

```java
// Java program to demonstrate
// cloning of one-dimensional arrays

class Test {
	public static void main(String args[])
	{
		int intArray[] = { 1, 2, 3 };

		int cloneArray[] = intArray.clone();

		// will print false as deep copy is created
		// for one-dimensional array
		System.out.println(intArray == cloneArray);

		for (int i = 0; i < cloneArray.length; i++) {
			System.out.print(cloneArray[i] + " ");
		}
	}
}
```

```mathematica
// 输出
false
1 2 3 
```

![Blank Diagram - Page 1 (11)](https://media.geeksforgeeks.org/wp-content/cdn-uploads/Blank-Diagram-Page-1-11.jpeg)

**多维数组的拷贝**

多维数组的拷贝是浅拷贝(shallow copy)，只为每个数组创建了数组的索引，子数组任然共享内存，如下例

```java
// Java program to demonstrate
// cloning of multi-dimensional arrays

class Test {
	public static void main(String args[])
	{
		int intArray[][] = { { 1, 2, 3 }, { 4, 5 } };

		int cloneArray[][] = intArray.clone();

		// will print false
		System.out.println(intArray == cloneArray);

		// will print true as shallow copy is created
		// i.e. sub-arrays are shared
		System.out.println(intArray[0] == cloneArray[0]);
		System.out.println(intArray[1] == cloneArray[1]);
	}
}
```

```mathematica
\\ 输出
false
true
true
```

![Blank Diagram - Page 1 (12)](https://media.geeksforgeeks.org/wp-content/cdn-uploads/Blank-Diagram-Page-1-12.jpeg)

### Arrays类

`java.util`包中的Arrays数组是Java Collection框架中的一部分，该类提供了一些静态方法动态的创建和存储java数组。该类由一些静态方法和一些Object类中的方法构成，并且类中的方法全为静态的。

**Arrays类中的一些方法**

| Methods                                                      | Action Performed                                             |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| asList()                                                     | Returns a fixed-size list backed by the specified Arrays     |
| [fill(originalArray, fillValue)](https://www.geeksforgeeks.org/array-class-in-java/) | Assigns this fill value to each index of this arrays.        |
| binarySearch()                                               | Searches for the specified element in the array with the help of the Binary Search Algorithm |
| binarySearch(array, fromIndex, toIndex, key, Comparator)     | Searches a range of the specified array for the specified object using the Binary Search Algorithm |
| [sort(T[] a, Comparator< super T> c)](https://www.geeksforgeeks.org/array-class-in-java/) | Sorts the specified array of objects according to the order induced by the specified comparator. |

**排序和二分示例**

```java
// Java Program to Demonstrate Arrays Class
// Via binarySearch() method

// Importing Arrays utility class
// from java.util package
import java.util.Arrays;

// Main class
public class GFG {

	// Main driver method
	public static void main(String[] args)
	{

		// Get the Array
		int intArr[] = { 10, 20, 15, 22, 35 };

		Arrays.sort(intArr);

		int intKey = 22;

		// Print the key and corresponding index
		System.out.println(
			intKey + " found at index = "
			+ Arrays.binarySearch(intArr, intKey));
	}
}
```



## Java文件操作

### File类

File类在java实现了文件和目录名。File包含了诸多操作文件和目录的方法，其中包括删除，重命名，创建目录，列出包含的子目录以及一些文件和目录相关的属性等等。

- File是文件和目录的抽象表示
- 路径名即可以是相对路径，也可以是绝对路径，父目录可以通过`getParent()`方法获得
- 首先我们需要传递目录名和文件名来创建一个文件类，文件系统还实现了在真实系统中对于文件的一些存取权限，例如读、写、执行等等
- File类的实例时固定的，文件引用一旦实例化，将不可改变

**创建一个文件对象**

```java
File a = new File("/usr/local/bin/geeks");
```

**其他的构造函数**

```java
File(File parent,String child);// 提供父目录对象，和子文件名
File(String pathname);// 提供路径名
File(String parent,String child);// 提供父目录名
File(URL url);// 提供一个url
```

**File类的一些方法**

| 方法                                                         | 描述                                                         | 返回值   |
| :----------------------------------------------------------- | ------------------------------------------------------------ | -------- |
| [**canExecute()**](https://www.geeksforgeeks.org/file-canexecute-method-in-java-with-examples/) | Tests whether the application can execute the file denoted by this abstract pathname. | boolean  |
| [**canRead()**](https://www.geeksforgeeks.org/file-canread-method-in-java-with-examples/) | Tests whether the application can read the file denoted by this abstract pathname. | boolean  |
| [**canWrite()**](https://www.geeksforgeeks.org/file-canwrite-method-in-java-with-examples/) | Tests whether the application can modify the file denoted by this abstract pathname. | boolean  |
| **compareTo(File pathname)**                                 | Compares two abstract pathnames lexicographically.           | int      |
| [**createNewFile()**](https://www.geeksforgeeks.org/file-createnewfile-method-in-java-with-examples/) | Atomically creates a new, empty file named by this abstract pathname. | boolean  |
| [**createTempFile(String prefix, String suffix)**](https://www.geeksforgeeks.org/file-createtempfile-method-in-java-with-examples/) | Creates an empty file in the default temporary-file directory. | File     |
| [**delete()**](https://www.geeksforgeeks.org/files-delete-method-in-java-with-examples/) | Deletes the file or directory denoted by this abstract pathname. | boolean  |
| **equals(Object obj)**                                       | Tests this abstract pathname for equality with the given object. | boolean  |
| [**exists()**](https://www.geeksforgeeks.org/file-exists-method-in-java-with-examples/) | Tests whether the file or directory denoted by this abstract pathname exists. | boolean  |
| [**getAbsolutePath()**](https://www.geeksforgeeks.org/file-getabsolutepath-method-in-java-with-examples/) | Returns the absolute pathname string of this abstract pathname. | String   |
| [**list()**](https://www.geeksforgeeks.org/file-list-method-in-java-with-examples/) | Returns an array of strings naming the files and directories in the directory. | String[] |
| [**getFreeSpace()**](https://www.geeksforgeeks.org/file-getfreespace-method-in-java-with-examples/) | Returns the number of unallocated bytes in the partition.    | long     |
| [**getName()**](https://www.geeksforgeeks.org/file-getname-method-in-java-with-examples/) | Returns the name of the file or directory denoted by this abstract pathname. | String   |
| [**getParent()**](https://www.geeksforgeeks.org/file-getparent-method-in-java-with-examples/) | Returns the pathname string of this abstract pathname’s parent. | String   |
| [**getParentFile()**](https://www.geeksforgeeks.org/file-getparentfile-method-in-java-with-examples/) | Returns the abstract pathname of this abstract pathname’s parent. | File     |
| [**getPath()**](https://www.geeksforgeeks.org/file-getpath-method-in-java-with-examples/) | Converts this abstract pathname into a pathname string.      | String   |
| [**setReadOnly()**](https://www.geeksforgeeks.org/file-setreadonly-method-in-java-with-examples/) | Marks the file or directory named so that only read operations are allowed. | boolean  |
| [**isDirectory()**](https://www.geeksforgeeks.org/file-isdirectory-method-in-java-with-examples/) | Tests whether the file denoted by this pathname is a directory. | boolean  |
| [**isFile()**](https://www.geeksforgeeks.org/file-isfile-method-in-java-with-examples/) | Tests whether the file denoted by this abstract pathname is a normal file. | boolean  |
| [**isHidden()**](https://www.geeksforgeeks.org/file-ishidden-method-in-java-with-examples/) | Tests whether the file named by this abstract pathname is a hidden file. | boolean  |
| [**length()**](https://www.geeksforgeeks.org/file-length-method-in-java-with-examples/) | Returns the length of the file denoted by this abstract pathname. | long     |
| [**listFiles()**](https://www.geeksforgeeks.org/file-listfiles-method-in-java-with-examples/) | Returns an array of abstract pathnames denoting the files in the directory. | File[]   |
| [**mkdir()**](https://www.geeksforgeeks.org/file-mkdir-method-in-java-with-examples/) | Creates the directory named by this abstract pathname.       | boolean  |
| [**renameTo(File dest)**](https://www.geeksforgeeks.org/file-renameto-method-in-java-with-examples/) | Renames the file denoted by this abstract pathname.          | boolean  |
| [**setExecutable(boolean executable)**](https://www.geeksforgeeks.org/file-setexecutable-method-in-java-with-examples/) | A convenience method to set the owner’s execute permission.  | boolean  |
| [**setReadable(boolean readable)**](https://www.geeksforgeeks.org/file-setreadable-function-in-java-with-examples/) | A convenience method to set the owner’s read permission.     | boolean  |
| [**setReadable(boolean readable, boolean ownerOnly)**](https://www.geeksforgeeks.org/file-setreadable-function-in-java-with-examples/) | Sets the owner’s or everybody’s read permission.             | boolean  |
| [**setWritable(boolean writable)**](https://www.geeksforgeeks.org/file-setwritable-method-in-java-with-examples/) | A convenience method to set the owner’s write permission.    | boolean  |
| **toString()**                                               | Returns the pathname string of this abstract pathname.       | String   |
| **toURI()**                                                  | Constructs a file URI that represents this abstract pathname. | URI      |

下面的实例展示了检查文件或目录是否存在

```java
// In this Java program, we accepts a file or directory name from
// command line arguments. Then the program will check if
// that file or directory physically exist or not and
// it displays the property of that file or directory.

import java.io.File;

// Displaying file property
class fileProperty {
	public static void main(String[] args)
	{

		// accept file name or directory name through
		// command line args
		String fname = args[0];

		// pass the filename or directory name to File
		// object
		File f = new File(fname);

		// apply File class methods on File object
		System.out.println("File name :" + f.getName());
		System.out.println("Path: " + f.getPath());
		System.out.println("Absolute path:"
						+ f.getAbsolutePath());
		System.out.println("Parent:" + f.getParent());
		System.out.println("Exists :" + f.exists());

		if (f.exists()) {
			System.out.println("Is writable:"
							+ f.canWrite());
			System.out.println("Is readable" + f.canRead());
			System.out.println("Is a directory:"
							+ f.isDirectory());
			System.out.println("File Size in bytes "
							+ f.length());
		}
	}
}
```

### 写文件操作

**FileWrite:** 创建一个文件，并向内写入字符

- 继承自`OutputStream`类
- 此构造函数假定默认字符编码和默认字节缓冲区大小是可以接受的
- 该类以字符流的方式写入数据
- 若文件不存在则创建一个新文件

FileWrite的一些构造函数如下：

- **FileWriter(File file)**
- **FileWriter (File file, boolean append)**
- **FileWriter (FileDescriptor fd)** 
- **FileWriter (String fileName)**
- **FileWriter (String fileName, Boolean append)**

该类提供的一些方法如下：

- **public void write (int c) throws IOException**：写入一个字符
- **public void write (char [] stir) throws IOException**：写入一个字符数组
- **public void write(String str)throws IOException**：写入一个字符串数据
- **public void write(String str,** **int off,** **int len)throws IOException**：从str的off位置开始，写入len长度的字符 
- **public void flush() throws IOException**：清空写入流
- **public void close() throws IOException**：清空写入流，并关闭文件

使用示例如下：

```java
// Creating a text File using FileWriter
import java.io.FileWriter;
import java.io.IOException;
class CreateFile
{
	public static void main(String[] args) throws IOException
	{
		// Accept a string
		String str = "File Handling in Java using "+
				" FileWriter and FileReader";

		// attach a file to FileWriter
		FileWriter fw=new FileWriter("output.txt");

		// read character wise from string and write
		// into FileWriter
		for (int i = 0; i < str.length(); i++)
			fw.write(str.charAt(i));

		System.out.println("Writing successful");
		//close the file
		fw.close();
	}
}
```

### 读文件操作

**FileReader:** 用于从文件中读取数据，

- 继承自`InputStreamReader`类
- 此构造函数假定默认字符编码和默认字节缓冲区大小是可以接受的
- 以字符流的方式从文件中读取数据

该类的一些构造函数如下：

- **FileReader(File file)**
- **FileReader(FileDescripter fd)**
- **FileReader(String fileName)**

该类的一些方法如下：

- **public int read () throws IOException**：读取一个字符
- **public int read(char[] cbuff) throws IOException**：将字符读入到array
- **public abstract int read(char[] buff, int off, int len) throws IOException**
- **public void close() throws IOException**：关闭文件
- **public long skip(long n) throws IOException**

示例如下：

```java
// Reading data from a file using FileReader
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;
class ReadFile
{
	public static void main(String[] args) throws IOException
	{
		// variable declaration
		int ch;

		// check if File exists or not
		FileReader fr=null;
		try
		{
			fr = new FileReader("text");
		}
		catch (FileNotFoundException fe)
		{
			System.out.println("File not found");
		}

		// read from FileReader till the end of file
		while ((ch=fr.read())!=-1)
			System.out.print((char)ch);

		// close the file
		fr.close();
	}
}
```

**Scanner:**

使用文件对象构造一个Scanner对象，即可类似从标准输入读数据的方式从文件对象中读取数据

示例如下：

```java
// Java Program to illustrate
// reading from Text File
// using Scanner Class
import java.io.File;
import java.util.Scanner;
public class ReadFromFileUsingScanner
{
    public static void main(String[] args) throws Exception
    {
        // pass the path to the file as a parameter
        File file = new File("C:\\Users\\pankaj\\Desktop\\test.txt");
        Scanner sc = new Scanner(file);

        while (sc.hasNextLine())
        System.out.println(sc.nextLine());
    }
}
```

## Java集合类(Collection)

在java中任何一组单独的对象称为对象的集合，集合接口(**java.util.Collection**)和Map接口(**java.util.Map**)是java集合两个主要的"根"接口。

所谓的框架(framework)就是提供一组现成体系结构的类和接口，其设计目的是为了方便不同的类执行相同类型的任务具有相同的接口。

**集合框架的一些优点：**

- 不同集合具有一致的API
- 减少编程难度
- 提高编程质量和效率

### 集合框架的层次结构图

![Hierarchy of the Collection Framework](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20220526152255/Collections-in-Java1.png)

**集合的一些公共方法**

| Method                                                       | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [**add(Object)**](https://www.geeksforgeeks.org/collection-add-method-in-java-with-examples/) | This method is used to add an object to the collection.      |
| [**addAll(Collection c)**](https://www.geeksforgeeks.org/collections-addall-method-in-java-with-examples/) | This method adds all the elements in the given collection to this collection. |
| [**clear()**](https://www.geeksforgeeks.org/collection-clear-method-in-java-with-examples/) | This method removes all of the elements from this collection. |
| [**contains(Object o)**](https://www.geeksforgeeks.org/collection-contains-method-in-java-with-examples/) | This method returns true if the collection contains the specified element. |
| **containsAll(Collection c)**                                | This method returns true if the collection contains all of the elements in the given collection. |
| **equals(Object o)**                                         | This method compares the specified object with this collection for equality. |
| **hashCode()**                                               | This method is used to return the hash code value for this collection. |
| [**isEmpty()**](https://www.geeksforgeeks.org/collection-isempty-method-in-java-with-examples/) | This method returns true if this collection contains no elements. |
| **iterator()**                                               | This method returns an iterator over the elements in this collection. |
| [**max()**](https://www.geeksforgeeks.org/collections-max-method-in-java-with-examples/) | This method is used to return the maximum value present in the collection. |
| **parallelStream()**                                         | This method returns a parallel Stream with this collection as its source. |
| **remove(Object o)**                                         | This method is used to remove the given object from the collection. If there are duplicate values, then this method removes the first occurrence of the object. |
| **removeAll(Collection c)**                                  | This method is used to remove all the objects mentioned in the given collection from the collection. |
| **removeIf(Predicate filter)**                               | This method is used to remove all the elements of this collection that satisfy the given [predicate](https://www.geeksforgeeks.org/mathematic-logic-predicates-quantifiers/). |
| **retainAll(Collection c)**                                  | This method is used to retain only the elements in this collection that are contained in the specified collection. |
| **size()**                                                   | This method is used to return the number of elements in the collection. |
| **spliterator()**                                            | This method is used to create a [Spliterator](https://www.geeksforgeeks.org/java-program-to-convert-iterator-to-spliterator/) over the elements in this collection. |
| **stream()**                                                 | This method is used to return a sequential Stream with this collection as its source. |
| **toArray()**                                                | This method is used to return an array containing all of the elements in this collection. |

### 集合中的一些接口

**迭代器(Iterable)接口：** 集合框架的根节点，collection接口扩展了该接口，所有的集合类和接口都实现了该接口。该接口的主要功能是给每一个集合提供一个迭代器。

**集合(collection)接口：** 这个接口扩展了迭代器接口，并且由所有的集合类实现。这个接口包含了集合类的一些常用方法，例如`add,remove,size`等。

**链表(List)接口：** 这是集合接口的子接口，这个接口声明了一种列表类型的数据，可以用来存储有序的对象集合，该接口被一些具体的类实现，例如`ArrayList,Vector,stack`等，由于所有的子类实现了链表，所有可以引用这些类的任何一个实例来实例化链表对象。

### ArrayList

Java中的动态数组，可动态改变数组的长度

**ArrayList的一些特点**

- 比标准数组的速度慢，同样支持随机存储
- 使用起来比标准数组更方便，灵活
- 不支持原始数据类型，因此需要使用Wrapper类将原始数据类型转换为引用数据类型
- 初始化不需要指定数组长度
- 不是线程同步的，Vector是线程同步的
- 类似与cpp中的vector

**ArrayList的一些要点**

- 支持重复元素存储
- 支持有序的插入
- 允许异构对象
- 允许插入空元素

**类层次图**

![ArrayList in Java](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20200624184403/ArrayList.png)

**存储实例**

![ArrayList in Java](https://media.geeksforgeeks.org/wp-content/uploads/20210908120146/ArrayListIntegerObjecttype-660x268.png)

**解释：ArrayList是如何实现动态特性的**

当数组满时，从堆内存中创建一个更大的内存，将当前内存元素复制到新的内存空间，将新加入的元素加入到更大的数组中，销毁原来的内存空间

**ArratList构造函数**

- ArrayList()
- ArrayList(Collection c)
- ArrayList(int capacity)

**ArrayList的一些方法**

| Method                                                       | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [add(int index, Object element)](https://www.geeksforgeeks.org/java-util-arraylist-add-method-java/) | This method is used to insert a specific element at a specific position index in a list. |
| [add(Object o)](https://www.geeksforgeeks.org/java-util-arraylist-add-method-java/) | This method is used to append a specific element to the end of a list. |
| [addAll(Collection C)](https://www.geeksforgeeks.org/java-util-arraylist-addall-method-java/) | This method is used to append all the elements from a specific collection to the end of the mentioned list, in such an order that the values are returned by the specified collection’s iterator. |
| [addAll(int index, Collection C)](https://www.geeksforgeeks.org/java-util-arraylist-addall-method-java/) | Used to insert all of the elements starting at the specified position from a specific collection into the mentioned list. |
| [clone()](https://www.geeksforgeeks.org/clone-method-in-java-2/) | This method is used to return a shallow copy of an ArrayList. |
| [contains(Object o)](https://www.geeksforgeeks.org/arraylist-contains-java/) | Returns true if this list contains the specified element.    |
| [forEach(Consumer action)](https://www.geeksforgeeks.org/arraylist-foreach-method-in-java/) | Performs the given action for each element of the Iterable until all elements have been processed or the action throws an exception. |
| [get(int index)](https://www.geeksforgeeks.org/arraylist-get-method-java-examples/) | Returns the element at the specified position in this list.  |
| [indexOf(Object O)](https://www.geeksforgeeks.org/java-util-arraylist-indexof-java/) | The index the first occurrence of a specific element is either returned, or -1 in case the element is not in the list. |
| [isEmpty()](https://www.geeksforgeeks.org/arraylist-isempty-java-example/) | Returns true if this list contains no elements.              |
| [toArray()](https://www.geeksforgeeks.org/arraylist-array-conversion-java-toarray-methods/) | This method is used to return an array containing all of the elements in the list in the correct order. |
| [toArrayObject(O)](https://www.geeksforgeeks.org/arraylist-array-conversion-java-toarray-methods/) | It is also used to return an array containing all of the elements in this list in the correct order same as the previous method. |
| [trimToSize()](https://www.geeksforgeeks.org/arraylist-trimtosize-java-example/) | This method is used to trim the capacity of the instance of the ArrayList to the list’s current size. |

**使用动态二维ArrayList**

```java
//        声明一个动态二维ArrayList
ArrayList<ArrayList<Integer>> nums = new ArrayList<>(5);
//        定义行数和列数
int row = 5;
int col = 5;
//        初始化nums
for (int i = 0; i < row; i++) {
    ArrayList<Integer> list = new ArrayList<>();
    nums.add(list);
    for (int j = 0; j < col; j++)
        nums.get(i).add(j + 10);
}
//        打印二维ArrayList
for (int i = 0; i < nums.size(); i++) {
    System.out.println(nums.get(i));
}
```

**使用size创建和访问ArrayList实例**

```java
// Java program to demonstrate the
// working of ArrayList in Java

import java.io.*;
import java.util.*;

class ArrayListExample {
	public static void main(String[] args)
	{
		// Size of the
		// ArrayList
		int n = 5;

		// Declaring the ArrayList with
		// initial size n
		ArrayList<Integer> arrli
			= new ArrayList<Integer>(n);

		// Appending new elements at
		// the end of the list
		for (int i = 1; i <= n; i++)
			arrli.add(i);

		// Printing elements
		System.out.println(arrli);

		// Remove element at index 3
		arrli.remove(3);

		// Displaying the ArrayList
		// after deletion
		System.out.println(arrli);

		// Printing elements one by one
		for (int i = 0; i < arrli.size(); i++)
			System.out.print(arrli.get(i) + " ");
	}
}
```

**使用迭代器迭代元素**

```java
// Java program to Iterate the elements
// in an ArrayList

// Importing all utility classes
import java.util.*;

// Main class
class GFG {

	// Main driver method
	public static void main(String args[])
	{
		// Creating an Arraylist of string type
		ArrayList<String> al = new ArrayList<>();

		// Adding elements to ArrayList
		// using standard add() method
		al.add("Geeks");
		al.add("Geeks");
		al.add(1, "For");

		// Using the Get method and the
		// for loop
		for (int i = 0; i < al.size(); i++) {

			System.out.print(al.get(i) + " ");
		}

		System.out.println();

		// Using the for each loop
		for (String str : al)
			System.out.print(str + " ");
	}
}
```

**在两数之间添加元素**

```java
import java.io.*;
import java.util.*;
class GFG {
	public static void main(String[] args)
	{
		ArrayList<Integer> list = new ArrayList();
		list.add(1);
		list.add(2);
		list.add(4);
		System.out.println(list);
		// insert missing element 3
		list.add(2, 3);
		System.out.println(list);
	}
}
```

**元素排序**

```java
import java.io.*;
import java.util.*;

class GFG {
	public static void main(String[] args)
	{
		ArrayList<Integer> list = new ArrayList();
		list.add(2);
		list.add(4);
		list.add(3);
		list.add(1);
		System.out.println("Before sorting list:");
		System.out.println(list);
		Collections.sort(list);
		System.out.println("after sorting list:");
		System.out.println(list);
	}
}
```

### Vector

与`ArrayList`大致相同，主要区别在于Vector是线程同步的

### Stack

提供了一种栈数据结构，除了push和pop基础操作外，该类还提供了其他三种函数，empty,search,peek，Stack类扩展了Vector类，是Vector的子类，Stack的层次结构图如下：

![Stack Class in Java](https://media.geeksforgeeks.org/wp-content/uploads/Selection_028.png)

**构造一个栈**

```java
Stack<E> stack = new Stack<E>();
```

**Stack的一些方法**

| METHOD                                                       | DESCRIPTION                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [empty()](https://www.geeksforgeeks.org/stack-empty-method-in-java/) | It returns true if nothing is on the top of the stack. Else, returns false. |
| [peek()](https://www.geeksforgeeks.org/stack-peek-method-in-java/) | Returns the element on the top of the stack, but does not remove it. |
| [pop()](https://www.geeksforgeeks.org/stack-pop-method-in-java/) | Removes and returns the top element of the stack. An ‘EmptyStackException’ An exception is thrown if we call pop() when the invoking stack is empty. |
| [push(Object element)](https://www.geeksforgeeks.org/stack-push-method-in-java/) | Pushes an element on the top of the stack.                   |
| [search(Object element)](https://www.geeksforgeeks.org/stack-search-method-in-java/) | It determines whether an object exists in the stack. If the element is found,It returns the position of the element from the top of the stack. Else, it returns -1. |

**使用ArrayList代替Stack**

java中更推荐使用ArrayDeque作为Stack的实现，因为ArrayDeque具有更好的性能，实例如下：

```java
// A Java Program to show implementation
// of Stack using ArrayDeque

import java.util.*;

class GFG {
	public static void main (String[] args) {
		Deque<Character> stack = new ArrayDeque<Character>();
		stack.push('A');
		stack.push('B');
		System.out.println(stack.peek());
		System.out.println(stack.pop());
	}
}

```

### LinkedList

该类实现的链表数据结构，这是一个线性数据结构，每个元素之间的存储时不连续的，并且每个元素存储数据和地址部分，元素与元素之间由指针和地址链接，每个元素称之为节点(node)

由于链表的动态性，相对于数组其更容易删除和插入，但链表不支持随机访问

**LinkedList构造函数**

- **LinkedList()**：创建一个空链表
-  **LinkedList(Collection C)**：从集合中船舰一个链表

**LinkedList中的一些常用方法**

| Method                                                       | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [addFirst(E e)](https://www.geeksforgeeks.org/linkedlist-addfirst-method-in-java/) | This method Inserts the specified element at the beginning of this list. |
| [addLast(E e)](https://www.geeksforgeeks.org/linkedlist-addlast-method-in-java/) | This method Appends the specified element to the end of this list. |
| [getFirst()](https://www.geeksforgeeks.org/java-util-linkedlist-get-getfirst-getlast-java/) | This method returns the first element in this list.          |
| [getLast()](https://www.geeksforgeeks.org/linkedlist-getlast-method-in-java/) | This method returns the last element in this list.           |
| [offer(E e)](https://www.geeksforgeeks.org/java-util-linkedlist-offer-offerfirst-offerlast-java/) | This method Adds the specified element as the tail (last element) of this list. |
| [offerFirst(E e)](https://www.geeksforgeeks.org/java-util-linkedlist-offer-offerfirst-offerlast-java/) | This method Inserts the specified element at the front of this list. |
| [offerLast(E e)](https://www.geeksforgeeks.org/java-util-linkedlist-offer-offerfirst-offerlast-java/) | This method Inserts the specified element at the end of this list. |
| [peek()](https://www.geeksforgeeks.org/java-util-linkedlist-peek-peekfirst-peeklast-java/) | This method retrieves but does not remove, the head (first element) of this list. |
| [peekFirst()](https://www.geeksforgeeks.org/java-util-linkedlist-peek-peekfirst-peeklast-java/) | This method retrieves, but does not remove, the first element of this list, or returns null if this list is empty. |
| [peekLast()](https://www.geeksforgeeks.org/java-util-linkedlist-peek-peekfirst-peeklast-java/) | This method retrieves, but does not remove, the last element of this list, or returns null if this list is empty. |
| [poll()](https://www.geeksforgeeks.org/java-util-linkedlist-poll-pollfirst-polllast-examples-java/) | This method retrieves and removes the head (first element) of this list. |
| [pollFirst()](https://www.geeksforgeeks.org/java-util-linkedlist-poll-pollfirst-polllast-examples-java/) | This method retrieves and removes the first element of this list, or returns null if this list is empty. |
| [pollLast()](https://www.geeksforgeeks.org/java-util-linkedlist-poll-pollfirst-polllast-examples-java/) | This method retrieves and removes the last element of this list, or returns null if this list is empty. |
| [pop()](https://www.geeksforgeeks.org/linkedlist-pop-method-in-java/) | This method Pops an element from the stack represented by this list. |
| [push(E e)](https://www.geeksforgeeks.org/linkedlist-push-method-in-java/) | This method pushes an element onto the stack represented by this list. |

**实例**

```java
// Java Program to Demonstrate
// Implementation of LinkedList
// class

// Importing required classes
import java.util.*;

// Main class
public class GFG {

	// Driver code
	public static void main(String args[])
	{
		// Creating object of the
		// class linked list
		LinkedList<String> ll = new LinkedList<String>();

		// Adding elements to the linked list
		ll.add("A");
		ll.add("B");
		ll.addLast("C");
		ll.addFirst("D");
		ll.add(2, "E");

		System.out.println(ll);

		ll.remove("B");
		ll.remove(3);
		ll.removeFirst();
		ll.removeLast();

		System.out.println(ll);
	}
}
```

Queue是一个接口，实现了先入先出的一种顺序，其被PriorityQueue和ArrayDeque

实现，在java中没有单独提供队列类，想要使用queue类时可以使用优先队列或者双端队列代替，下面详细介绍PriorityQueue和ArrayDeque

### PriorityQueue

优先队列除了具有队列的性质外，还为每一元素定义了优先级，优先级大的位于队头，默认情况下，元素优先级由常规优先顺序定义，若用户需要自定义优先级，可实例化`Comparator`，内部由堆实现，优先队列类结构图如下

![Queue-Deque-PriorityQueue-In-Java](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20200903183026/Queue-Deque-PriorityQueue-In-Java.png)

**优先队列的构造函数**

- **PriorityQueue()**
- **PriorityQueue(Collection<E> c)**
- **PriorityQueue(int initialCapacity)**
- **PriorityQueue(int initialCapacity, Comparator<E> comparator)**：定义一个指定比较器的优先队列
- **PriorityQueue(PriorityQueue<E> c)**
- **PriorityQueue(SortedSet<E> c)**

**优先队列常用的方法**

| Method                                                       | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [boolean add(E element)](https://www.geeksforgeeks.org/priorityqueue-add-method-in-java/) | This method inserts the specified element into this priority queue. |
| [public peek()](https://www.geeksforgeeks.org/queue-peek-method-in-java/) | This method retrieves, but does not remove, the head of this queue, or returns null if this queue is empty. |
| [public poll()](https://www.geeksforgeeks.org/queue-poll-method-in-java/) | This method retrieves and removes the head of this queue, or returns null if this queue is empty. |

**实例**

```java
import java.util.PriorityQueue;

public class PriorityQueueExample {

	public static void main(String[] args) {
		
		// Create a priority queue with initial capacity 10
		PriorityQueue<Integer> pq = new PriorityQueue<>(10);
		
		// Add elements to the queue
		pq.add(3);
		pq.add(1);
		pq.add(2);
		pq.add(5);
		pq.add(4);
		
		// Print the queue
		System.out.println("Priority queue: " + pq);
		
		// Peek at the top element of the queue
		System.out.println("Peek: " + pq.peek());
		
		// Remove the top element of the queue
		pq.poll();
		
		// Print the queue again
		System.out.println("Priority queue after removing top element: " + pq);
		
		// Check if the queue contains a specific element
		System.out.println("Does the queue contain 3? " + pq.contains(3));
		
		// Get the size of the queue
		System.out.println("Size of queue: " + pq.size());
		
		// Remove all elements from the queue
		pq.clear();
		
		// Check if the queue is empty
		System.out.println("Is the queue empty? " + pq.isEmpty());
	}
}
```

**优先队列的一些实际应用**

- 任务调度
- 急症室
- 网络路由
- 运输
- 作业调度
- 在线市场

### ArrayDeque

ArrayDeque应用可变长数组实现了Deque接口，该类提供了数组的双端操作，也就是所谓的双端队列，既可以当作栈使用也可以当作数组使用，在性能上比Stack效率更高。

**ArrayDeque的一些优点**

- 高性能，该类对于从两端插入元素和删除元素提供了常量时间性能的操作
- 长度可变，该类的长度是可以随着元素的操作而改变的
- 轻量的，该类是一种轻量型数据结构，不需要额外的开销，例如链表
- 线程安全，该类不是线程安全的，但是可以使用`Collections.synchronizedDeque`方法创建一个线程安全版本的类

**ArrayDeque的一些缺点**

- 不支持同步，该类是不支持线程同步的，即多个线程可同时访问该类中的数据，这就造成了潜在的数据损坏的可能
- 该类的容量是有限的

**ArrayDeque类层次图**

![ArrayDeque in Java](https://media.geeksforgeeks.org/wp-content/uploads/20200909140302/ArrayDequeinJava.png)

**构造函数**

- **ArrayDeque()**
- **ArrayDeque(Collection<? extends E> c)**
- **ArrayDeque(int numofElements)**

**ArrayDeque中的一些方法**

| METHOD                                                       | DESCRIPTION                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [addFirst(Element e)](https://www.geeksforgeeks.org/arraydeque-addfirst-method-in-java/) | The method inserts particular element at the start of the deque. |
| [addLast(Element e) ](https://www.geeksforgeeks.org/arraydeque-addlast-method-in-java/) | The method inserts a particular element at the end of the deque. It is similar to the add() method |
| [getFirst()](https://www.geeksforgeeks.org/arraydeque-getfirst-method-in-java/) | The method returns first element of the deque                |
| [getLast()](https://www.geeksforgeeks.org/arraydeque-getlast-method-in-java/) | The method returns last element of the deque                 |
| [offer(Element e)](https://www.geeksforgeeks.org/arraydeque-offer-method-in-java/) | The method inserts element at the end of deque.              |
| [offerFirst(Element e) ](https://www.geeksforgeeks.org/arraydeque-offerfirst-method-in-java/) | The method inserts element at the front of deque.            |
| [offerLast(Element e)](https://www.geeksforgeeks.org/arraydeque-offerlast-method-in-java/) | The method inserts element at the end of the deque.          |
| [peek()](https://www.geeksforgeeks.org/arraydeque-peek-method-in-java/) | The method returns head element without removing it.         |
| [poll()](https://www.geeksforgeeks.org/arraydeque-poll-method-in-java/) | The method returns head element and also removes it          |
| [pop()](https://www.geeksforgeeks.org/arraydeque-pop-method-in-java/) | The method pops out an element for stack represented by deque |
| [push(Element e)](https://www.geeksforgeeks.org/arraydeque-push-method-in-java/) | The method pushes an element onto stack represented by deque |

### HashMap

该类存在于`java.util`，其实现了Map接口，在内存中以(key,value)的方式存储数据，如果插入重复的键，则会替换相应的键对应的值。与HashTable的不同在于，HashTbale支持同步而HashMap不支持同步。

**HashMap层次结构图**

![Hierarchy of HashMap in Java](https://media.geeksforgeeks.org/wp-content/uploads/20201119122201/HashMapinJava.png)

**HashMap的一些优点**

- 快速的存储，提供常量的时间复杂度检索和插入元素
- 支持空键和空值
- HashMap是无序的
- 允许值的重复而不允许键的重复

**构造函数**

- HashMap()
- HashMap(int initialCapacity)
- HashMap(int initialCapacity, float loadFactor)
- HashMap(Map map)

构造一个HashMap实例

```java
HashMap<Integer, ArrayList<Integer>> map = new HashMap<Integer, ArrayList<Integer>>();
```

**常用的一些方法**

| Method                                                       | Descripition                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [containsKey(Object key)](https://www.geeksforgeeks.org/hashmap-containskey-method-in-java/) | Returns true if this map contains a mapping for the specified key. |
| [containsValue(Object value)](https://www.geeksforgeeks.org/hashmap-containsvalue-method-in-java/) | Returns true if this map maps one or more keys to the specified value. |
| [get(Object key)](https://www.geeksforgeeks.org/hashmap-get-method-in-java/) | Returns the value to which the specified key is mapped, or null if this map contains no mapping for the key. |
| [put(K key, V value)](https://www.geeksforgeeks.org/hashmap-put-method-in-java/) | Associates the specified value with the specified key in this map. |
| [values()](https://www.geeksforgeeks.org/hashmap-values-method-in-java/) | Returns a Collection view of the values contained in this map. |

### HashSet

### Java中的Collections类

Collections是Java集合框架中的通用类，位于`java.util`包中，该类中使用静态方法操作和返回集合，所有的方法抛出`NullPointerException`若操作的集合为空的话

**Collections中的一些方法**

| **Methods**                                                  | **Description**                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [binarySearch(List list, T key)](https://www.google.com/url?client=internal-element-cse&cx=009682134359037907028:tj6eafkv_be&q=https://www.geeksforgeeks.org/collections-binarysearch-java-examples/&sa=U&ved=2ahUKEwi6uP_199nsAhXj73MBHZbDDPMQFjAJegQIBRAC&usg=AOvVaw3Z6NwOyP0de-c-hRasRUsf) | This method searches the key using binary search in the specified list. |
| [binarySearch(List list, T key, Comparator c)](https://www.google.com/url?client=internal-element-cse&cx=009682134359037907028:tj6eafkv_be&q=https://www.geeksforgeeks.org/collections-binarysearch-java-examples/&sa=U&ved=2ahUKEwi6uP_199nsAhXj73MBHZbDDPMQFjAJegQIBRAC&usg=AOvVaw3Z6NwOyP0de-c-hRasRUsf) | This method searches the specified list for the specified object using the binary search algorithm. |
| [enumeration(Collection c)](https://www.google.com/url?client=internal-element-cse&cx=009682134359037907028:tj6eafkv_be&q=https://www.geeksforgeeks.org/collections-enumeration-method-in-java-with-examples/&sa=U&ved=2ahUKEwjKuPOa-NnsAhWF6XMBHV52Bxg4ChAWMAl6BAgAEAI&usg=AOvVaw2zQdzpk5s0qYfnqwiTKmSC) | This method returns an enumeration over the specified collection. |
| [fill(List list, T obj)](https://www.google.com/url?client=internal-element-cse&cx=009682134359037907028:tj6eafkv_be&q=https://www.geeksforgeeks.org/collections-fill-method-in-java-with-examples/&sa=U&ved=2ahUKEwi2_5_3-NnsAhWCheYKHZBvD4E4MhAWMAZ6BAgGEAI&usg=AOvVaw1xqIqDpotyXSl0SNNWLwsG) | This method replaces all of the elements of the specified list with the specified element. |
| [sort(List list)](https://www.google.com/url?client=internal-element-cse&cx=009682134359037907028:tj6eafkv_be&q=https://www.geeksforgeeks.org/collections-sort-java-examples/&sa=U&ved=2ahUKEwi6uP_199nsAhXj73MBHZbDDPMQFjADegQIBxAC&usg=AOvVaw3LK6ysEznNr0ARFYCFDvYh) | This method sorts the specified list into ascending order, according to the natural ordering of its elements. |
| sort(List<T> list, Comparator<super T> c)                    | This method sorts the specified list according to the order induced by the specified comparator. |

**排序和二分示例**

```java
// Java Program to Demonstrate Binary Search
// Using Collections.binarySearch()

// Importing required classes
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

// Main class
// BinarySearchOnACollection
public class GFG {

	// Main driver method
	public static void main(String[] args)
	{
		// Creating a List
		// Declaring object of string type
		List<String> items = new ArrayList<>();

		// Adding elements to object
		// using add() method
		items.add("Shoes");
		items.add("Toys");
		items.add("Horse");
		items.add("Ball");
		items.add("Grapes");

		// Sort the List
		Collections.sort(items);

		// BinarySearch on the List
		System.out.println(
			"The index of Horse is "
			+ Collections.binarySearch(items, "Horse"));

		// BinarySearch on the List
		System.out.println(
			"The index of Dog is "
			+ Collections.binarySearch(items, "Dog"));
	}
}
```

### Java中的Comparator接口

该接口方便用户对于自定义类的排序，比较器对象能够比较两个相同类的对象。该类存在于`java.util`包中，包含两个方法：compare(Object obj1, Object obj2)和equals(Object element)，其中compare()方法返回值为-1，0和1，若想基于compare()方法对给定集合排序，则必须实现Comparator接口

**二维数组排序示例**

```java
void sort_array(int [][]nums){
    // 使用lambda表达式
    Arrays.sort(nums,(v1,v2)->{
        return v1[0]-v2[0];
    });
}
```

