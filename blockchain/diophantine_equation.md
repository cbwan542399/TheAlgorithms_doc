# modular_division 



## 定义
丢番图方程又名不定方程、整系数多项式方程，是变量仅容许是整数的多项式等式；即形式如下图的方程，
$$ a_1x_1^{b_1} + a_2x_2^{b_2} +\ldots+ a_nx_n^{b_n} = C $$


其中所有的$ a_j,b_j $ 和 c 均是整数，若其中能找到一组整数解者则称之有整数解。
丢番图问题有数条等式，其数目比未知数的数目少；<br>
丢番图问题要求找出对所有等式都成立的整数组合。<br>
对丢番图问题的数学研究称为丢番图分析 <br>
3世纪希腊数学家亚历山大城的丢番图曾对这些方程进行研究。 <br>
丢番图方程的例子有贝祖等式、勾股定理的整数解、四平方和定理和费马最后定理等。
```



## 代码
[modular_division.py]{..\src\blockchain\modular_division.py}


```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块

"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

## 案例一： 
最简化的丢番图方程（Diophantine Equation） <br>
Diophantine Equation : Given integers a,b,c ( at least one of a and b != 0), the
diophantine equation a*x + b*y = c has a solution (where x and y are integers)
iff gcd(a,b) divides c.



```python
from blockchain.diophantine_equation import diophantine
"""
"""
# diophantine(10,6,14) #  (-7.0, 14.0)
a,b,c = 10,6,14
(x1,y1) = diophantine(a,b,c)
(x,y) = (int(x1),int(y1))
print ('ax + by = c ')
print (f'即：({a})*({x}) + ({b})*({y}) = ({c}) ')

# diophantine(391,299,-69)  #    (9.0, -12.0)
a,b,c = 391,299,-69
(x1,y1) = diophantine(a,b,c)
(x,y) = (int(x1),int(y1))
print ('ax + by = c ')
print (f'即：({a})*({x}) + ({b})*({y}) = ({c}) ')


```

    ax + by = c 
    即：(10)*(-7) + (6)*(14) = (14) 
    ax + by = c 
    即：(391)*(9) + (299)*(-12) = (-69) 
    

## 案例二： 
最简化的丢番图方程（Diophantine Equation）
Finding All solutions of Diophantine Equations:
```
diophantine_all_soln(a: int, b: int, c: int, n: int = 2) -> None:
   # n is the number of solution you want, n = 2 by default
```



```python
from blockchain.diophantine_equation import diophantine_all_soln
"""
"""
"""
   >>> diophantine_all_soln(10, 6, 14)
    -7.0 14.0
    -4.0 9.0

    >>> diophantine_all_soln(10, 6, 14, 4)
    -7.0 14.0
    -4.0 9.0
    -1.0 4.0
    2.0 -1.0

    >>> diophantine_all_soln(391, 299, -69, n = 4)
    9.0 -12.0
    22.0 -29.0
    35.0 -46.0
    48.0 -63.0
"""
print("diophantine_all_soln(10, 6, 14):")
diophantine_all_soln(10, 6, 14)

print("diophantine_all_soln(10, 6, 14, 4):")
diophantine_all_soln(10, 6, 14, 4)

print("diophantine_all_soln(391, 299, -69, n = 4):")
diophantine_all_soln(391, 299, -69, n = 4)


```

    diophantine_all_soln(10, 6, 14):
    -7.0 14.0
    -4.0 9.0
    diophantine_all_soln(10, 6, 14, 4):
    -7.0 14.0
    -4.0 9.0
    -1.0 4.0
    2.0 -1.0
    diophantine_all_soln(391, 299, -69, n = 4):
    9.0 -12.0
    22.0 -29.0
    35.0 -46.0
    48.0 -63.0
    
