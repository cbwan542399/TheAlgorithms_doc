# n_queens_math  N皇后问题


八皇后问题，是一个古老而著名的问题.该问题是国际西洋棋棋手马克斯·贝瑟尔于1848年提出：在8×8格的国际象棋上摆放八个皇后，使其不能互相攻击，即任意两个皇后都不能处于同一行、同一列或同一斜线上，问有多少种摆法?

那么，我们将8皇后问题推广一下，就可以得到我们的N皇后问题了。N皇后问题是一个经典的问题，在一个NxN的棋盘上放置N个皇后，
使其不能互相攻击 (同一行、同一列、同一斜线上的皇后都会自动攻击) 那么问，有多少种摆法？





## 代码
[n_queens_math.py]{..\src\backtracking\n_queens_math.py}




```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块

"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

## 案例一： 


```
def n_queens_solution(n: int) -> None:
    boards: List[List[str]] = []
    depth_first_search([], [], [], boards, n)
```


```python
from backtracking.n_queens_math import n_queens_solution
import math
"""
"""
n_queens_solution(5)


    

```

    Q . . . . 
    . . Q . . 
    . . . . Q 
    . Q . . . 
    . . . Q . 
    
    Q . . . . 
    . . . Q . 
    . Q . . . 
    . . . . Q 
    . . Q . . 
    
    . Q . . . 
    . . . Q . 
    Q . . . . 
    . . Q . . 
    . . . . Q 
    
    . Q . . . 
    . . . . Q 
    . . Q . . 
    Q . . . . 
    . . . Q . 
    
    . . Q . . 
    Q . . . . 
    . . . Q . 
    . Q . . . 
    . . . . Q 
    
    . . Q . . 
    . . . . Q 
    . Q . . . 
    . . . Q . 
    Q . . . . 
    
    . . . Q . 
    Q . . . . 
    . . Q . . 
    . . . . Q 
    . Q . . . 
    
    . . . Q . 
    . Q . . . 
    . . . . Q 
    . . Q . . 
    Q . . . . 
    
    . . . . Q 
    . Q . . . 
    . . . Q . 
    Q . . . . 
    . . Q . . 
    
    . . . . Q 
    . . Q . . 
    Q . . . . 
    . . . Q . 
    . Q . . . 
    
    10 solutions were found.
    


```python

```
