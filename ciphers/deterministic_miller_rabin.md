# deterministic_miller_rabin 确定性米勒-拉宾素性检验

米勒-拉宾素性检验（Miller Rabin算法）

- 算法背景 <br>
米勒-拉宾素性检验（Miller Rabin算法），是一种素数判定法则，利用随机化算法判断一个数是合数还是可能是素数。卡内基梅隆大学的计算机系教授Gary Lee Miller首先提出了基于广义黎曼猜想的确定性算法，由于广义黎曼猜想并没有被证明，其后由以色列耶路撒冷希伯来大学的Michael O. Rabin教授作出修改，提出了不依赖于该假设的随机化算法。<br>

- 涉及知识点 <br>
  - 费马小定理 <br>
费马小定理就是说如果p是一个质数，而整数a不是p的倍数，则有$ a^{(p-1)}≡1（mod \ p）$。也可以写做$ a^p ≡ p (mod \ p) $.<br>

  - 二次探测 <br>
如果p是一个素数，那么使得$ x^2 ≡ 1 (mod \ p) $ 的 x的解只有两种可能，就是$ x = 1 $ 或者 $ x = p-1 $。<br>
证明如下：<br>
$x^2 ≡ 1 (mod \ p) $可以转换为 $x^2-1 = 0（mod \ p）$ ，然后就化为了$(x-1)(x+1) = 0 (mod p) $ , 因此p是整除$(x-1)(x+1)$, 用数学语言也就是说$p|(x-1)(x+1)$。因此$x = 1$ 或者 $x = p-1$。

- Miller-Rabin证明过程 <br>
假设n为奇素数，那么满足方程$ x^2 ≡ 1（mod \ n）$ 的解为x = 1 或者 x = n-1。<br>
又已知费马小定理 $ a^n-1 ≡1（mod n）$ <br>
$$ 
   a^{m*2^{t-1}} = 1 （mod \ n) \quad 
   \text 或者 \quad 
   a^{m*2^{t-1}} = n-1 （mod \ n)
$$
已知n为奇数，那么$ n-1 $ 一定为偶数，我们可以设 $n-1 = m * 2^t $。其中$m$一定为奇数，否则就可以并到 $2^t$ 里面。其实原本是$ n-1 = m * q^t $ 。为了计算就给q特殊化为2了。那么如何求m和t呢，上面其实也说了，m一定是奇数，所以只要给$n-1$不断地除2，直到$n-1$ 变为奇数，那么$m$就是这个奇数，设初始t为0，每次(n-1)除以2后，t都加一。这样t和m都求出来了。<br>

接下来我们从 $[1, n-1]$ 里面随机取一个a，容易得到$a^{n-1} = a^{m*2^t}$, 又由二次探索可知 <br>

不断的递归下去，不断的用二次探索定理，直到最后 $a^m = 1(mod \ n)$ 或者$ a^m = n-1(mod n) $，中间只要有一个不满足二次测试定理，那么这个数就一定是合数，否则就有$3/4$ 的概率为质数。这样其实为合数的几率也不小，有$25%$ 的大小。因此我们要多取几次$ a $进行计算，这样是合数的概率就变为了$（1/4）k$ 。最后其实也就是相当与肯定是质数了。<br>

- 算法流程 <br>
上面说了整体的证明，可能有一些人看到代码还是蒙，那我们就说一下算法的流程。<br>

1. 首先对于要判断的数$ n $，先判断是不是$2$，是就直接返回true。<br>
2. 判断是不是小于2或者为偶数，是就返回false。<br>
3. 令 $ n-1 = m*2^t $，求出 $m$ 和 $t$ 。<br>
4. 利用rand随机找一个a， a属于$[1， n-1]$ <br>
5. 令$ x = (a^m) \text % n $  <br>
6. 然后进行 $ t $ 次循环，为什么要循环 $ t $ 次呢，上面证明是从$ 2^t $倒着推到$ 2^0 $，我们写程序完全可以正着来，上面的x其实就是 <br>
 $$ a^{m*2^0}$$
