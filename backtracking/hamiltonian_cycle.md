# hamiltonian_cycle  哈密顿圈问题


哈密顿圈问题(Hamilton circuit problem)是图论中著名的难题之一。巡回售货员问题有一个基于图的天然类似问题，它是图论中的一个基本问题，给定一个有向图G(V，E)，如果G中的圈C恰好经过每一个顶点一次，则称圈C是一个哈密顿圈。换句话说，它构成一条经过所有顶点的、没有重复的“路线”。哈密顿圈问题如下：给定一个有向图G，问它有一条哈密顿圈吗?

- 基本介绍 <br>
设有一个图，若其上存在一个圈，这个圈包含该图上的每一节点，则称该圈为哈密顿圈，这个图称为哈密顿图.哈密顿圈问题可叙述为：什么样的图为哈密顿图，或者说判断一个图是哈密顿图的行之有效的充分必要条件是什么.目前这一问题尚未解决.关于哈密顿圈的研究，最早是欧拉(L.Euler)研究骑士(相当于中国象棋中的马)从棋盘上的某一位置出发，走遍所有可能的位置且每个位置只通过一次后，回到原来的位置，而哈密顿(W.R.Hamilton)研究环游世界的游戏是在欧拉之后近一个世纪，然而却由此开始引起人们对于这个问题的注意.实际上，哈密顿的游戏就是，在一个正十二面体上，从一个顶点开始沿着棱走遍所有的十二个顶点回到原地，使得每一顶点只通过一次.就是在十二面体相应的图上求一个哈密顿圈.若一个图上存在一条路，这条路包含该图上的所有节点，则称该图为可迹图，称这样的路为哈密顿路，若对于一个图上的每一节点，存在一个以该节点为始点的哈密顿路，则称该图为齐次可迹图，一个图被称为哈密顿连通图，若对于这图上任何两节点，存在一条哈密顿路连结这两节点，称一个图为亚哈密顿图，若从这图上去掉无论哪一节点，所得的图都是哈密顿图，称一个图为亚可迹图，若从这图上去掉无论哪一节点，所得的图都是可迹图

- 哈密顿周游世界问题 <br>
1859年，英国数学家、物理学家威廉·罗恩·哈密顿(1805～1865)，提出了以下“周游世界游戏”，据说公布在当地市场上：用图2那样的一个正12面体的20个顶点来表示地球上的20个城市，如何才能从某个城市出发，沿着各条棱走正好只经过每个城市一次，最后返回到出发地点?

"周游世界棋盘”问题是哈密顿问题的特例，其对象后来也扩展为一般的m×n棋盘上走马步的问题。<br>
用电子计算机研究之后，目前的成果有：对任意奇数的m，n，m×n，棋盘上不存在马的哈密顿同路；<br>
国际象棋8 x 8的棋盘上至少存在10条哈密顿回路；<br>
中国象棋9×10的棋盘上至少存在300条哈密顿回路。<br>
这些问题，包括中国数学工作者在内的许多学者仍在不断地寻找解决方法。

要判定一个图是否具有哈密顿圈的问题，是图论中著名的难题之一。除个别情形以外，迄今为止还没有找到一个图是否具有哈密顿圈的必要而且充分的条件。

哈密顿圈问题引出了诸如货郎问题、邮递员问题等类似的问题。
比如，货郎问题就是货郎必须到每个村庄售货，怎样走才能使路程最短?当然，这个问题因为还要求“路程最短”，比哈密顿圈问题难度更大，以致用现代电子计算机来解决都很复杂。

这类问题的研究，促进了最优化方法、图论等问题的研究，促进了运筹学、拓扑学等学科的发展




## 代码
[hamiltonian_cycle.py]{..\src\backtracking\hamiltonian_cycle.py}




