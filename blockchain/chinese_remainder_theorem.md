# chinese_remainder_theorem   中国余数定理

中国余数定理又称孙子定理，数学著作《孙子算经》卷下第二十六题，叫做“物不知数”问题，原文如下：
有物不知其数，三三数之剩二，五五数之剩三，七七数之剩二。问物几何？即，一个整数除以三余二，除以五余三，除以七余二，求这个整数。<br>
《孙子算经》中首次提到了同余方程组问题，以及以上具体问题的解法，因此在中文数学文献中也会将中国剩余定理称为孙子定理。其实，南宋数学家秦九韶在其著作《数书九章》中，系统的提出并证明了这一类问题的解法，因此这个定理也可以称为孙子秦九韶定理。<br>

明朝数学家程大位将解法编成易于上口的《孙子歌诀》：

三人同行七十稀，五树梅花廿一支，七子团圆正半月，除百零五使得知

这个歌诀给出了模数为3、5、7时候的同余方程的秦九韶解法。意思是：将除以3得到的余数乘以70，将除以5得到的余数乘以21，将除以7得到的余数乘以15，全部加起来后除以105（或者105的倍数），得到的余数就是答案。比如说在以上的物不知数问题里面，按歌诀求出的结果就是23

## 算法
### 中国余数定理说明：
  对于一元线性同余方程组 
  $$ 
     (S)= 
     \begin{cases}
        x \equiv a_1  \quad ( mod \quad {m_1}) \\
        x \equiv a_2  \quad ( mod \quad {m_2}) \\
        \ldots   \\
        x \equiv a_n  \quad ( mod \quad {m_n}) \\
     \end{cases}
  $$ 
  假设整数 $ m_1,m_2, \ldots ,m_n $两两互质，则对任意的整数：$ a_1,a_2, \ldots ,a_n $, 方程组有解，并且通解可以用如下方式构造得到：
设 $ M=m_1 * m_2 * \ldots * m_n =\prod_{i=1}^n m_i  $  是整数$ m_1,m_2, \ldots ,m_n $ 的乘积，并设 是除了mi以外的n- 1个整数的乘积。


### 欧几里得算法 ， 又称辗转相除法
  GCD ( Greatest Common Divisor ) or HCF ( Highest Common Factor )
   最大公约数；最大公因子
求解两个正整数a，b的最大公约数：
  gcd(a,b) = gcd(b,a mod b)
示例：求 GCD (4851, 840)
```
解：
 步骤1：
     4851 / 840 = 5(余651)
     gcd (4851, 840) = gcd (840, 651) 
 步骤2：
     840 / 651 = 1(余189)
     gcd (840, 651) = gcd (651, 189) 
 步骤3：
     651 / 189 = 3(余84)
     gcd (651, 189) = gcd (189, 84) 
  步骤4：
     189 /84 = 2(余21)
     gcd (189, 84) = gcd (84, 21) 
   步骤5：
     84/21 = 4(余0)
     gcd (84, 21) = 21 
故：gcd (4851, 840) =21
```
### 扩展欧几里得算法
   已知整数a、b，扩展欧几里得算法可以在求得a、b的最大公约数的同时，能找到整数x、y（其中一个很可能是负数），使它们满足等式：
   $$ ax+by=gcd(a,b) $$ 
   
## 范例：
- 例1、一个数被5除余2，被6除余4，被7除余3，这个数最少是多少？<br>
解：第一步：判断5，6，7两两互余。   <br>
    第二步：计算5，6，7的最小公倍数，得5×6×7=210。<br>
    第三步：计算各除数的逆元。<br>
     将5去掉，计算6×7=42，42÷5=8……2，将余数2适当的扩大倍数，使除以5的余数是1，很显然这个倍数是3，也就是逆元是3；<br>
    将6去掉，计算5×7=35，35÷6=5……5，将余数5适当的扩大倍数，使除以6的余数是1，很显然这个倍数是5，也就是逆元是5；<br>
    将7去掉，计算5×6=30，30÷7=4……2，将余数2适当的扩大倍数，使除以7的余数是1，很显然这个倍数是4，也就是逆元是4；<br>
   第四步：将余数和逆元和最小公倍数除以该数的商相乘，然后将各个结果相加，再除以最小公倍数所得的余数即为所求。计算42×3×2+35×5×4+30×4×3=1312，1312÷210=6……52，因此这个最小的数就是52。

## 代码
[chinese_remainder_theorem.py]{..\src\blockchain\chinese_remainder_theorem.py}


```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块

"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

## 案例一： 
扩展euclid
```
extended_euclid(a: int, b: int) -> Tuple[int, int]:
```
$$ ax+by=gcd(a,b) $$ 

求解 ：
```
  extended_euclid(10, 6) = (-1, 2) 
```
代表 :
  $$ ax+by=gcd(a,b) $$
即：
$$ 10*(-1)+6*(2) =gcd(10,6) =2  $$






```python
from blockchain.chinese_remainder_theorem import extended_euclid,chinese_remainder_theorem
"""
"""
# extended_euclid(10, 6)  # (-1, 2)
a,b=10,6
(x,y) = extended_euclid(a, b)
print ('a*x+b*y=gcd(a,b) : ')
print (f'({a})*({x}) + ({b})*({y}) = gcd({a},{b}) ')

# extended_euclid(7, 5)  #  (-2, 3)
a,b=7,5
(x,y) = extended_euclid(a, b)
print ('a*x+b*y=gcd(a,b): ')
print (f'({a})*({x}) + ({b})*({y}) = gcd({a},{b}) ')
```

    a*x+b*y=gcd(a,b) : 
    (10)*(-1) + (6)*(2) = gcd(10,6) 
    a*x+b*y=gcd(a,b): 
    (7)*(-2) + (5)*(3) = gcd(7,5) 
    

## 案例二： 
中国余数定理应用
例：  X 除以 5 ，得余数 1
      X 除以 7 ，得余数 3
 求最小的整数 X;

    """
    >>> chinese_remainder_theorem(5,1,7,3)
    31

    Explanation : 31 is the smallest number such that
                (i)  When we divide it by 5, we get remainder 1
                (ii) When we divide it by 7, we get remainder 3


```python
from blockchain.chinese_remainder_theorem import extended_euclid,chinese_remainder_theorem
"""
chinese_remainder_theorem(n1: int, r1: int, n2: int, r2: int) -> int:
  n1，r1:代表除数 ,余数
  n2，r2: 类似

  约束：参考参数代码，目前代码还仅限于两组条件，对于不限多组条件，尚需扩展
"""
print(chinese_remainder_theorem(5,1,7,3)) # 31

# 一个数被5除余2，被6除余4，被7除余3，这个数最少是多少？
# print(chinese_remainder_theorem(5,2,6,4,7,3)) # 52

```

    31
    


```python

```