7. 那么在循环中每次都进行 $ y =（x*x）\text %n $ ， $ x = y $ 的操作，最终会变为$a^{n-1}$，也就是 <br>
 $$ a^{m*2^t}$$ <br>
又因为x在循环时是一定小于n的，所以可以用二次探测定理 <br>
运算过程中如果$(x^2)\text %n = 1$, 也就是 $y = 1$，假如n是素数，那么$x == 1$ 或者 $ x == n-1 $，否则n就一定不是素数，直接返回false。
8. 整个循环结束后，程序运行到最后$x = a^{n-1}$, 根据费马小定理，如果x还是不等于1，那么肯定不是素数，直接返回false。
9. Miller-Rabin算法正确率为75%，所以要进行大约4~8次来提高正确率。



## 代码
[deterministic_miller_rabin.py]{..\src\ciphers\deterministic_miller_rabin.py}


```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块

"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

## 案例一： 

判定是否素数


```python
from ciphers.deterministic_miller_rabin import miller_rabin
    
"""
"""
n = 17
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')

'''
assert not miller_rabin(561)
assert miller_rabin(563)
'''
n = 561
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')

n = 563
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')

'''
assert not miller_rabin(838_201)
assert miller_rabin(838_207)
'''
n = 838_201
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')

n = 838_207
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')

'''
assert not miller_rabin(17_316_001)
assert miller_rabin(17_316_017)
'''
n = 17_316_001
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')

n = 17_316_017
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')

'''
assert not miller_rabin(3_078_386_641)
assert miller_rabin(3_078_386_653)
'''
n = 3_078_386_641
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')

n = 3_078_386_653
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')
'''
assert not miller_rabin(1_713_045_574_801)
assert miller_rabin(1_713_045_574_819)
'''
n = 1_713_045_574_801
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')

n = 1_713_045_574_819
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')

'''
assert not miller_rabin(2_779_799_728_307)
assert miller_rabin(2_779_799_728_327)
'''
n = 2_779_799_728_307
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')

n = 2_779_799_728_327
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')

'''
assert not miller_rabin(113_850_023_909_441)
assert miller_rabin(113_850_023_909_527)
'''
n = 113_850_023_909_441
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')

n = 113_850_023_909_527
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')

'''
assert not miller_rabin(1_275_041_018_848_804_351)
assert miller_rabin(1_275_041_018_848_804_391)
'''
n = 1_275_041_018_848_804_351
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')

n = 1_275_041_018_848_804_391
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')

'''
assert not miller_rabin(79_666_464_458_507_787_791_867)
assert miller_rabin(79_666_464_458_507_787_791_951)
'''
n = 79_666_464_458_507_787_791_867
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')

n = 79_666_464_458_507_787_791_951
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')

'''
assert not miller_rabin(552_840_677_446_647_897_660_333)
assert miller_rabin(552_840_677_446_647_897_660_359)
'''
n = 552_840_677_446_647_897_660_333
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')

n = 552_840_677_446_647_897_660_359
bPrime = miller_rabin(n)
print(f'{n} is Prime ? :{bPrime}')

```

    17 is Prime ? :True
    561 is Prime ? :False
    563 is Prime ? :True
    838201 is Prime ? :False
    838207 is Prime ? :True
    17316001 is Prime ? :False
    17316017 is Prime ? :True
    3078386641 is Prime ? :False
    3078386653 is Prime ? :True
    1713045574801 is Prime ? :False
    1713045574819 is Prime ? :True
    2779799728307 is Prime ? :False
    2779799728327 is Prime ? :True
    113850023909441 is Prime ? :False
    113850023909527 is Prime ? :True
    1275041018848804351 is Prime ? :False
    1275041018848804391 is Prime ? :True
    79666464458507787791867 is Prime ? :False
    79666464458507787791951 is Prime ? :True
    552840677446647897660333 is Prime ? :False
    552840677446647897660359 is Prime ? :True
    


```python

```
