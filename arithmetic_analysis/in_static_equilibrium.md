##   in_static_equilibrium 处于静态平衡

### 点集与向量集的区别及联系

- 1. 标积/内积/数量积/点积 <br>

  设：  $ a = {a_1,a_2,\cdots,a_n} \\
          b = {b_1,b_2,\cdots,b_n} 
        $ 时
  $$ 
    \vec{a} \cdot \vec{b}  
    = a_1 \times b_1 + a_2 \times b_2 +\cdots +a_n \times b_n 
    = \sum_{i=1}^{n} a_i  \times b_i
  $$

几何意义 ：向量$ \vec{a} $在向量 $ \vec{b} $方向上的投影与向量$ \vec{b} $的模的乘积 <br>
运算结果： 标量（常用于物理）/数量（常用于数学）

- 2. 向量积，数学中又称外积、叉积，物理中称矢积、叉乘，是一种在向量空间中向量的二元运算。
运算式： $ \vec{a} \times \vec{b} =|a||b|\times \cos (θ) $  <br>
与点积不同，它的运算结果是一个向量而不是一个标量。并且两个向量的叉积与这两个向量和垂直。其应用也十分广泛，通常应用于物理学光学和计算机图形学中。
表示方法
两个向量$ \vec{a} $ 和 $ \vec{b} $ 的叉积写作 $ \vec{a} \times \vec{b} $
（有时也被写成 $ \vec{a} \text{∧} \vec{b} $ 避免和字母x混淆）。
定义
向量积可以被定义为：|a×b|=|a||b|sin<a，b>。
模长：（在这里θ表示两向量之间的夹角（共起点的前提下）（0°≤θ≤180°），它位于这两个矢量所定义的平面上。）
方向：a向量与b向量的向量积的方向与这两个向量所在平面垂直，且遵守右手定则。（一个简单的确定满足“右手定则”的结果向量的方向的方法是这样的：若坐标系是满足右手定则的，当右手的四指从a以不超过180度的转角转向b时，竖起的大拇指指向是c的方向。）
也可以这样定义（等效）：
向量积|c|=|a×b|=|a||b|sin<a，b>
即c的长度在数值上等于以a，b，夹角为θ组成的平行四边形的面积。
而c的方向垂直于a与b所决定的平面，c的指向按右手定则从a转向b来确定。

#### 几何意义及其运用
叉积的长度|a×b|可以解释成这两个叉乘向量a，b共起点时，所构成平行四边形的面积。据此有：混合积[abc]=（a×b）·c可以得到以a，b，c为棱的平行六面体的体积。

#### 与数量积的区别
注：向量积≠向量的积（向量的积一般指点乘）
一定要清晰地区分开向量积（矢积）与数量积（标积）。

### 算法
- 极坐标与直角坐标的转化
$$ 
   \begin{cases}
      x = \rho \times \cos(θ) \\
      y = \rho \times \sin(θ) 
   \end{cases}
$$

```
def polar_force(
    magnitude: float,         # $ \rho $ 值
               angle: float,  # 角度 θ 
               radian_mode: bool = False  # 是否弧度，
) -> List[float]:   # （x,y)


- 向量的叉积
```
numpy.cross
numpy.cross(a, b, axisa=-1, axisb=-1, axisc=-1, axis=None)  
返回两个（数组）向量的叉积。
```
- 是否静态平衡
```
def in_static_equilibrium(
    forces: ndarray, 
    location: ndarray, 
    eps: float = 10 ** -1
) -> bool:

# summation of moments is zero
moments: ndarray = cross(location, forces)
sum_moments: float = sum(moments)
return abs(sum_moments) < eps

```

### 代码
in_static_equilibrium.py{..\src\arithmetic_analysis\in_static_equilibrium.py}

　　




```python
"""
Prepare
   1 . sys.path 中增加 TheAlgorithms\src 子模块
"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')
```

案例一：极坐标与直角坐标的转化
```
 Resolves force along rectangular components.
    (force, angle) => (force_x, force_y)
    >>> polar_force(10, 45)
    [7.0710678118654755, 7.071067811865475]
    >>> polar_force(10, 3.14, radian_mode=True)
    [-9.999987317275394, 0.01592652916486828]
```


```python
from arithmetic_analysis.in_static_equilibrium import polar_force
"""
"""
print(polar_force(10, 45))  # [7.0710678118654755, 7.071067811865475]
print(polar_force(10, 3.14, radian_mode=True)) #[-9.999987317275394, 0.01592652916486828]
```

    [7.0710678118654755, 7.0710678118654755]
    [-9.999987317275394, 0.01592652916486828]
    

## 案例二：检查系统平衡状态
Check if a system is in equilibrium.
    It takes two numpy.array objects.
```
    forces ==>  [
                        [force1_x, force1_y],
                        [force2_x, force2_y],
                        ....]
    location ==>  [
                        [x1, y1],
                        [x2, y2],
                        ....]
```


```python
from arithmetic_analysis.in_static_equilibrium import in_static_equilibrium
from numpy import array
"""
"""
force = array([[1, 1], [-1, 2]])
location = array([[1, 0], [10, 0]])
print(in_static_equilibrium(force, location))   #False
```

    False
    


```python

```
