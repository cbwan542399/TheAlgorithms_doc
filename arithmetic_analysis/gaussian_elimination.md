# gaussian_elimination  高斯消元法

## 简介
数学上，高斯消元法（或译：高斯消去法），是线性代数规划中的一个算法，可用来为线性方程组求解。但其算法十分复杂，不常用于加减消元法，求出矩阵的秩，以及求出可逆方阵的逆矩阵。不过，如果有过百万条等式时，这个算法会十分省时。一些极大的方程组通常会用迭代法以及花式消元来解决。当用于一个矩阵时，高斯消元法会产生出一个“行梯阵式”。高斯消元法可以用在电脑中来解决数千条等式及未知数。亦有一些方法特地用来解决一些有特别排列的系数的方程组。

## 历史
该方法以数学家高斯命名，由拉布扎比.伊丁特改进，发表于法国,但最早出现于中国古籍《九章算术》，成书于约公元前150年。 

## 原理
### 内容
消元法是将方程组中的一方程的未知数用含有另一未知数的代数式表示，并将其代入到另一方程中，这就消去了一未知数，得到一解；或将方程组中的一方程倍乘某个常数加到另外一方程中去，也可达到消去一未知数的目的。消元法主要用于二元一次方程组的求解。
### 核心
- 1)两方程互换，解不变；
- 2)一方程乘以非零数k，解不变；
- 3)一方程乘以数k加上另一方程，解不变  。

### 求逆矩阵具体例子
例如，考虑下面的矩阵
$$
        \begin{bmatrix}
        2 & -1 & 0 \\
        -1 & 2 & -1 \\
        0 & -1 & 2 
        \end{bmatrix}
$$

为了找到这个矩阵的逆矩阵，扩充以下矩阵：
$$
  \begin{bmatrix}
     A|I
  \end{bmatrix} =
  \left[
     \begin{array}{ccc|ccc}
        2 & -1 & 0 & 1 & 0 & 0 \\
        -1 & 2 & -1 & 0 & 1 & 0 \\
        0 & -1 & 2 & 0 & 0 & 1 
     \end{array}
  \right]
$$

通过计算，可以将增广矩阵转换为简化行阶梯形式，即把左边转化为单位矩阵：

$$
  \begin{bmatrix}
     I|B
  \end{bmatrix} =
  \left[
     \begin{array}{ccc|ccc}
        1 & 0 & 0 & \frac34 & \frac12 & \frac14 \\
        0 & 1 & 0 & \frac12 & 1 & \frac12 \\
        0 & 0 & 1 & \frac14 & \frac12 & \frac34 
     \end{array}
  \right]
$$

求得B为A的逆矩阵。

## 其他应用
### 找出逆矩阵
高斯消元法可以用来找出一个可逆矩阵的逆矩阵。设A 为一个 $ N \times N $ 的矩阵，其逆矩阵可被两个分块矩阵表示出来。将一个 $ N \times N $ 单位矩阵 放在A 的右手边，形成一个$ N \times 2N $ 的分块矩阵
$ B = [A,I] $。经过高斯消元法的计算程序后，矩阵B 的左手边会变成一个单位矩阵I ，而逆矩阵
$ A^{(-1)} $  会出现在B 的右手边。
假如高斯消元法不能将A 化为三角形的格式，那就代表A 是一个不可逆的矩阵。
应用上，高斯消元法极少被用来求出逆矩阵。高斯消元法通常只为线性方程组求解。
### 计出秩的基本算法
高斯消元法可应用在任何 $m*n$ 的矩阵A。在不可减去某数的情况下，我们都只有跳到下一行。以一个$ 6 * 9 $ 的矩阵作例，它可以变化为一个行梯阵式：
$$
  \begin{bmatrix}
    1 & * &0 & 0 & * & * & 0 & * & 0 \\
    0 & 0 &1 & 0 & * & * & 0 & * & 0 \\
    0 & 0 &0 & 1 & * & * & 0 & * & 0  \\
    0 & 0 &0 & 0 & 0 & 0 & 1 & * & 0 \\
    0 & 0 &0 & 0 & 0 & 0 & 0 & 0 & 1  \\
    0 & 0 &0 & 0 & 0 & 0 & 0 & 0 & 0
  \end{bmatrix}
