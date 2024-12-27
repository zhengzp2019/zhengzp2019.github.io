---
layout: _post
title: scipy.optimize使用文档
date: 2022-11-28 16:33:43
categories:
  - [编程语言, python]
tags:
  - 最优化理论
  - 编程
mathjax: True
---

该文档记录了`scipy.optimize`包中个人常用的一些优化方法和`API`，想要了解更多优化方法和使用方式可以参考官方文档[scipy.optimize](https://docs.scipy.org/doc/scipy/tutorial/optimize.html#unconstrained-minimization-of-multivariate-scalar-functions-minimize)

其他的一些优化包：

[cvx](http://cvxr.com/cvx/)：`matlab`中常用的优化包

[cvxopt](https://cvxopt.org/)：基于python语言的凸优化软件包，主要用于解决凸优化问题

[cvxpy](https://www.cvxpy.org/)：也是用于解决凸优化问题的软件包，可以自动将凸优化问题转化为标准形式（用起来应该会比较方便）

<!-- more -->

## 无约束多标量最小值优化(minimize)

## 有约束多标量最小值优化

## 全局优化

## 最小二乘最小化优化

## 单变量最小值优化(minimize_scalar)

当目标函数中只有一个变量该方法拥有更高的效率，该函数提供了两种求最优值方法，其中`brent`用来解决无约束优化问题，`bounded`方法用来解决有约束优化问题。两种不同方法所需要的API如下。

### `API`接口

`minimize_scalar(fun, bracket=None, bounds=None, args=(), method='brent', tol=None, options=None)`

最小化单变量函数

#### 输入

- `fun:` 

  目标函数，返回一个标量

- `bracket:`sequence

  当使用`brent`和`golden`方法时才使用该参数

- `bounds:`

  当选择使用`bounded`方法时，提供变量的边界

- `args:`tuple

  传递函数需要的额外参数

- `method:`str

  最小化所使用的方法

  - Brent
  - Bounded
  - Golden

- `tol:`float

  误差项

- `options:`dict

  - maxiter: 最大迭代次数

  - disp: 

    当disp = True时打印收敛信息

#### 输出

- res: OptimizeResult

## 线性规划(`linprog`)

### 标准式

$$
\begin{equation}
\begin{aligned}
\underset{x}{min}\ \ &c^Tx\\
s.t.\ \ &A_{ub}x\le b_{ub}\\
&A_{eq}x=b_{eq}\\
&l\le x \le u
\end{aligned}
\end{equation}
$$

其中x为多维决策变量，$c,b_{ub},b_{eq},l,,u$为向量，$A_{ub},A_{eq}$矩阵。

### `API`接口

`linprog(c, A_ub=None, b_ub=None, A_eq=None, b_eq=None, bounds=None, method='highs', options=None)`

其中$c,A_{ub},b_{ub},A_{eq},b_{eq}$的定义相同

#### 输入

- `bounds: sequence`

  x中每个元素(min,max)构成的序列，其中min和max为`x`的最大值和最小值构成的边界。

  若不存在边界使用None初始化。

  若只提供一个(min,max)对，则x中所有元素最值边界均由该(min,max)定义

- `methods: str`

  解决标准问题所使用的方法，文档中定义了`highs`,`highs-ds`,`highs-ipm`,`interior-point`,`revised simplex`,和`simplex`方法，在选择具体的方法时需要注意所使用方法的合法性。默认使用`highs`

- `options: dict`

  一个求解器字典，用来传递一些求解问题的参数，例如最大迭代次数，是否显示收敛信息，接受误差等，具体如下：

  - `maxiter: int`

    最大迭代次数

  - `disp: bool`

    True：打印收敛信息

  - `tol: float`

    误差项，当函数值或者决策变量收敛到多少时可以视为0

- `x_0: 1-D array`

  优化的起始点

#### 输出：

- res：OptimizeResult对象

  返回优化结果，包含下述一些属性

  - `x:1-D array`

    优化完成后决策变量的值

  - `fun: float`

    优化完成后，目标函数的值

  - `succes: bool`

    是否找到最优解

  - `status: int`

    表示算法当前的状态

    `0`：优化成功终止

    `1`：到达最大迭代次数

    `2`：当前问题不可行（可能是问题本身问题，也可能是一些`API`提供错误）

    `3`：当前问题无下界（无穷小出收敛，无最小值）

    `4`：数值计算困难

  - `nit: int`

    优化迭代次数

  - `message: str`

    文字描述当前算法状态

    

### 实例

$$
\begin{equation}
\begin{aligned}
\underset{x_1,x_2x_3,x_4}{max}\ \ &29x_1+45x_2\\
s.t.\ \ &x_1-x_2-3x_3\le5\\
&2x_1-3x_2-7x_3+3x_4\ge10\\
&2x_1+8x_2+x_3=60\\
&4x_1+4x_2+x_4=60\\
&0\le x_0\\
&0\le x_1 \le 5\\
&x_2 \le 0.5\\
&-3 \le x_3
\end{aligned}
\end{equation}
$$



#### 1、将目标问题转化为`linprog`可接受的形式

该问题的决策变量为$x=[x_1,x_2,x_3,x_4]^T$，由于`linprog`只能解决最小化问题，需要将目标函数转化为如下最小化问题
$$
\underset{x_1,x_2,x_3,x_4}{min}\ \ -29x_1-45x_2+0x_3+0x_4
$$
而约束条件只接受小于等于约束，等式约束和决策变量定义域，则不等式约束转化后如下
$$
x_1-x_2-3x_3+0x_4\le5\\
-2x_1+3x_2+7x_3-3x_4\le-10\\
$$

#### 2、写出linprog所需接口的矩阵和向量形式

首先定义优化问题初始点`x0`，然后写出$c,A_{ub},b_{ub},A_{eq},b_{eq}$
$$
\begin{aligned}
&c=[-29,-45,0,0]^T\\
&A_{ub} = \left[ \begin{matrix}
	1&		-1&		-3&		0\\
	-2&		3&		7&		-3\\
\end{matrix} \right] \\
&b_{ub}=[5,-10]^T\\
&A_{eq}=
\left[ \begin{matrix}
2&8&1&0\\
4&4&0&1\\
\end{matrix} \right]\\
&b_{eq}=[60,60]^T
\end{aligned}
$$
其中决策变量的定义域定义为`linprog`的所需要的`bounds`变量

```python
bounds = [(0, None), (0, 6), (None, 0.5), (-3, None)]
```



#### 3、定义`linprog`所需要的其它`API`

完成上面步骤后，即可求得目标问题最优解，同时也可让程序在优化过程中做一些其他工作，最常见的是向程序传递一个options对象，让程序输出是否收敛信息。

```python
options = {
    'maxiter': 50,
    'disp': True
}
```

#### 4、上述问题的完整求解过程如下

```python
c = [-29, -45, 0, 0]
c = np.array(c)
A_ub = [[1, -1, -3, 0],
        [-2, 3, 7, -3]]
b_ub = [5, -10]
A_eq = [[2, 8, 1, 0],
        [4, 4, 0, 1]]
b_eq = [60, 60]
A_ub = np.array(A_ub)
b_ub = np.array(b_ub)
A_eq = np.array(A_eq)
b_eq = np.array(b_eq)
options = {
    'maxiter': 50,
    'disp': True
}
bounds = [(0, None), (0, 5), (None, 0.5), (-3, None)]
res = linprog(c, A_ub=A_ub, b_ub=b_ub, A_eq=A_eq,
              b_eq=b_eq, bounds=bounds, options=options)
print(res)
```

输出结果如下

![image-20221126154809402](https://raw.githubusercontent.com/zhengzp2019/Image/main/image-20221126154809402.png)

结果中显示该问题是不可行的，这种情况是存在的，可能的原因是决策变量的约束条件太苛刻，将`x1`的边界放松成(0,6)即可得到如下结果

<img src="https://raw.githubusercontent.com/zhengzp2019/Image/main/image-20221126155131738.png" alt="image-20221126155131738" style="zoom:80%;" />