# rat_in_maze  老鼠在迷宫

回溯法解迷宫

一个迷宫被给出为$ n*n $二进制矩阵的块，其中源块是最左上方的块，即$ Maze[0][0$]，目标块是最右下方的块，即$Maze[n-1][n-1]$。老鼠从源头出发，必须到达目的地。老鼠只能朝两个方向移动：向前和向下

## 算法
```
def run_maze(
    maze: List[List[int]],  # 迷宫list 
    i: int, j: int,         # 起点 (i,j)
    solutions: List[List[int]]) # 解决方案
-> bool:
    """
    This method is recursive starting from (i, j) and going in one of four directions:
    up, down, left, right.
    If a path is found to destination it returns True otherwise it returns False.
    Parameters:
        maze(2D matrix) : maze
        i, j : coordinates of matrix
        solutions(2D matrix) : solutions
    Returns:
        Boolean if path is found True, Otherwise False.
```

## 代码
[rat_in_maze.py]{..\src\backtracking\rat_in_maze.py}




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
def solve_maze(maze: List[List[int]]) -> bool:
    """
    This method solves the "rat in maze" problem.
    In this problem we have some n by n matrix, a start point and an end point.
    We want to go from the start to the end. In this matrix zeroes represent walls
    and ones paths we can use.
    Parameters :
        maze(2D matrix) : maze
    Returns:
        Return: True if the maze has a solution or False if it does not.
```


```python
from backtracking.rat_in_maze import solve_maze
"""
"""
i = 0  # sample i
maze = [[0, 1, 0, 1, 1],
        [0, 0, 0, 0, 0],
        [1, 0, 1, 0, 1],
        [0, 0, 1, 0, 0],
        [1, 0, 0, 1, 0]]
print (f'this is the {i+1} example ')
solve_maze(maze)
'''
    [1, 0, 0, 0, 0]
    [1, 1, 1, 1, 0]
    [0, 0, 0, 1, 0]
    [0, 0, 0, 1, 1]
    [0, 0, 0, 0, 1]
    True
'''
i += 1 
maze = [[0, 1, 0, 1, 1],
        [0, 0, 0, 0, 0],
        [0, 0, 0, 0, 1],
        [0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0]]
print (f'this is the {i+1} example ')
solve_maze(maze)
'''
    [1, 0, 0, 0, 0]
    [1, 0, 0, 0, 0]
    [1, 0, 0, 0, 0]
    [1, 0, 0, 0, 0]
    [1, 1, 1, 1, 1]
    True
'''
i += 1
maze = [[0, 0, 0],
        [0, 1, 0],
        [1, 0, 0]]
print (f'this is the {i+1} example ')
solve_maze(maze)
'''
    [1, 1, 1]
    [0, 0, 1]
    [0, 0, 1]
    True
'''
i += 1
maze = [[0, 1, 0],
        [0, 1, 0],
        [1, 0, 0]]
print (f'this is the {i+1} example ')
solve_maze(maze)
'''
    No solution exists!
    False
'''
i += 1
maze = [[0, 1],
        [1, 0]]
print (f'this is the {i+1} example ')
solve_maze(maze)
'''
    No solution exists!
'''  

```

    this is the 1 example 
    [1, 0, 0, 0, 0]
    [1, 1, 1, 1, 0]
    [0, 0, 0, 1, 0]
    [0, 0, 0, 1, 1]
    [0, 0, 0, 0, 1]
    this is the 2 example 
    [1, 0, 0, 0, 0]
    [1, 0, 0, 0, 0]
    [1, 0, 0, 0, 0]
    [1, 0, 0, 0, 0]
    [1, 1, 1, 1, 1]
    this is the 3 example 
    [1, 1, 1]
    [0, 0, 1]
    [0, 0, 1]
    this is the 4 example 
    No solution exists!
    this is the 5 example 
    No solution exists!
    




    '\n    No solution exists!\n'


