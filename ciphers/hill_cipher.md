# hill_cipher 希尔密码

## 简介
希尔密码（Hill Cipher）是运用基本矩阵论原理的替换密码，由Lester S. Hill在1929年发明。<br>
每个字母当作 $ 26 $ 进制数字：$ A=0, B=1, C=2,\cdots $ 一串字母当成 $ n $ 维向量，跟一个 $ n \times n $ 的矩阵相乘，再将得出的结果模 $ 26 $ 。<br>
注意用作加密的矩阵（即密匙）在 必须是可逆的，否则就不可能解码。只有矩阵的行列式和 $ 26 $ 互质，才是可逆的。<br>
## 产生原因
随着科技的日新月异和人们对信用卡、计算机的依赖性的加强，密码学显得愈来愈重要。密码学是一门关于加密和解密、密文和明文的学科。若将原本的符号代换成另一种符号，即可称之为广义的密码。狭义的密码主要是为了保密，是一种防止窃文者得知内容而设的另一种符号文字，也是一般人所熟知的密码。<br>
使用信用卡、网络账号及密码、电子信箱、电子签名等都需要密码。为了方便记忆，许多人用生日、电话号码、门牌号码记做密码，但是这样安全性较差。<br>
为了使密码更加复杂，更难解密，产生了许多不同形式的密码。密码的函数特性是明文对密码为一对一或一对多的关系，即明文是密码的函数。传统密码中有一种叫移位法，移位法基本型态是加法加密系统 $ C=P+s{(mod \quad m)} $。一般来说，我们以 $ 1 $ 表示 $ A $ ，$ 2 $ 表示 $ B $，……，$ 25 $ 表示 $ Y $ ， $ 26 $ 表示 $ Z $，以此类推。由于 $ s=0 $ 时相当于未加密，而 $ 0≤s≤m-1 $ （$ s≥m $ 都可用 $ 0≤s≤m-1 $ 取代），因此，整个系统只有 $ m-1 $ 种变化。换言之，只要试过 $ m-1 $ 次，机密的信息就会泄漏出去。<br>
由此看来，日常生活中的密码和传统的密码的可靠性较差，我们有必要寻求一种容易将字母的自然频度隐蔽或均匀化，从而有利于统计分析的安全可靠的加密方法。希尔密码能基本满足这一要求。
## 原理
希尔加密算法的基本思想是，将 $ d $ 个明文字母通过线性变换将它们转换为 $ d $ 个密文字母。解密只要作一次逆变换就可以了，密钥就是变换矩阵本身。
希尔密码是多字母代换密码的一种。多字母代换密码可以利用矩阵变换方便地描述，有时又称为矩阵变换密码。<br>
令明文字母表为 $ Z $ ，若采用 $ L $ 个字母为单位进行代换，则多码代换是映射$ f：Z→Z $ 。<br>
若映射是线性的，则$ f $ 是线性变换，可以用$ Z $ 上的$ L×L $ 矩阵$ K $ 表示。<br>
若是满秩的，则变换为一一映射，且存在有逆变换 $ K $ 。<br>
将$ L $ 个字母的数字表示为$ Z $ 上的$ L $ 维矢量 $ m $ ，<br>
相应的密文矢量 $ c $，且 $ m \times K = c $ ，<br>
以 $ K^{-1} $ 作为解密矩阵，可由 $ c $ 恢复出相应的明文 $ c \times K^{-1} = m $。
在军事通讯中，常将字符（信息）与数字对应（为方便起见，我们将字符和数字按原有的顺序对应，事实上这种对应规则是极易被破解的）：
$$ a \quad b \quad c \quad d \quad e \cdots \quad x \quad y \quad z $$
$$ 1 \quad 2 \quad 3 \quad 4 \quad 5  \cdots \quad 24 \quad 25 \quad 26 $$
如信息“NOSLEEPPING”对应着一组编码 $ 14,15,19,12,5,5,16,16,9,14,7 $。<br>
但如果按这种方式直接传输出去，则很容易被敌方破译。
于是必须采取加密措施，即用一个约定的加密矩阵 $ K $ 乘以原信号 $ B $ ，传输信号为 $ C=K \times B $（加密），收到信号的一方再将信号还原（破译）为 $ B=K^{-1} \times C $ 。如果敌方不知道加密矩阵，则很难破译。<br>
## 加密
第一步，设定加密矩阵为 
 $
   \begin{bmatrix}
       1 & 1 & 2 \\
       -1 & 2 & 0 \\
       2 & 1 & 3 
   \end{bmatrix}
 $,<br> 

 即在希尔密码中设 $ q=26，L=3 $ ，<br>
