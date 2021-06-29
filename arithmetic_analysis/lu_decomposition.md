# lu_decomposition LU 三角分解 

Lower-Upper (LU) Decomposition

参考：https://baike.baidu.com/item/%E4%B8%89%E8%A7%92%E5%88%86%E8%A7%A3%E6%B3%95/19061680?fr=aladdin

三角分解法亦称因子分解法，由消元法演变而来的解线性方程组的一类方法。设方程组的矩阵形式为$ Ax=b $，三角分解法就是将系数矩阵A分解为一个下三角矩阵L和一个上三角矩阵U之积：$ A=LU $ ，然后依次解两个三角形方程组$ Ly=b $ 和 $ Ux=y $，而得到原方程组的解，例如，杜利特尔分解法、乔莱斯基分解法等就是三角分解法。



## 基本介绍
若能通过正交变换，将系数矩阵A分解为$ A=LU $ ，其中$ L $是单位下三角矩阵(主对角线元素为1的下三角矩阵)，而$ U $ 是上三角矩阵，则线性方程组$ Ax=b $ 变为$ LUx =b $，若令$ Ux=y $ ，则线性方程组$ Ax=b $ 的求解分为两个三角方程组的求解：
- (1)求解$ Ly=b $ ，得y；
- (2)再求解$ Ux=y $，即得方程组的解x；
因此三角分解法的关键问题在于系数矩阵A的LU分解

## 矩阵能LU分解的充分条件
一般地，任给一个矩阵不一定有LU分解，下面给出一个矩阵能LU分解的充分条件。<br>
定理1 对任意矩阵 $ A\in R^{n*n} （n\geq 2）$ ，若A的各阶顺序主子式均不为零，则A有唯一的Doolittle分解(或Crout分解)。<br>
定理2 若矩阵 $ A\in R^{n*n} （n\geq 2）$ 非奇异，且其$ LU $ 分解存在，则$ A $的$ LU $分解是唯一的。<br>

## 矩阵A的Doolittle分解
定义1 设  $ A\in R^{n*n} （n\geq 2）$，称A=LU，其中:<br>
$$ 
  L= 
    \begin{bmatrix} 
      1  \\ 
      l_{21} & 1 \\
      \vdots & \vdots & \vdots & \ddots \\
      l_{n1} & l_{n2} & \cdots & l_{n,n-1} & 1
    \end{bmatrix}
    ,
  U= 
    \begin{bmatrix} 
      u_{11}  & u_{12} & \cdots & u_{1n} \\ 
              & u_{22} & \cdots & u_{2n} \\ 
               &        & \ddots & \vdots \\ 
               &       &        & u_{nn} \\ 
    \end{bmatrix}
    
$$

假设A的各阶顺序主子式均不为零，从Gauss消去法的消元过程可以看出，第一次消元时执行了n一1次初等行变换，若用矩阵的语言解释，相当于
$$ Ax= A^{(0)}x = b => A^{(1)}x =b^{(1)},L_1A^{(0)} = A^{(1)} ,$$

其中 
$$ 
  L_1= 
    \begin{bmatrix} 
      1  \\ 
      -l_{21} & 1 \\
      -l_{31} & 0 & 1 \\
      \vdots & \vdots & \vdots & \ddots \\
      -l_{n1} & 0 & \cdots & 0 & 1
    \end{bmatrix}
$$
第二次消元时，相当于
$$ A^{(1)}x =b^{(1)} => A^{(2)}x =b^{(2)}, L_2A^{(1)}=A^{(2)}$$

其中 
$$ 
  L_2= 
    \begin{bmatrix} 
      1                                  \\ 
      0      & 1                          \\
      0      & -l_{32} & 1                 \\
      \vdots & \vdots  & \vdots & \ddots    \\
      0      & -l_{n2} & 0      & \cdots  & 1
    \end{bmatrix}
$$

重复上述过程，经过n一1次消元，最后得到等价方程组：
$$ A^{(n-1)}x =b^{(n-1)}, L_{(n-1)}A^{(n-1)}=A^n =U,$$
其中
$$ 
  L_{n-1}= 
    \begin{bmatrix} 
      1                                          \\ 
      0      & 1                                 \\
      0      & 0       & \ddots                   \\
      \vdots & \vdots  & \vdots & 1              \\
      0      & 0       & \cdots & l_{n,{n-1}} & 1
    \end{bmatrix}
