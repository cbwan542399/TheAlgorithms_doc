# atbash  埃特巴什码 

## 概念

埃特巴什码（Atbash Cipher）是一个系统：最后一个字母代表第一个字母，倒数第二个字母代表第二个字母。
在罗马字母表中，它是这样出现的：
```
常文：A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
密文：Z Y X W V U T S R Q P O N M L K J I H G F E D C B A
```
这种密码是由熊斐特博士发现的。熊斐特博士为库姆兰《死海古卷》的最初研究者之一，他在《圣经》历史研究方面最有名气的著作是《逾越节的阴谋》。他运用这种密码来研究别人利用其他方法不能破解的那些经文。这种密码被运用在公元1世纪的艾赛尼/萨多吉/拿撒勒教派的经文中，用以隐藏姓名。其实早在公元前500年，它就被抄经人用来写作《耶利米书》耶利米是活动在公元前627-前586年间的犹太先知，圣经旧约书中有许多关于他的记载。在他离世前，犹太领土已被巴比伦人占领。。它也是希伯来文所用的数种密码系统之一。
## 算法
- atbash_slow(sequence: str) -> str
- atbash_slow(sequence: str) -> str
  
## 代码
[attbash.py]{..\src\ciphers\attbash.py}


```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块

"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

## 案例一： 
 对明文进行加密 <br>
 对密文进行解密 <br>
 其中：对密文进行加密得到明文 <br>


```python
from ciphers.atbash import atbash_slow,atbash
"""
    >>> atbash_slow("ABCDEFG")
    'ZYXWVUT'

    >>> atbash_slow("aW;;123BX")
    'zD;;123YC'

    >>> atbash("ABCDEFG")
    'ZYXWVUT'

    >>> atbash("aW;;123BX")
    'zD;;123YC'
"""
s = "ABCDEFG"
s_atbash_slow = atbash_slow(s)
print ("s:=",s)
print ("atbash_slow(s):",s_atbash_slow)
print ("double atbash_slow(s):",atbash_slow(s_atbash_slow)) 


s = "aW;;123BX"
s_atbash_slow = atbash_slow(s)
print ("s:=",s)
print ("atbash_slow(s):",s_atbash_slow)
print ("double atbash_slow(s):",atbash_slow(s_atbash_slow))

s = "ABCDEFG"
s_atbash = atbash(s)
print ("s:=",s)
print ("atbash(s):",s_atbash)
print ("double atbash(s):",atbash(s_atbash))


s = "aW;;123BX"
s_atbash = atbash(s)
print ("s:=",s)
print ("atbash(s):",s_atbash)
print ("double atbash(s):",atbash(s_atbash))

```

    s:= ABCDEFG
    atbash_slow(s): ZYXWVUT
    double atbash_slow(s): ABCDEFG
    s:= aW;;123BX
    atbash_slow(s): zD;;123YC
    double atbash_slow(s): aW;;123BX
    s:= ABCDEFG
    atbash(s): ZYXWVUT
    double atbash(s): ABCDEFG
    s:= aW;;123BX
    atbash(s): zD;;123YC
    double atbash(s): aW;;123BX
    


```python

```