$$

而矩阵中的 '*' 是一些数字。这个梯阵式的矩阵T 会有一些关于A的资讯：
A 的秩是5，因为T 有5行非0的行；
A 的列的向量空间，可从A 的第1、3、4、7和9列中得知，其数值在矩阵T 之中；
矩阵中的 '*' 表示了A 的列可怎样写为列中的数的组合。 
### 分析
高斯消元法的算法复杂度是；这就是说，如果系数矩阵的是 $n× n$ ，那么高斯消元法所需要的计算量大约与成比例。
高斯消元法可用在任何域中。
高斯消元法对于一些矩阵来说是稳定的。对于普遍的矩阵来说，高斯消元法在应用上通常也是稳定的，不过亦有例外。





```python
"""
Prepare
   1 . sys.path 中增加 TheAlgorithms\src 子模块
"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')
```

例子一： 求解如下方程的解 <br>
  $$ 
     2x_1 + 2x_2 - 1x_3 = 5 \\      
     0x_1 - 2x_2 - 1x_3 = -7 \\       
     0x_1 + 0x_2 + 5x_3 = 15 
  $$
即：AX=B 如下：
$$
     \begin{bmatrix}
        2 & 2 & 1 \\
        -1 & 2 & -1 \\
        0 & -1 & 2 
      \end{bmatrix}
      *
      \begin{bmatrix}
        x_1 \\
        x_2  \\
        x_3 
      \end{bmatrix}
      =
      \begin{bmatrix}
        5 \\
        -7  \\
        15 
      \end{bmatrix}
$$
解得：<br>  
$$
      \begin{bmatrix}
        x_1 \\
        x_2  \\
        x_3 
      \end{bmatrix}
      =
      \begin{bmatrix}
        2 \\
        2  \\
        3 
      \end{bmatrix}
$$


```python
from arithmetic_analysis.gaussian_elimination import gaussian_elimination 
"""
# 直接调用 bisection 中的 __main__ 内相关信息
"""
A = [
     [2, 2, -1],
     [0, -2, -1], 
     [0, 0, 5]
    ]
B = [
     [5],
     [-7],
     [15]
    ]
X= gaussian_elimination(A,B)
print (X)

```

    [[2.]
     [2.]
     [3.]]
    

例子二： 求解如下方程的解 <br>
$$ 
    2x_1 + 2x_2  = -1 \\        
    0x_1 - 2x_2  = -1 
$$       
即：AX=B 如下：
$$
     \begin{bmatrix}
        2 & 2  \\
        0 & -2 
      \end{bmatrix}
      *
      \begin{bmatrix}
        x_1 \\
        x_2 
      \end{bmatrix}
      =
      \begin{bmatrix}
        -1 \\
        -1 
      \end{bmatrix}
$$
解得：<br>  
$$
      \begin{bmatrix}
        x_1 \\
        x_2 
      \end{bmatrix}
      =
      \begin{bmatrix}
        -1 \\
        0.5
      \end{bmatrix}
$$


```python
from arithmetic_analysis.gaussian_elimination import gaussian_elimination 
"""
  retroactive_resolution(coefficients: np.matrix, vector: np.ndarray) -> np.ndarray:
     coefficients: np.matrix 系数，
     vector： np.ndarray 向量
     -> np.ndarray 向量
"""
A = [
     [2, 2],
     [0, -2]
    ]
B = [
     [-1],
     [-1]
    ]
X= gaussian_elimination(A,B)
print (X)

```

    [[-1. ]
     [ 0.5]]
    


```python

```
