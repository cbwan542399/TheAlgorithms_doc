# all_subsequences 所有子序列

将n个元素组成的序列进行选择，列出其所有的子序列，
其子序列总数为 $ 2^n $ 

## 算法

在这个问题中，我们想要确定所有可能的子序列  
对于给定序列的。 我们使用回溯来解决这个问题。  

## 范例：
由$ ['A', 'B', 'C'] $  3个字符组成的序列，其子序列共有 $ 2^n = 2^3 =8 $ 
其子序列如下：
$$
  []  \\
  ['C'] \\
  ['B']  \\
  ['B', 'C'] \\
  ['A']  \\
  ['A', 'C'] \\
  ['A', 'B']  \\
  ['A', 'B', 'C'] \\
$$

## 代码
[all_subsequences.py]{..\src\backtracking\all_subsequences.py}




```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块

"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

## 案例一： 
由$ ['A', 'B', 'C'] $  3个字符组成的序列，其子序列共有 $ 2^n = 2^3 =8 $ 


```python
from backtracking.all_subsequences import generate_all_subsequences
from typing import Any, List
"""
"""
seq: List[Any] =["A","B", "C"]
generate_all_subsequences(seq)

# seq: List[Any] =["A","B", "C"]
# generate_all_subsequences(seq)

```

    []
    ['C']
    ['B']
    ['B', 'C']
    ['A']
    ['A', 'C']
    ['A', 'B']
    ['A', 'B', 'C']
    

## 案例二： 
由$  [3,2,1,4,"C"] $  3个字符组成的序列，其子序列共有 $ 2^n = 2^5 =32 $ 


```python
from backtracking.all_subsequences import generate_all_subsequences
from typing import Any, List
"""
"""
seq: List[Any] =  [3,2,1,4,"C"]
generate_all_subsequences(seq)
```

    []
    ['C']
    [4]
    [4, 'C']
    [1]
    [1, 'C']
    [1, 4]
    [1, 4, 'C']
    [2]
    [2, 'C']
    [2, 4]
    [2, 4, 'C']
    [2, 1]
    [2, 1, 'C']
    [2, 1, 4]
    [2, 1, 4, 'C']
    [3]
    [3, 'C']
    [3, 4]
    [3, 4, 'C']
    [3, 1]
    [3, 1, 'C']
    [3, 1, 4]
    [3, 1, 4, 'C']
    [3, 2]
    [3, 2, 'C']
    [3, 2, 4]
    [3, 2, 4, 'C']
    [3, 2, 1]
    [3, 2, 1, 'C']
    [3, 2, 1, 4]
    [3, 2, 1, 4, 'C']
    


```python

```
