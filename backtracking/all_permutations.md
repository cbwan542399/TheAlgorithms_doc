# all_permutations 所有排列

将n个元素组成的序列进行排列，其序列由数字、字符串 组成，列出其所有的全排列，
其排列数为 $ P_n^n $ 

## 算法

在这个问题中，我们要确定所有可能的排列  
对于给定序列的。 我们使用回溯来解决这个问题。 

## 范例：
由$ ['A', 'B', 'C'] $  3个字符组成的序列，其排列共有 $P_3^3=3*2*1=6 $ 
其排列如下：
$$
  ['A', 'B', 'C'] \\
  ['A', 'C', 'B'] \\
  ['B', 'A', 'C'] \\
  ['B', 'C', 'A'] \\
  ['C', 'A', 'B'] \\
  ['C', 'B', 'A']
$$

## 代码
[all_permutations.py]{..\src\backtracking\all_permutations.py}




```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块

"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

## 案例一： 
由$ ['A', 'B', 'C'] $  组成的所有排列,其排列共有 $P_3^3=3*2*1=6 $ 


```python
from backtracking.all_permutations import generate_all_permutations
from typing import List, Union
"""
"""
sequence: List[Union[int, str]] = ["A", "B", "C"]
generate_all_permutations(sequence)


```

    ['A', 'B', 'C']
    ['A', 'C', 'B']
    ['B', 'A', 'C']
    ['B', 'C', 'A']
    ['C', 'A', 'B']
    ['C', 'B', 'A']
    

## 案例二： 
由$ [3,2,1,4,"C"] $  组成的所有排列,其排列共有 $P_5^5=5*4*3*2*1=6 $ 



```python
from backtracking.all_permutations import generate_all_permutations
from typing import List, Union
"""
"""
sequence: List[Union[int, str]] = [3,2,1,4,"C"]
generate_all_permutations(sequence)

```

    [3, 2, 1, 4, 'C']
    [3, 2, 1, 'C', 4]
    [3, 2, 4, 1, 'C']
    [3, 2, 4, 'C', 1]
    [3, 2, 'C', 1, 4]
    [3, 2, 'C', 4, 1]
    [3, 1, 2, 4, 'C']
    [3, 1, 2, 'C', 4]
    [3, 1, 4, 2, 'C']
    [3, 1, 4, 'C', 2]
    [3, 1, 'C', 2, 4]
    [3, 1, 'C', 4, 2]
    [3, 4, 2, 1, 'C']
    [3, 4, 2, 'C', 1]
    [3, 4, 1, 2, 'C']
    [3, 4, 1, 'C', 2]
    [3, 4, 'C', 2, 1]
    [3, 4, 'C', 1, 2]
    [3, 'C', 2, 1, 4]
    [3, 'C', 2, 4, 1]
    [3, 'C', 1, 2, 4]
    [3, 'C', 1, 4, 2]
    [3, 'C', 4, 2, 1]
    [3, 'C', 4, 1, 2]
    [2, 3, 1, 4, 'C']
    [2, 3, 1, 'C', 4]
    [2, 3, 4, 1, 'C']
    [2, 3, 4, 'C', 1]
    [2, 3, 'C', 1, 4]
    [2, 3, 'C', 4, 1]
    [2, 1, 3, 4, 'C']
    [2, 1, 3, 'C', 4]
    [2, 1, 4, 3, 'C']
    [2, 1, 4, 'C', 3]
    [2, 1, 'C', 3, 4]
    [2, 1, 'C', 4, 3]
    [2, 4, 3, 1, 'C']
    [2, 4, 3, 'C', 1]
    [2, 4, 1, 3, 'C']
    [2, 4, 1, 'C', 3]
    [2, 4, 'C', 3, 1]
    [2, 4, 'C', 1, 3]
    [2, 'C', 3, 1, 4]
    [2, 'C', 3, 4, 1]
    [2, 'C', 1, 3, 4]
    [2, 'C', 1, 4, 3]
    [2, 'C', 4, 3, 1]
    [2, 'C', 4, 1, 3]
    [1, 3, 2, 4, 'C']
    [1, 3, 2, 'C', 4]
    [1, 3, 4, 2, 'C']
    [1, 3, 4, 'C', 2]
    [1, 3, 'C', 2, 4]
    [1, 3, 'C', 4, 2]
    [1, 2, 3, 4, 'C']
    [1, 2, 3, 'C', 4]
    [1, 2, 4, 3, 'C']
    [1, 2, 4, 'C', 3]
    [1, 2, 'C', 3, 4]
    [1, 2, 'C', 4, 3]
    [1, 4, 3, 2, 'C']
    [1, 4, 3, 'C', 2]
    [1, 4, 2, 3, 'C']
    [1, 4, 2, 'C', 3]
    [1, 4, 'C', 3, 2]
    [1, 4, 'C', 2, 3]
    [1, 'C', 3, 2, 4]
    [1, 'C', 3, 4, 2]
    [1, 'C', 2, 3, 4]
    [1, 'C', 2, 4, 3]
    [1, 'C', 4, 3, 2]
    [1, 'C', 4, 2, 3]
    [4, 3, 2, 1, 'C']
    [4, 3, 2, 'C', 1]
    [4, 3, 1, 2, 'C']
    [4, 3, 1, 'C', 2]
    [4, 3, 'C', 2, 1]
    [4, 3, 'C', 1, 2]
    [4, 2, 3, 1, 'C']
    [4, 2, 3, 'C', 1]
    [4, 2, 1, 3, 'C']
    [4, 2, 1, 'C', 3]
    [4, 2, 'C', 3, 1]
    [4, 2, 'C', 1, 3]
    [4, 1, 3, 2, 'C']
    [4, 1, 3, 'C', 2]
    [4, 1, 2, 3, 'C']
    [4, 1, 2, 'C', 3]
    [4, 1, 'C', 3, 2]
    [4, 1, 'C', 2, 3]
    [4, 'C', 3, 2, 1]
    [4, 'C', 3, 1, 2]
    [4, 'C', 2, 3, 1]
    [4, 'C', 2, 1, 3]
    [4, 'C', 1, 3, 2]
    [4, 'C', 1, 2, 3]
    ['C', 3, 2, 1, 4]
    ['C', 3, 2, 4, 1]
    ['C', 3, 1, 2, 4]
    ['C', 3, 1, 4, 2]
    ['C', 3, 4, 2, 1]
    ['C', 3, 4, 1, 2]
    ['C', 2, 3, 1, 4]
    ['C', 2, 3, 4, 1]
    ['C', 2, 1, 3, 4]
    ['C', 2, 1, 4, 3]
    ['C', 2, 4, 3, 1]
    ['C', 2, 4, 1, 3]
    ['C', 1, 3, 2, 4]
    ['C', 1, 3, 4, 2]
    ['C', 1, 2, 3, 4]
    ['C', 1, 2, 4, 3]
    ['C', 1, 4, 3, 2]
    ['C', 1, 4, 2, 3]
    ['C', 4, 3, 2, 1]
    ['C', 4, 3, 1, 2]
    ['C', 4, 2, 3, 1]
    ['C', 4, 2, 1, 3]
    ['C', 4, 1, 3, 2]
    ['C', 4, 1, 2, 3]
    