选取满秩 $ 3×3 $ 阶可逆矩阵。
我们之所以取 $ 3×3 $ 可逆方阵，也是为了计算方便，相应的安全性就要低一些。<br>

第二步，将信息 $ 14，15，19，12，5，5，16，16，9，14，7 $ ,<br>

分为4个列矩阵：$ X_1=14 \quad 15 \quad 19，X_2=12 \quad 5 \quad 5，X_3=16 \quad 16 \quad 9，X_4=14 \quad 7 \quad 0 $ ，<br>
其中X中的 $ “0” $ 是虚设的，其目的是为了与列矩阵的行数一致。列矩阵的行数3和个数 $4$ 完全依赖于加密后的信息所对应的数字的多少和加密矩阵阶数决定。<br>

第三步，将信息加密。进行矩阵的乘法运算：<br>
$$ 
  Y_1=K \times X_1
   =\begin{bmatrix}
        1 & 1 & 2 \\
        -1 & 2 & 0 \\
        2 & 1 & 3 
     \end{bmatrix}
   \times
   \begin{bmatrix}
        14  \\
        15  \\
        19
    \end{bmatrix}
   =\begin{bmatrix}
        67  \\
        16  \\
        100
    \end{bmatrix}
$$
$$ 
  Y_2=K \times X_2
   =\begin{bmatrix}
        1 & 1 & 2 \\
        -1 & 2 & 0 \\
        2 & 1 & 3 
     \end{bmatrix}
   \times
   \begin{bmatrix}
        12  \\
        5  \\
        5
    \end{bmatrix}
   =\begin{bmatrix}
        27  \\
        -2  \\
        44
    \end{bmatrix}
$$
$$ 
  Y_3=K \times X_3
   =\begin{bmatrix}
        1 & 1 & 2 \\
        -1 & 2 & 0 \\
        2 & 1 & 3 
     \end{bmatrix}
   \times
   \begin{bmatrix}
        16  \\
        16  \\
        9
    \end{bmatrix}
   =\begin{bmatrix}
        50  \\
        16  \\
        75
    \end{bmatrix}
$$
$$ 
  Y_4=K \times X_4
   =\begin{bmatrix}
        1 & 1 & 2 \\
        -1 & 2 & 0 \\
        2 & 1 & 3 
     \end{bmatrix}
   \times
   \begin{bmatrix}
        14  \\
        7  \\
        0
    \end{bmatrix}
   =\begin{bmatrix}
        21  \\
        0  \\
        35
    \end{bmatrix}
$$
加密后的新码为 $ 67,16,100,27,-2,44,50,16,75,21,0 $ 。<br>

$ Y $中的 $ 35 $ 虽然是多余的信息，但要连同密码一起发给对方，对方在破解密码时要参与计算。
## 解密
第一步，求密匙矩阵K的逆矩阵。K可用Mathematica计算。即 
 $ K^{(-1)} =
   \begin{bmatrix}
       -6 & 1 & 4 \\
       -3 & 1 & 2 \\
       5 & -1 & -3 
   \end{bmatrix}
    $ .

第二步，再次进行矩阵乘法运算：
$$ 
  X_1=K^{(-1)} \times Y_1
   =\begin{bmatrix}
       -6 & 1 & 4 \\
       -3 & 1 & 2 \\
       5 & -1 & -3 
    \end{bmatrix}
   \times
   \begin{bmatrix}
        67  \\
        16  \\
        100
    \end{bmatrix}
   =\begin{bmatrix}
        14  \\
        15  \\
        19
    \end{bmatrix}
$$
$$ 
  X_2=K^{(-1)} \times Y_2
   =\begin{bmatrix}
       -6 & 1 & 4 \\
       -3 & 1 & 2 \\
       5 & -1 & -3 
    \end{bmatrix}
   \times
   \begin{bmatrix}
        27  \\
        -2  \\
        44
    \end{bmatrix}
  =   \begin{bmatrix}
        12  \\
        5  \\
        5
    \end{bmatrix}
$$
$$ 
  X_3=K^{(-1)} \times Y_3
   =\begin{bmatrix}
       -6 & 1 & 4 \\
       -3 & 1 & 2 \\
       5 & -1 & -3 
    \end{bmatrix}
   \times
   \begin{bmatrix}
        50  \\
        16  \\
        75
    \end{bmatrix}
  =\begin{bmatrix}
        16  \\
        16  \\
        9
    \end{bmatrix}
