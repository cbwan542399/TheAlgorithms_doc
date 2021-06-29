# all_combinations 所有组合

即所有N个数的k个组合，其总数为 $ C_n^k $

## 算法

在这个问题中，我们要确定从 $ 1 {\ldots} n $ 中数出k个数的所有可能的组合,
我们用回溯法来解决这个问题。  

## 范例： 
  $C_n^k = C_4^2 $ 的所有组合是：<br>
  $$ [1, 2], [1, 3], [1, 4], [2, 3], [2, 4], [3, 4]$$


## 代码
[all_combinations.py]{..\src\backtracking\all_combinations.py}




```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块

"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

## 案例一： 
  $C_n^k = C_4^2 $ 的所有组合是：<br>
  $$ [1, 2], [1, 3], [1, 4], [2, 3], [2, 4], [3, 4]$$


```python
from backtracking.all_combinations import generate_all_combinations
"""
"""
n,k=4,2     # 设置 n, k 值 ，其中 n>=k

print(generate_all_combinations(n,k)) # 生成 generate_all_combinations 列表

```

    [[1, 2], [1, 3], [1, 4], [2, 3], [2, 4], [3, 4]]
    

## 案例二： 
  $C_n^k = C_6^4 $ 的所有组合是：<br>

$$ [[1, 2, 3, 4], [1, 2, 3, 5], [1, 2, 3, 6], [1, 2, 4, 5], [1, 2, 4, 6], [1, 2, 5, 6], [1, 3, 4, 5], [1, 3, 4, 6], [1, 3, 5, 6], [1, 4, 5, 6], [2, 3, 4, 5], [2, 3, 4, 6], [2, 3, 5, 6], [2, 4, 5, 6], [3, 4, 5, 6]] $$

 其组合的数量应与 $ C_n^{(n-k)} = C_6^{(6-4)} $ 是一致的
 $$ [[1, 2], [1, 3], [1, 4], [1, 5], [1, 6], [2, 3], [2, 4], [2, 5], [2, 6], [3, 4], [3, 5], [3, 6], [4, 5], [4, 6], [5, 6]] $$


```python
from backtracking.all_combinations import generate_all_combinations
"""
"""
n,k=6,4     # 设置 n, k 值 ，其中 n>=k

myList = generate_all_combinations(n,k) # 生成 generate_all_combinations 列表
print(len(myList)) # 显示其数量
print(myList) # 显示明细list
## 验证 C(6,4)=C(6,2)
myList = generate_all_combinations(n,n-k) # 生成 generate_all_combinations 列表
print(len(myList)) # 显示其数量
print(myList) # 显示明细list


```

    15
    [[1, 2, 3, 4], [1, 2, 3, 5], [1, 2, 3, 6], [1, 2, 4, 5], [1, 2, 4, 6], [1, 2, 5, 6], [1, 3, 4, 5], [1, 3, 4, 6], [1, 3, 5, 6], [1, 4, 5, 6], [2, 3, 4, 5], [2, 3, 4, 6], [2, 3, 5, 6], [2, 4, 5, 6], [3, 4, 5, 6]]
    15
    [[1, 2], [1, 3], [1, 4], [1, 5], [1, 6], [2, 3], [2, 4], [2, 5], [2, 6], [3, 4], [3, 5], [3, 6], [4, 5], [4, 6], [5, 6]]
    