$$
综上所述，得 
$$ 
   A = A^{(0)}
     = L_1^{-1} A^{(1)}
     = L_2^{-1} L_1^{-1} A^{(2)}
     = \cdots 
     = L_{n-1}^{-1} \cdots L_2^{-1} L_1^{-1} A^{(n-1)}
$$

 为上三角矩阵，记 $ A^{(n-1)}=U $,且
 $$ 
   L_{n-1}^{-1} \cdots L_2^{-1} L_1^{-1} 
  =
      \begin{bmatrix} 
      1                                          \\ 
      l_{21}      & 1                             \\
      l_{31}      & l_{32}      & 1               \\
      \vdots & \vdots  & \vdots & \ddots              \\
      l_{n1}      & l_{n2}       & \cdots & l_{n,{n-1}} & 1
    \end{bmatrix}
 =L
 $$ ,

于是有 
$$
   A = A^{(0)}
     = LA^{(n-1)}
     = LU
 $$

注上述过程中，若不假设A的各阶顺序主子式均不为零，只假设A非奇异，则Gauss消元过程未必能完全实施，一般需要选主元，然后进行初等行或列变换，以保证消元过程的进行．若用矩阵的语言解释，相当于对A左乘或右乘一个置换矩阵。




```python
"""
Prepare
   1 . sys.path 中增加 TheAlgorithms\src 子模块
"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')
```

例子一： LU 矩阵分解
$$
  A=LU \text 即：\\

    \begin{bmatrix}
        2 & -2 & 1 \\
        1 & 1 &  2 \\
        5 & 3 & 1 
     \end{bmatrix}
      =
      \begin{bmatrix}
          1 & 0 & 0 \\
          0 & 1 & 0 \\
        2.5 & 8 & 1 
      \end{bmatrix}
      *
      \begin{bmatrix}
        2 & -2 & 1 \\
        0 & 1 &  2 \\
        0 & 0 & -17.5 
      \end{bmatrix}

$$
    >>> matrix = np.array([[2, -2, 1], [0, 1, 2], [5, 3, 1]])
    >>> outcome = lower_upper_decomposition(matrix)
    >>> outcome[0]
    array([[1. , 0. , 0. ],
           [0. , 1. , 0. ],
           [2.5, 8. , 1. ]])
    >>> outcome[1]
    array([[  2. ,  -2. ,   1. ],
           [  0. ,   1. ,   2. ],
           [  0. ,   0. , -17.5]])




```python
from arithmetic_analysis.lu_decomposition import lower_upper_decomposition
"""
  lower_upper_decomposition(table: ndarray) -> Tuple[ndarray, ndarray]:
     table: ndarray, 参数 A 矩阵
     Tuple[ndarray, ndarray] 由 （L 矩阵，U 矩阵 ） 组成的 元组；
"""
A = [
     [2, -2, 1],
     [0, 1, 2], 
     [5, 3, 1]
    ]
(L,U)= lower_upper_decomposition(A)  # (L,U) 构建反回结果的元组
print ("A=LU")
print ("A=:",A)
print ("L=:",L)
print ("U=:",U)


```

    A=LU
    A=: [[2, -2, 1], [0, 1, 2], [5, 3, 1]]
    L=: [[1.  0.  0. ]
     [0.  1.  0. ]
     [2.5 8.  1. ]]
    U=: [[  2.   -2.    1. ]
     [  0.    1.    2. ]
     [  0.    0.  -17.5]]
    

例子二： LU 矩阵分解
$$
  A =
      \begin{bmatrix}
        1 & 1 & 1 & 1\\
        1 & 2 & 3 & 4\\
        1 & 3 & 6 & 10 \\
        1 & 4 & 10 & 20         
     \end{bmatrix}
$$



```python
from arithmetic_analysis.lu_decomposition import lower_upper_decomposition
"""
"""
A = [
     [1, 1, 1, 1],
     [1, 2, 3, 4], 
     [1, 3, 6, 10],
     [1, 4, 10, 20]
    ]
(L,U)= lower_upper_decomposition(A)  # (L,U) 构建反回结果的元组
print ("A=LU")
print ("A=:",A)
print ("L=:",L)
print ("U=:",U)


```

    A=LU
    A=: [[1, 1, 1, 1], [1, 2, 3, 4], [1, 3, 6, 10], [1, 4, 10, 20]]
    L=: [[1. 0. 0. 0.]
     [1. 1. 0. 0.]
     [1. 2. 1. 0.]
     [1. 3. 3. 1.]]
    U=: [[1. 1. 1. 1.]
     [0. 1. 2. 3.]
     [0. 0. 1. 3.]
     [0. 0. 0. 1.]]
    


```python

```
