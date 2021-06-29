# newton_method   牛顿迭代法求解

参考： https://baike.baidu.com/item/%E7%89%9B%E9%A1%BF%E8%BF%AD%E4%BB%A3%E6%B3%95/10887580?fromtitle=%E7%89%9B%E9%A1%BF%E6%B3%95&fromid=1384129&fr=aladdin <br>


牛顿迭代法（Newton's method）又称为牛顿-拉夫逊（拉弗森）方法（Newton-Raphson method），它是牛顿在17世纪提出的一种在实数域和复数域上近似求解方程的方法。

- 产生背景 <br>
多数方程不存在求根公式，因此求精确根非常困难，甚至不可解，从而寻找方程的近似根就显得特别重要。方法使用函数 的泰勒级数的前面几项来寻找方程 的根。牛顿迭代法是求方程根的重要方法之一，其最大优点是在方程 的单根附近具有平方收敛，而且该法还可以用来求方程的重根、复根，此时线性收敛，但是可通过一些方法变成超线性收敛。另外该方法广泛用于计算机编程中。


- 牛顿迭代公式 <br>
设 $ r $ 是$ f(x)=0 $ 的根，选取$ x_0 $ 作为 $ r $ 的初始近似值，过点$(x_0,f(x_0)) $ 做曲线 $ y= f(x) $ 的切线 $ L $，$ L: y=f(x_0)+f^{'}(x_0)(x-x_0) $，则 $L $与$ X $ 轴交点的横坐标 $X_1=X_0-\frac{f(x_0)}{f^{'}(x_0)} $，称 $ X_1$为 $ r $的一次近似值。<br>
过点 $(x_1,f(x_1)) $ 做曲线  $ y= f(x) $  的切线，并求该切线与$x$ 轴交点的横坐标 ，称 $X_2=X_1-\frac{f(x_1)}{f^{'}(x_1)} $ 为r的二次近似值。<br>
重复以上过程，得 $ r $ 的近似值序列，其中，$X_{n+1}=X_n-\frac{f(x_n)}{f^{'}(x_n)} $ 称为 $ r $的$n+1 $ 次近似值，上式称为牛顿迭代公式。<br>

用牛顿迭代法解非线性方程，是把非线性方程 $f(x）=0 $ 线性化的一种近似方法。把$ f(x) $ 在点 $ x_0 $ 的某邻域内展开成泰勒级数
$ 
  f(x)=f(x_0)+ f^{'}(x_0)(x-x_0)+\frac{f^{"}(x_0)(x-x_0)^2}{2!}+\cdots+ \frac{f^{(n)}(x_0)(x-x_0)^n}{n!}+R_n(x)
$  
，取其线性部分（即泰勒展开的前两项），并令其等于0，即 
$ 
  f(x)=f(x_0)+ f^{'}(x_0)(x-x_0)
$
 ，以此作为非线性方程 $ f(x) =0 $ 的近似方程，若 $ f^{'}(x_0) \neq 0 $，则其解为 $ x_1=x_0-\frac{f(x_0)}{f^{'}(x_0)} $， 这样，得到牛顿迭代法的一个迭代关系式：$ x_{n+1}=x_n-\frac{f(x_n)}{f^{'}(x_n)} $ 。
 
已经证明，如果是连续的，并且待求的零点是孤立的，那么在零点周围存在一个区域，只要初始值位于这个邻近区域内，那么牛顿法必定收敛。 并且，如果不为0, 那么牛顿法将具有平方收敛的性能. 粗略的说，这意味着每迭代一次，牛顿法结果的有效数字将增加一倍。
迭代法也称辗转法，是一种不断用变量的旧值递推新值的过程，跟迭代法相对应的是直接法（或者称为一次解法），即一次性解决问题。迭代算法是用计算机解决问题的一种基本方法。它利用计算机运算速度快、适合做重复性操作的特点，让计算机对一组指令（或一定步骤）重复执行，在每次执行这组指令（或这些步骤）时，都从变量的原值推出它的一个新值。
利用迭代算法解决问题，需要做好以下三个方面的工作：
- 1、确定迭代变量 <br>
在可以用迭代算法解决的问题中，至少存在一个可直接或间接地不断由旧值递推出新值的变量，这个变量就是迭代变量。
- 2、建立迭代关系式 <br>
所谓迭代关系式，指如何从变量的前一个值推出其下一个值的公式（或关系）。迭代关系式的建立是解决迭代问题的关键，通常可以使用递推或倒推的方法来完成。
- 3、对迭代过程进行控制 <br>
在什么时候结束迭代过程？这是编写迭代程序必须考虑的问题。不能让迭代过程无休止地执行下去。迭代过程的控制通常可分为两种情况：一种是所需的迭代次数是个确定的值，可以计算出来；另一种是所需的迭代次数无法确定。对于前一种情况，可以构建一个固定次数的循环来实现对迭代过程的控制；对于后一种情况，需要进一步分析得出可用来结束迭代过程的条件。

- 算法
def newton(    <br>
    function: RealFunc,   -- 函数 $ f(x) $    <br>
    derivative: RealFunc, -- 函数 $ f^{'}(x) $  <br>
    starting_int: int,    -- 初始值   <br>
) -> float:  <br>


## 代码
[newton_method.py]{..\src\arithmetic_analysis\newton_method.py}




```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块
"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

** 案例一 <br>

    >>>newton(lambda x: x ** 3 - 2 * x - 5, lambda x: 3 * x ** 2 - 2, 3)
    2.0945514815423474
    >>> newton(lambda x: x ** 3 - 1, lambda x: 3 * x ** 2, -2)
    1.0
    >>> newton(lambda x: x ** 3 - 1, lambda x: 3 * x ** 2, -4)
    1.0000000000000102
    >>> import math
    >>> newton(math.sin, math.cos, 1)
    0.0
    >>> newton(math.sin, math.cos, 2)
    3.141592653589793
    >>> newton(math.cos, lambda x: -math.sin(x), 2)
    1.5707963267948966



```python
from arithmetic_analysis.newton_method import  newton
import math
"""
"""

print(newton(lambda x: x ** 3 - 2 * x - 5, lambda x: 3 * x ** 2 - 2, 3))
# 2.0945514815423474

print(newton(lambda x: x ** 3 - 1, lambda x: 3 * x ** 2, -2))
# 1.0
print(newton(lambda x: x ** 3 - 1, lambda x: 3 * x ** 2, -4))
# 1.0000000000000102
print(newton(math.sin, math.cos, 1))
# 0.0
print(newton(math.sin, math.cos, 2))
# 3.141592653589793
print(newton(math.cos, lambda x: -math.sin(x), 2))
# 1.5707963267948966

```

    2.0945514815423474
    1.0
    1.0000000000000102
    0.0
    3.141592653589793
    1.5707963267948966
    

** 案例二 <br>

def f(x: float) -> float:
def f1(x: float) -> float:   #  $ f_1= f^{'} $
求  newton(    <br>
    function: RealFunc,   -- 函数 $ f(x) $    <br>
    derivative: RealFunc, -- 函数 $ f^{'}(x) $  <br>
    starting_int: int,    -- 初始值   <br>
) -> float:  <br>






```python
from arithmetic_analysis.newton_method import  newton
def f(x: float) -> float:
    return (x ** 3) - (2 * x) - 5


def f1(x: float) -> float:
    return 3 * (x ** 2) - 2

print(newton(f, f1, 3))


```

    2.0945514815423474
    
