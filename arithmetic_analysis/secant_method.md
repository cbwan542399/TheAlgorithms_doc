# Secant method 弦截法

- 参考： https://www.docin.com/p-623621182.html 

虽然牛顿法收敛速度很快，但它每次迭代要计算两个函数：$f(x),f^{'}(x)$ .以前计算导函数一般页言是繁琐的，因此产生了一种不需要计臬导数的方法-弦截法。

为避免导数的计算，我们用差商 $ \frac {f(x_k)-f(x_0)}{x_k-x_0}$ 替代牛顿法中的导数$f^{'}(x_k) $,得到 弦截法（单点弦截法） 的迭代公式：
 $$ X_{k+1} = X_k - \frac{f(x_k)}{f(x_k)-f(x_0)} (x_k-x_0) $$
- 算法
```
 def f(x: float) -> float:

 secant_method(
     lower_bound: float,   # 下界
     upper_bound: float,   # 上界
     repeats: int)         #  重复次数
     -> float: 

```

## 代码
[secant_method.py]{..\src\arithmetic_analysis\secant_method.py}




```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块
"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

** 案例一 <br>

def f(x: float) -> float:  <br>
secant_method(1, 3, 2)  <br>




```python
from arithmetic_analysis.secant_method import f, secant_method
# f: return 8 * x - 2 * exp(-x)

print(f(5)) #   39.98652410600183
'''
secant_method(1, 3, 2) #  0.2139409276214589
'''

print(f"Example: {secant_method(1, 3, 2) = }")

```

    39.98652410600183
    Example: secant_method(1, 3, 2) = 0.2139409276214589
    


```python

```
