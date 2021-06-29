# diffie公钥私钥机制依素数简化实现

- 1、依据一个素数,寻找一个另一可用素数
- 2、分别设置 Alice 、Bob 的公钥、私钥
- 3、Alice 、Bob 分别利用 对端公钥、自身私钥、及可用素数 形成 各自的 密钥 key 
- 4、检查 key 的一致性 （应该是相同的）

## 代码
[diffie.py]{..\src\ciphers\diffie.py}



```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块

"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

## 案例一：依据一个素数,寻找一个另一可用素数
 
```
def find_primitive(n: int) -> Optional[int]:
    for r in range(1, n):
        li = []
        for x in range(n - 1):
            val = pow(r, x, n)  
            # pow(x, y[, z]), 函数是计算x的y次方，如果z在存在，则再对结果进行取模，
            # 其结果等效于pow(x,y) %z
            if val in li:
                break
            li.append(val)
        else:
            return r
    return None
```


```python
from ciphers.diffie import find_primitive
"""
"""
print(find_primitive(7))
print(find_primitive(563))
# print(find_primitive(838207))

```

    3
    2
    

## 案例二：
```
- 1、依据一个素数,寻找一个另一可用素数
```
- 2、分别设置 Alice 、Bob 的公钥、私钥
- 3、Alice 、Bob 分别利用 对端公钥、自身私钥、及可用素数 形成 各自的 密钥 key
- 4、检查 key 的一致性 （应该是相同的）


```python
  # q = int(input("Enter a prime number q: "))
  q = 563
  a = find_primitive(q)
  if a is None:
      print(f"Cannot find the primitive for the value: {a!r}")
  else:
      # alice_private = int(input("Enter private key of A: "))
      alice_private = 89
      alice_public = pow(a, alice_private, q)
      # bob_private = int(input("Enter private key of B: "))
      bob_private = 23
      bob_public = pow(a, bob_private, q)

      alice_secret = pow(bob_public, alice_private, q)
      bob_secret = pow(alice_public, bob_private, q)

      print("The key value generated by Alice is: ", alice_secret)
      print("The key value generated by Bob is: ", bob_secret)
      print(f"The key generated by Alice,Bob is equal ?: {alice_secret == bob_secret} ")


```

    The key value generated by Alice is:  350
    The key value generated by Bob is:  350
    The key generated by Alice,Bob is equal ?: True 
    


```python

```