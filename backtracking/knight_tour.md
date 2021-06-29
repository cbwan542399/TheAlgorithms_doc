# knight_tour  骑士游历算法

- 1、问题描述
在一个N*M的棋盘上，在任意位置放置一个骑士，骑士的走"日字"，和象棋中的马一样。<br>
问该骑士能否不重复遍历整个棋盘。下面的方法本质还是穷举，所以就写成可以计算出共有多少种不同的遍历方法。<br>

- 2、分析与思路
根据题意，骑士走的下一步可能在棋盘上有多种选择（最多8种），需要选择1种，然后继续走下去，直到无处可走。 <br>
无处可走时有两种情况：
  - 情况一：成功完成了遍历，那么接下来就通过回溯（回到上一步的位置，重新选择下一步的位置），寻找其他的走法。
  - 情况二：未完成遍历，接下来还是要通过回溯继续寻找能够完成遍历的走法。

## 算法
- get_valid_pos 找出骑士可以从当前位置移动到的所有有效位置
```
def get_valid_pos(
    position: Tuple[int, int],   # 当前位置
     n: int)                     # 棋盘大小
-> List[Tuple[int, int]]:
```
- is_complete 检查板(矩阵)是否已完全填满非零值
```
def is_complete(
    board: List[List[int]]  #棋盘
) 
-> bool:
```
- open_knight_tour_helper 助手功能，解决骑士游览问题。
```
def open_knight_tour_helper(
    board: List[List[int]],   # 棋盘
    pos: Tuple[int, int],     # 位置
    curr: int                 # 当前步数 
) -> bool:
```
- open_knight_tour 求大小为n的板的骑士旅行问题的解  
```
def open_knight_tour(n: int) -> List[List[int]]:
    """
    Find the solution for the knight tour problem for a board of size n. Raises
    ValueError if the tour cannot be performed for the given size.
```    
## 代码
[knight_tour.py]{..\src\backtracking\knight_tour.py}




```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块

"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

## 案例一： 

找出骑士可以从当前位置移动到的所有有效位置

```
def get_valid_pos(
    position: Tuple[int, int],   # 当前位置
     n: int)                     # 棋盘大小
-> List[Tuple[int, int]]:
    y, x = position
    positions = [
        (y + 1, x + 2),
        (y - 1, x + 2),
        (y + 1, x - 2),
        (y - 1, x - 2),
        (y + 2, x + 1),
        (y + 2, x - 1),
        (y - 2, x + 1),
        (y - 2, x - 1),
    ]
```


```python
from backtracking.knight_tour import get_valid_pos
"""
"""
print(get_valid_pos((1, 3), 4))  #    [(2, 1), (0, 1), (3, 2)]

print(get_valid_pos((1, 3), 10))  



```

    [(2, 1), (0, 1), (3, 2)]
    [(2, 5), (0, 5), (2, 1), (0, 1), (3, 4), (3, 2)]
    

## 案例二： 
检查板(矩阵)是否已完全填满非零值  

```
def is_complete(board: List[List[int]]) 
-> bool:

return not any(elem == 0 for row in board for elem in row)


```


```python
from backtracking.knight_tour import is_complete
"""
"""

print(is_complete([[1]]))  #    True

print(is_complete([[1, 2], [3, 0]])) #    False

```

    True
    False
    

## 案例三： 求大小为n的板的骑士旅行问题的解  


```python
from backtracking.knight_tour import open_knight_tour
"""
"""
i = 5
thisList = open_knight_tour(i)
# print(list(result))  显示结果不够清晰
print(f'open_knight_tour({i})：')
for i,val in enumerate(thisList):
   print("行号：%s   步骤顺序：%s" % (i + 1, val))

i = 6
thisList = open_knight_tour(i)
# print(list(result))  显示结果不够清晰
print(f'open_knight_tour({i})：')
for i,val in enumerate(thisList):
   print("行号：%s   步骤顺序：%s" % (i + 1, val))
   
```

    open_knight_tour(5)：
    行号：1   步骤顺序：[1, 14, 19, 8, 25]
    行号：2   步骤顺序：[6, 9, 2, 13, 18]
    行号：3   步骤顺序：[15, 20, 7, 24, 3]
    行号：4   步骤顺序：[10, 5, 22, 17, 12]
    行号：5   步骤顺序：[21, 16, 11, 4, 23]
    open_knight_tour(6)：
    行号：1   步骤顺序：[1, 22, 13, 30, 33, 36]
    行号：2   步骤顺序：[12, 29, 2, 35, 14, 31]
    行号：3   步骤顺序：[21, 8, 23, 32, 3, 34]
    行号：4   步骤顺序：[28, 11, 4, 17, 24, 15]
    行号：5   步骤顺序：[7, 20, 9, 26, 5, 18]
    行号：6   步骤顺序：[10, 27, 6, 19, 16, 25]
    
