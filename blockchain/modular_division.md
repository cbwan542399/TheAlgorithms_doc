# modular_division  模数除法

- modular_division
```
def modular_division(a: int, b: int, n: int) -> int:
    """
    Modular Division :
    An efficient algorithm for dividing b by a modulo n.

    GCD ( Greatest Common Divisor ) or HCF ( Highest Common Factor )

    Given three integers a, b, and n, such that gcd(a,n)=1 and n>1, the algorithm should
    return an integer x such that 0≤x≤n−1, and  b/a=x(modn) (that is, b=ax(modn)).

    Theorem:
    a has a multiplicative inverse modulo n iff gcd(a,n) = 1

    This find x = b*a^(-1) mod n
    Uses ExtendedEuclid to find the inverse of a

    """
```
- invert_modulo
```
def invert_modulo(a: int, n: int) -> int:
    """
    This function find the inverses of a i.e., a^(-1)
    """
```
- modular_division2
```
def modular_division2(a: int, b: int, n: int) -> int:
    """
    This function used the above inversion of a to find x = (b*a^(-1))mod n
    """
```
- extended_gcd
```
def extended_gcd(a: int, b: int) -> Tuple[int, int, int]:
    """
    Extended Euclid's Algorithm : If d divides a and b and d = a*x + b*y for integers x
    and y, then d = gcd(a,b)
    """
```
- extended_euclid
```
def extended_euclid(a: int, b: int) -> Tuple[int, int]:
    """
    Extended Euclid
    """
```

def greatest_common_divisor(a: int, b: int) -> int:
    """
    Euclid's Lemma :  d divides a and b, if and only if d divides a-b and b
    Euclid's Algorithm
    

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

## 案例一： modular_division
```
modular_division(
    a: int, 
    b: int, 
    n: int) 
    -> int:
    """
    b除以一个模n的有效算法。
    """
```



```python
from blockchain.modular_division import modular_division
"""
"""
print(modular_division(4,8,5)) #2
print(modular_division(3,8,5)) # 1
print(modular_division(4, 11, 5)) #4

```

    2
    1
    4
    

## 案例二：invert_modulo

这个函数求a的逆函数，也就是 $ a^{(-1)} $

```
invert_modulo(
    a: int,
    n: int) 
    -> int:
```


```python
from blockchain.modular_division import invert_modulo
"""
"""

print(invert_modulo(2, 5)) #   3
print(invert_modulo(8,7))  #   1

```

    3
    1
    

## 案例三：modular_division2

这个函数利用上面的a的逆运算求出 $ x = (b*a^{(-1)}) \mod n $ 
```
modular_division2(
    a: int,
    b: int, 
    n: int) 
    -> int:
```


```python
from blockchain.modular_division import modular_division2
"""
"""
print(modular_division2(4,8,5)) #    2
print(modular_division2(3,8,5)) #    1
print(modular_division2(4, 11, 5)) #    4

```

    2
    1
    4
    

## 案例四：extended_gcd

扩展欧几里德算法是用来在已知a, b求解一组x，y，使它们满足贝祖等式：$ ax + by = gcd(a, b) = d $（解一定存在，根据数论中的相关定理）。扩展欧几里德常用在求解模线性方程及方程组中
```
extended_gcd(a: int, b: int) -> Tuple[int, int, int]:
```
    


```python
from blockchain.modular_division import extended_gcd
"""
"""
# print(extended_gcd(10, 6))  #    (2, -1, 2)
a,b = 10, 6
x,y,d = extended_gcd(10, 6)
print(f'extended_gcd({a}, {b}): ',end="")
print(f'{a}*({x})+{b}*({y}) = gcd({a},{b}) = {d}')

# print(extended_gcd(7, 5))  #    (1, -2, 3)

a,b = 7, 5
x,y,d = extended_gcd(10, 6)
print(f'extended_gcd({a}, {b}): ',end="")
print(f'{a}*({x})+{b}*({y}) = gcd({a},{b}) = {d}')

```

    extended_gcd(10, 6): 10*(2)+6*(-1) = gcd(10,6) = 2
    extended_gcd(7, 5): 7*(2)+5*(-1) = gcd(7,5) = 2
    

## 案例五：extended_euclid
扩展欧几里德算法是用来在已知a, b求解一组x，y，使它们满足贝祖等式：$ ax + by = gcd(a, b) = d $（解一定存在，根据数论中的相关定理）。扩展欧几里德常用在求解模线性方程及方程组中。



```python
from blockchain.modular_division import extended_euclid,greatest_common_divisor
"""
"""
#print(extended_euclid(10, 6))  #    (-1, 2)
a,b = 10,6
x,y = extended_euclid(a, b)
gcd = greatest_common_divisor(a,b)  # 最大公约数
print(f'extended_euclid({a}, {b}): ',end="")
print(f'{a}*({x})+{b}*({y}) = gcd({a},{b}) = {gcd}')

# print(extended_euclid(7, 5))  #    (-2, 3)
a,b = 7,5
x,y = extended_euclid(a, b)
gcd = greatest_common_divisor(a,b)  # 最大公约数
print(f'extended_euclid({a}, {b}): ',end="")
print(f'{a}*({x})+{b}*({y}) = gcd({a},{b}) = {gcd}')

```

    extended_euclid(10, 6): 10*(-1)+6*(2) = gcd(10,6) = 2
    extended_euclid(7, 5): 7*(-2)+5*(3) = gcd(7,5) = 1
    

## 案例六：greatest_common_divisor
最大公约数；最大公因子


```python
from blockchain.modular_division import greatest_common_divisor
"""
"""
print(greatest_common_divisor(7,5))  #   1
print(greatest_common_divisor(121, 11)) #  11

```

    1
    11
    
