# minimax  Minimax算法,极小化极大算法

参考：https://baike.baidu.com/item/%E6%9E%81%E5%B0%8F%E5%8C%96%E6%9E%81%E5%A4%A7%E7%AE%97%E6%B3%95/1351828?fromtitle=Minimax%E7%AE%97%E6%B3%95&fromid=3876233&fr=aladdin

Minimax算法（亦称 MinMax or MM）又名极小化极大算法，是一种找出失败的最大可能性中的最小值的算法

- 介绍 <br>
Minimax算法常用于棋类等由两方较量的游戏和程序。该算法是一个零总和算法，即一方要在可选的选项中选择将其优势最大化的选择，另一方则选择令对手优势最小化的方法 。而开始的时候总和为0。很多棋类游戏可以采取此算法，例如井字棋（tic-tac-toe）。
- 基本算法思想 <br>
极小化极大（minimax）算法顾名思义，就是让最大得情况最小，这里的最大一般是指最差的情况，比如游戏中最不利的情况。
该算法需要满足零和博弈，初略的解释就是若有两个玩家进行游戏，如果其中一方得到利益那么另一方就会失去利益，游戏利益的总和为0（某些情况下为常数）。
因此，零和的约束条件也使得该算法在很多游戏中图体现出很好的效果，比如大多数的棋类游戏。
其实说白了，这个算法就是一个树形结构的递归算法，每个节点的孩子和父节点都是对方玩家，所有的节点被分为极大值（我方）节点和极小值（对方）节点。
- 算法优化 <br>
  - α-β剪枝算法 <br>
在上述的极大极小算法中，MIN和MAX过程将所有的可能性省搜索树，然后再从端点的估计值倒推计算，这样的效率非常低下。而α-β算法的引入可以提高运算效率，对一些非必要的估计值进行舍弃。其策略是进行深度优先搜索，当生成结点到达规定深度时，立即进行静态估计，一旦某一个非端点的节点可以确定倒推值的时候立即赋值，节省下其他分支拓展到节点的开销。<br>
  - 剪枝规则：<br>
（1）α剪枝，任一极小层节点的β值不大于他任一前驱极大值层节点的α值，即α（前驱层）≥β（后继层），则可以终止该极小层中这个MIN节点以下的搜索过程。这个MIN节点的倒推值确定为这个β值。<br>
（2）β剪枝，任一极大层节点的α值不小于它任一前驱极小值层节点的β值，即β（前驱层）≤α（后继层），则可以终止该极大值层中这个MAX节点以下的搜索过程。这个MAX节点的倒推值确定为这个α值。<br>


## 代码
[minimax.py]{..\src\backtracking\minimax.py}




```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块

"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

## 案例一： 

nodeIndex是当前节点在scores[]中的索引。  
如果move是maximizer返回true否则返回false  
游戏树的叶子存储在scores中[]  
高度是游戏树的最大高度  
```
def minimax(
    depth: int, 
    node_index: int, 
    is_max: bool, 
    scores: List[int], 
    height: float
) -> int:
```


```python
from backtracking.minimax import minimax
import math
"""
"""
depth, node_index,is_max = 0,0,True
scores = [90, 23, 6, 33, 21, 65, 123, 34423]
height = math.log(len(scores), 2)
print(f'height :{height}')
print("Optimal value : ", end="")
# print(minimax(0, 0, True, scores, height))
print(minimax(depth, node_index, is_max, scores, height))

    

```

    height :3.0
    Optimal value : 65
    


```python

```