$$
$$ 
  X_4=K^{(-1)} \times Y_4
   =\begin{bmatrix}
       -6 & 1 & 4 \\
       -3 & 1 & 2 \\
       5 & -1 & -3 
    \end{bmatrix}
   \times
    \begin{bmatrix}
        21  \\
        0  \\
        35
    \end{bmatrix}
    =   \begin{bmatrix}
        14  \\
        7  \\
        0
    \end{bmatrix}
$$
   这样原来的信息编码为 $ 14,15,19,12,5,5,16,16,9,14,7 $。<br>

第三步，对照编码表，即可获得对方发来的信息内容为“NOSLEEPPING”。<br>

## 安全性分析
不难看出，希尔密码算法中有两个非常重要的条件。第一个条件是字符（信息）与数字对应表，当加密矩阵的阶数 $ n $（本文实例中的加密矩阵的阶数n=3）越大，破译的难度就会增大，此时计算量也大，我们可以借助有关数学软件如Mathematica提高运算效率。第二个条件是加密矩阵，如何定义、求解这个矩阵对于密码的加密和破译至关重要。  
从破译密码的角度来看，传统的密码有一个致命弱点，就是破译者可从统计出来的字符频率中找到规律，进而找出破译的突破口，尤其是在计算机技术高度发达的今天，破译的速度更快。希尔密码算法则完全克服了这一缺陷，它通过采用线性代数中的矩阵乘法运算和逆运算，能够较好地抵抗频率分析，很难被攻破。
希尔密码体系为破译者至少设置了三道关口，加大了破译难度。破译希尔密码的关键是猜测文字被转换成几维向量（列矩阵的行数）、所对应的字母表是怎样排列的，更为重要的是要设法获取加密矩阵A。要破解密码，向量的维数、字母的排列表和加密矩阵三者缺一不可。古今中外的谍报战中，敌对双方总是千方百计地获取破解对方密码的钥匙，但要想获取希尔密码的三把钥匙谈何容易。
世界上没有攻不破的密码，希尔密码也不例外。希尔密码算法的缺点在于线性变换的安全性很脆弱，易被攻击击破，黑客正是利用各种密码的弱点来向用户频频发起攻击的。尽管如此，希尔密码仍不失为一种简便高效的密码。


## 代码
[hill_cipher.py]{..\src\ciphers\hill_cipher.py}


## 范例一：求解示例中逆矩阵及加解密

```
numpy.linalg.inv() 函数计算矩阵的乘法逆矩阵。
```


```python
import numpy as np 

k_0 = np.array([[1,1,2],[-1,2,0],[2,1,3]]) 
k_1 = np.linalg.inv(k_0) # numpy.linalg.inv() 函数计算矩阵的乘法逆矩阵。
print (f"K_0 = : {k_0}")
print (f"k_1 = : {k_1}")
print (f"k_0 * k_1 = : {np.dot(k_0,k_1)}")
x1 =[14,15,19]
x2 = [12,5,5]
x3 = [16,16,9]
x4 = [14,7,0]
# numpy.matmul
# numpy.matmul 函数返回两个数组的矩阵乘积

y1 = np.dot(k_0,x1)
y2 = np.dot(k_0,x2)
y3 = np.dot(k_0,x3)
y4 = np.dot(k_0,x4)

print(f"x1: = {x1}")
print(f"x2: = {x2}")
print(f"x3: = {x3}")
print(f"x4: = {x4}")

print(f"y1 = Kx1 = k_0 * X1 :=  {y1} ")
print(f"y2 = Kx2 = k_0 * X2 :=  {y2} ")
print(f"y3 = Kx3 = k_0 * X3 :=  {y3} ")
print(f"y4 = Kx4 = K_0 * X4 :=  {y4} ")

print(f"x1 = k(-1) * y1 = k_1 * y1 = {np.dot(k_1,y1)}")
print(f"x2 = k(-1) * y2 = k_1 * y2 = {np.dot(k_1,y2)}")
print(f"x3 = k(-1) * y3 = k_1 * y3 = {np.dot(k_1,y3)}")
print(f"x4 = k(-1) * y4 = k_1 * y4 = {np.dot(k_1,y4)}")



```

    K_0 = : [[ 1  1  2]
     [-1  2  0]
     [ 2  1  3]]
    k_1 = : [[-6.  1.  4.]
     [-3.  1.  2.]
     [ 5. -1. -3.]]
    k_0 * k_1 = : [[ 1.00000000e+00  4.44089210e-16  8.88178420e-16]
     [ 0.00000000e+00  1.00000000e+00  0.00000000e+00]
     [-8.88178420e-16  2.22044605e-16  1.00000000e+00]]
    x1: = [14, 15, 19]
    x2: = [12, 5, 5]
    x3: = [16, 16, 9]
    x4: = [14, 7, 0]
    y1 = Kx1 = k_0 * X1 :=  [ 67  16 100] 
    y2 = Kx2 = k_0 * X2 :=  [27 -2 44] 
    y3 = Kx3 = k_0 * X3 :=  [50 16 75] 
    y4 = Kx4 = K_0 * X4 :=  [21  0 35] 
    x1 = k(-1) * y1 = k_1 * y1 = [14. 15. 19.]
    x2 = k(-1) * y2 = k_1 * y2 = [12.  5.  5.]
    x3 = k(-1) * y3 = k_1 * y3 = [16. 16.  9.]
    x4 = k(-1) * y4 = k_1 * y4 = [14.  7.  0.]
    