```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块

"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

## 案例一： valid_connection
```
def valid_connection(
    graph: List[List[int]], next_ver: int, curr_ind: int, path: List[int]
) -> bool:
    """
    Checks whether it is possible to add next into path by validating 2 statements
    1. There should be path between current and next vertex
    2. Next vertex should not be in path
    If both validations succeeds we return True saying that it is possible to connect
    this vertices either we return False
```


```python
from backtracking.hamiltonian_cycle import valid_connection
"""
"""
'''
 Case 1:Use exact graph as in main function, with initialized values
'''
graph = [[0, 1, 0, 1, 0],
         [1, 0, 1, 1, 1],
         [0, 1, 0, 0, 1],
         [1, 1, 0, 0, 1],
         [0, 1, 1, 1, 0]]
path = [0, -1, -1, -1, -1, 0]
curr_ind = 1
next_ver = 1
print(valid_connection(graph, next_ver, curr_ind, path)) #   True

   
'''
    Case 2: Same graph, but trying to connect to node that is already in path
'''
path = [0, 1, 2, 4, -1, 0]
curr_ind = 4
next_ver = 1
print(valid_connection(graph, next_ver, curr_ind, path)) #    False



```

    True
    False
    

## 案例二：   util_hamilton_cycle
```
def util_hamilton_cycle(graph: List[List[int]], path: List[int], curr_ind: int) -> bool:
    """
    Pseudo-Code
    Base Case:
    1. Check if we visited all of vertices
        1.1 If last visited vertex has path to starting vertex return True either
            return False
    Recursive Step:
    2. Iterate over each vertex
        Check if next vertex is valid for transiting from current vertex
            2.1 Remember next vertex as next transition
            2.2 Do recursive call and check if going to this vertex solves problem
            2.3 If next vertex leads to solution return True
            2.4 Else backtrack, delete remembered vertex

```



```python
from backtracking.hamiltonian_cycle import util_hamilton_cycle
"""
"""
'''
Case 1: Use exact graph as in main function, with initialized values
'''
graph = [[0, 1, 0, 1, 0],
          [1, 0, 1, 1, 1],
          [0, 1, 0, 0, 1],
        [1, 1, 0, 0, 1],
        [0, 1, 1, 1, 0]]
path = [0, -1, -1, -1, -1, 0]
curr_ind = 1
print(util_hamilton_cycle(graph, path, curr_ind)) # True
print(path)                                # [0, 1, 2, 4, 3, 0]
'''
Case 2: Use exact graph as in previous case, but in the properties taken from        middle of calculation
'''
graph = [[0, 1, 0, 1, 0],
         [1, 0, 1, 1, 1],
         [0, 1, 0, 0, 1],
         [1, 1, 0, 0, 1],
         [0, 1, 1, 1, 0]]
path = [0, 1, 2, -1, -1, 0]
curr_ind = 3
print(util_hamilton_cycle(graph, path, curr_ind))   # True
print(path)                                  # [0, 1, 2, 4, 3, 0]
```

    True
    [0, 1, 2, 4, 3, 0]
    True
    [0, 1, 2, 4, 3, 0]
    

## 案例三： hamilton_cycle
```
def hamilton_cycle(graph: List[List[int]], start_index: int = 0) -> List[int]:
    r"""
    Wrapper function to call subroutine called util_hamilton_cycle,
    which will either return array of vertices indicating hamiltonian cycle
    or an empty list indicating that hamiltonian cycle was not found.
    Case 1:
    Following graph consists of 5 edges.
    If we look closely, we can see that there are multiple Hamiltonian cycles.
```



```python
from backtracking.hamiltonian_cycle import hamilton_cycle
"""
"""
'''
For example one result is when we iterate like:
    (0)->(1)->(2)->(4)->(3)->(0)

    (0)---(1)---(2)
     |   /   \   |
     |  /     \  |
     | /       \ |
     |/         \|
    (3)---------(4)
'''
graph = [[0, 1, 0, 1, 0],
         [1, 0, 1, 1, 1],
         [0, 1, 0, 0, 1],
         [1, 1, 0, 0, 1],
         [0, 1, 1, 1, 0]]
print(hamilton_cycle(graph))  #   [0, 1, 2, 4, 3, 0]
'''
    Case 2:
    Same Graph as it was in Case 1, changed starting index from default to 3

    (0)---(1)---(2)
     |   /   \   |
     |  /     \  |
     | /       \ |
     |/         \|
    (3)---------(4)
'''
graph = [[0, 1, 0, 1, 0],
         [1, 0, 1, 1, 1],
         [0, 1, 0, 0, 1],
         [1, 1, 0, 0, 1],
         [0, 1, 1, 1, 0]]
print(hamilton_cycle(graph, 3))  #    [3, 0, 1, 2, 4, 3]
'''

    Case 3:
    Following Graph is exactly what it was before, but edge 3-4 is removed.
    Result is that there is no Hamiltonian Cycle anymore.

    (0)---(1)---(2)
     |   /   \   |
     |  /     \  |
     | /       \ |
     |/         \|
    (3)         (4)
'''
graph = [[0, 1, 0, 1, 0],
         [1, 0, 1, 1, 1],
         [0, 1, 0, 0, 1],
         [1, 1, 0, 0, 0],
         [0, 1, 1, 0, 0]]
print(hamilton_cycle(graph,4)) #    []

```

    [0, 1, 2, 4, 3, 0]
    [3, 0, 1, 2, 4, 3]
    []
    
