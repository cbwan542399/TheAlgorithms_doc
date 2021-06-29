# mixed_keyword_cypher 混杂关键字加密

mixed_keyword_cypher 混杂关键字加密，即利用一个关键字，代替其顺序的 A,B,C,..., 再取A,B,C 顺序未替代的部分进行转换。
如： key:hello
其 A,B,C,...,X,Y,Z 26个字母替代顺序为
```
    H E L O
    A B C D
    F G I J
    K M N P
    Q R S T
    U V W X
    Y Z
    and map vertically
```
## 代码
[mixed_keyword_cypher.py]{..\src\ciphers\mixed_keyword_cypher.py}



```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块

"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

## 案例一：



```python
def mixed_keyword(key: str = "college", pt: str = "UNIVERSITY") -> str:
    """

    For key:hello

    H E L O
    A B C D
    F G I J
    K M N P
    Q R S T
    U V W X
    Y Z
    and map vertically

    >>> mixed_keyword("college", "UNIVERSITY")  # doctest: +NORMALIZE_WHITESPACE
    {'A': 'C', 'B': 'A', 'C': 'I', 'D': 'P', 'E': 'U', 'F': 'Z', 'G': 'O', 'H': 'B',
     'I': 'J', 'J': 'Q', 'K': 'V', 'L': 'L', 'M': 'D', 'N': 'K', 'O': 'R', 'P': 'W',
     'Q': 'E', 'R': 'F', 'S': 'M', 'T': 'S', 'U': 'X', 'V': 'G', 'W': 'H', 'X': 'N',
     'Y': 'T', 'Z': 'Y'}
    'XKJGUFMJST'
    """
    key = key.upper()
    pt = pt.upper()
    temp = []
    for i in key:
        if i not in temp:
            temp.append(i)
    len_temp = len(temp)
    print(f"temp:{temp}")
    alpha = []
    modalpha = []
    for j in range(65, 91):
        t = chr(j)
        alpha.append(t)
        if t not in temp:
            temp.append(t)
    # print(temp)
    print(f"temp:{temp}")
    r = int(26 / 4)
    # print(r)
    print(f"r:{r}")
    k = 0
    for _ in range(r):
        s = []
        for j in range(len_temp):
            s.append(temp[k])
            if not (k < 25):
                break
            k += 1
        modalpha.append(s)
    print(f"modalpha:{modalpha}")
    # print(modalpha)
    d = {}
    j = 0
    k = 0
    for j in range(len_temp):
        for m in modalpha:
            if not (len(m) - 1 >= j):
                break
            d[alpha[k]] = m[j]
            if not k < 25:
                break
            k += 1
    # print(d)
    print(f"d:{d}")
    cypher = ""
    for i in pt:
        cypher += d[i]
    return cypher


print(mixed_keyword("college", "UNIVERSITY"))
```

    temp:['C', 'O', 'L', 'E', 'G']
    temp:['C', 'O', 'L', 'E', 'G', 'A', 'B', 'D', 'F', 'H', 'I', 'J', 'K', 'M', 'N', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z']
    r:6
    modalpha:[['C', 'O', 'L', 'E', 'G'], ['A', 'B', 'D', 'F', 'H'], ['I', 'J', 'K', 'M', 'N'], ['P', 'Q', 'R', 'S', 'T'], ['U', 'V', 'W', 'X', 'Y'], ['Z']]
    d:{'A': 'C', 'B': 'A', 'C': 'I', 'D': 'P', 'E': 'U', 'F': 'Z', 'G': 'O', 'H': 'B', 'I': 'J', 'J': 'Q', 'K': 'V', 'L': 'L', 'M': 'D', 'N': 'K', 'O': 'R', 'P': 'W', 'Q': 'E', 'R': 'F', 'S': 'M', 'T': 'S', 'U': 'X', 'V': 'G', 'W': 'H', 'X': 'N', 'Y': 'T', 'Z': 'Y'}
    XKJGUFMJST
    


```python

```
