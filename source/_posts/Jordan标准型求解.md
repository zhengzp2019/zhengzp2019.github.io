---
layout: _post
title: Jordan标准型求解
date: 2022-11-18 10:26:08
categories: 数学
tags:
- 数学
---

# 什么是Jordan标准型？

任何方阵都可通过某一相似变换转化为如下Jordan标准型:
$$
J=\begin{pmatrix}
J_1(\lambda_1) & & & \\
& J_2(\lambda_2) & & \\
& & \ddots & \\
& & & J_s(\lambda_s) \\
\end{pmatrix}
$$

其中Jordan块如下，$\lambda_1,\lambda_2,\cdots,\lambda_s$为A的特征值，可以是多重的。
$$
J_i\left( \lambda _i \right) \ =\ \left[ \begin{matrix}
	\lambda _1&		1&		&		0\\
	&		\lambda _1&		\ddots&		\\
	&		&		\ddots&		1\\
	0&		&		&		\lambda _1\\
\end{matrix} \right]
$$
<!-- more -->
# 为什么要转化为Jordan标准型？

将原矩阵转化为Jordan标准型的原因与转化为对角型矩阵原因类似，只不过有些矩阵无法通过相似转化为对角型，但任何矩阵都可通过相似转化为Jordan型。

Jordan标准型与原矩阵有相同的特征值和特征向量，但是相对于原矩阵有更简单的数字结构，对原矩阵的一些计算与操作可以转化为对Jordan标准型的计算与操作能够大大简化计算过程。

# 如何求Jordan标准型？

## 1、使用初等因子组求Jordan标准型

- 求不变因子组$d_i(\lambda)$

  > 什么是不变因子组？
  >
  > ​	对于一个多项式矩阵（也称$\lambda$矩阵，即矩阵中每一个元素都为$\lambda$多项式），一定可以通过初等变换化简为标准形式，即除对角线元素外，其余元素为0，如下：
  > $$
  > A\left( \lambda \right) =\left[ \begin{matrix}
  > 	d_1\left( \lambda \right)&		&		&		&		&		&		0\\
  > 	&		d_2\left( \lambda \right)&		&		&		&		&		\\
  > 	&		&		\ddots&		&		&		&		\\
  > 	&		&		&		d_r\left( \lambda \right)&		&		&		\\
  > 	&		&		&		&		0&		&		\\
  > 	&		&		&		&		&		\ddots&		\\
  > 	0&		&		&		&		&		&		0\\
  > \end{matrix} \right]
  > $$
  > 其中多项式$d_i(\lambda_i)$是首一多项式（最高次幂的系数为1），且$d_i(\lambda_1)|d_{i+1}(\lambda_{i+1})$即$d_i(\lambda_i)$是$d_{i+1}(\lambda_{i+1})$的因式。多项式矩阵的标准形式不随所采用的初等变换而变，故称$d_i(\lambda)$为不变因子。
  >
  > 
  >
  > 如何求不变因子组？
  >
  > - 将多项式矩阵化为标准型==如何化简==？
  > - 设$D_i(\lambda)$为A(λ)的所有i阶子行列式$\Delta_i^j$的最大因式，则$d_i\left( \lambda \right) =\frac{D_i\left( \lambda \right)}{D_{i-1}\left( \lambda \right)}$，其中$D_i(\lambda)$成为i阶子行列式因子。

- 将不变因子化为不可约因式

- 写出初等因子，每个初等因子对应一个$\lambda_i$

- 写出初等因子对应的Jordan块

- 合成所有的Jordan块

## 2、利用Jordan标准型求变换矩阵

由前面的描述知道，任何一个方阵A都存在一个可逆矩阵P将A变换为Jordan标准型，即$A = P^{-1}JP$，下面说一下如何计算变换矩阵P，变换矩阵在后面的很多计算中都需要使用，如利用Jordan标准型计算矩阵函数，$f(A)=P^{-1}f(J)P$。

易知AP=JP,将P根据Jordan标准块，转化为列向量块，即$P=(p_1,p_2,\cdots,p_s)$，其中$p_i$中列向量数目与第i个Jordan的重数相同，则$Ap_i=J(\lambda_i)p_i$，若第i个Jordan块的重数为m，则$A*(p_{i1},p_{i2},\cdots,p_{im})=J(\lambda_i)*(p_{i1},p_{i2},\cdots,p_{im})$，又因为$J_i\left( \lambda _i \right) \ =\ \left[ \begin{matrix}
	\lambda _1&		1&		&		0\\
	&		\lambda _1&		\ddots&		\\
	&		&		\ddots&		1\\
	0&		&		&		\lambda _1\\
\end{matrix} \right]$，有如下等式：
$$
\begin{array}{l}
	Ap_{i1}=\lambda _ip_{i1}\\
	Ap_{i2}=\lambda _ip_{i2}+p_{i1}\\
	\ \ \ \ \vdots\\
	Ap_{im}=\lambda _ip_{im}+p_{im-1}\\
\end{array}\Longrightarrow \begin{array}{l}
	\left( A-\lambda _iI \right) p_{i1}=0\\
	\left( A-\lambda _iI \right) p_{i2}=p_{i1}\\
	\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\vdots\\
	\left( A-\lambda _iI \right) p_{i\boldsymbol{m}}=p_{i\boldsymbol{m}-1}\\
\end{array}
$$


​	由上式可知$p_{i1}$为A的$\lambda_{i}$对应的特征方程，则对于$p_{i1},\cdots,p_{im}$有两种解法：

1. 由上向下计算，先计算$p_{i1}$，然后一次计算后面的向量，但是$p_{i1}$与后面的向量式相关联的，在对特征向量进行赋值时，受到后面向量关联，计算起来比较麻烦

2. 由下向上计算，现根据等式$(A-\lambda_iI)^mp_{im}=0,且（A-\lambda_iI）^{m-1}p_{im}=p_{im-1}\ne0$计算出$p_{im}$然后根据上式，依次计算出其余向量。

   > 注：由于同一特征值可能出现在不同的Jordan块中，对于这种情况，按各Jordan块阶数高低依次进行处理，高阶先处理，低阶后处理，同阶同时处理。
   >
   > 1. 最高阶按照上述方法计算出$p_{im}$，然后由上述方程依次计算出，$p_{im-1},\cdots,p_{ij}$，且j等于下一个属于同阶特征值的Jordan块的阶数。
   >2. 对于上述新的Jordan块，它的$p_{im}$不仅要满足上述两个式子，还需要与$p_{ij}$线性无关