```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块

"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

## 基础公用
class HillCipher  约束
```
key_string = string.ascii_uppercase + string.digits
# This cipher takes alphanumerics into account
# i.e. a total of 36 characters

# take x and return x % len(key_string)
modulus = numpy.vectorize(lambda x: x % 36)

to_int = numpy.vectorize(lambda x: round(x))
    
```
class HillCipher:
```
   def __init__(self, encrypt_key: numpy.ndarray) -> None:
   def replace_letters(self, letter: str) -> int:
   def replace_digits(self, num: int) -> str:
   def encrypt(self, text: str) -> str:
   def make_decrypt_key(self) -> numpy.ndarray:
   def decrypt(self, text: str) -> str:
```  


```python
from ciphers.hill_cipher import HillCipher
import string
import numpy

"""
"""

hill_cipher = HillCipher(numpy.array([[2, 5], [1, 6]]))
'''
    def __init__(self, encrypt_key: numpy.ndarray) -> None:
        """
        encrypt_key is an NxN numpy array
        """
        self.encrypt_key = self.modulus(encrypt_key)  # mod36 calc's on the encrypt key
        self.check_determinant()  # validate the determinant of the encryption key
        self.break_key = encrypt_key.shape[0]
'''

```




    '\n    def __init__(self, encrypt_key: numpy.ndarray) -> None:\n        """\n        encrypt_key is an NxN numpy array\n        """\n        self.encrypt_key = self.modulus(encrypt_key)  # mod36 calc\'s on the encrypt key\n        self.check_determinant()  # validate the determinant of the encryption key\n        self.break_key = encrypt_key.shape[0]\n'



案例一：hill_cipher.replace_letters 方法


```python
"""
"""
print(hill_cipher.replace_letters('T')) #        19
print(hill_cipher.replace_letters('0')) #        26

```

    19
    26
    

## 案例二  replace_digits 方法


```python
print(hill_cipher.replace_digits(19))  #  'T'
print(hill_cipher.replace_digits(26))  # '0'
       
```

    T
    0
    

## 案例三： encrypt(self, text: str) -> str: 方法



```python
print(hill_cipher.encrypt('testing hill cipher')) #       'WHXYJOLM9C6XT085LL'
print(hill_cipher.encrypt('hello')) #        '85FF00'
```

    WHXYJOLM9C6XT085LL
    85FF00
    

## 案例四   def make_decrypt_key(self) -> numpy.ndarray:方法


```python
print(hill_cipher.make_decrypt_key())
'''
        array([[ 6, 25],
               [ 5, 26]])
'''
'''
hill_cipher = HillCipher(numpy.array([[6,25,1], [5,26]]))
print(hill_cipher.make_decrypt_key())

hill_cipher = HillCipher(numpy.array([[6,24,1], [13,16 ,10],[20,17,15]]))
print(hill_cipher.make_decrypt_key())

hill_cipher = HillCipher(numpy.array([[1,1,2], [-1,2 ,0],[2,1,3]]))
print(hill_cipher.make_decrypt_key())
'''


```

    [[ 6 25]
     [ 5 26]]
    




    '\nhill_cipher = HillCipher(numpy.array([[6,25,1], [5,26]]))\nprint(hill_cipher.make_decrypt_key())\n\nhill_cipher = HillCipher(numpy.array([[6,24,1], [13,16 ,10],[20,17,15]]))\nprint(hill_cipher.make_decrypt_key())\n\nhill_cipher = HillCipher(numpy.array([[1,1,2], [-1,2 ,0],[2,1,3]]))\nprint(hill_cipher.make_decrypt_key())\n'



## 案例五： decrypt(self, text: str) -> str 方法
    


```python
print(hill_cipher.decrypt('WHXYJOLM9C6XT085LL')) # 'TESTINGHILLCIPHERR'
print(hill_cipher.decrypt('85FF00')) #        'HELLOO'
```

    TESTINGHILLCIPHERR
    HELLOO
    


```python

```
