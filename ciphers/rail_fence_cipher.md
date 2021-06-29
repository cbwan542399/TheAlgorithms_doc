# Rail_fence_cipher 栅栏密码

所谓栅栏密码，就是把要加密的明文分成N个一组，然后把每组的第1个字连起来，形成一段无规律的话。 不过栅栏密码本身有一个潜规则，就是组成栅栏的字母一般不会太多。（一般不超过30个，也就是一、两句话）<br>


## 加 密 原 理
当加密为两组时，把将要传递的信息中的字母交替排成上下两行。<br>
再将下面一行字母排在上面一行的后边，从而形成一段密码。<br>
例如：<br>
- 加密明文。<br>
ALL LIFE IS A GAME OF LUCK <br>
当加密为两组时，将句子从上往下交替写成两行，也就是第一 三 五等奇数个字母作为第一组，第二四六作为第二组。<br>
ALIESGMOLC <br>
LLFIAAEFUK <br>
再将第一组放在第二组前 <br>
ALIESGMOLCLLFIAAEFUK <br>
加密完成。<br>

在实际应用当中可以将该加密方式分成更多组，或者与其他加密方式组合使用。<br>

- 解 密 <br>
第一步将密文按组分开。当密文字母个数为奇数个时，第一组比第二组多一个。<br>
第二步自上向下读出。<br>
举例：<br>
密文：TMKECDYONOAEAHACUT <br>
密文字母个数为18，第一组9个字母，第二组9个字母。<br>
TMKECDYON <br>
OAEAHACUT <br>
自上向下读出 <br>
TOMAKEEACHDAYCOUNT <br>
得明文 <br>
TO MAKE EACH DAY COUNT<br>
练 习
密文: TMROIAOHRAOORWSNTEDY








## 代码
[rail_fence_cipher.py]{..\src\ciphers\rail_fence_cipher.py}



```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块

"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

## 案例一：
- encrypt <br>
通过放置字符串的每个字符来打乱字符串的字符  
在一个锯齿形的网格中(高度取决于键)  
从左到右阅读。  
```
encrypt(
    input_string: str,
    key: int)
    -> str:
```
- decrypt <br>
根据密钥生成模板并将其填充  
输入字符串的字符，然后读入  
一个锯齿形的形成。  
```
decrypt(
    input_string: str,
    key: int) 
    -> str:
```
- bruteforce
  通过猜测每个密钥使用解密函数
```
bruteforce(
    input_string: str) 
    -> dict[int, str]
```


```python
from ciphers.rail_fence_cipher import encrypt,decrypt
# ,bruteforce
"""
"""
print(encrypt("Hello World", 4))   #  'HWe olordll'

print(decrypt("HWe olordll", 4))   #  'Hello World'

"""
 Uses decrypt function by guessing every key
"""

# print(bruteforce("HWe olordll")[4]) #    'Hello World'




    
```

    HWe olordll
    Hello World
    




    '\n Uses decrypt function by guessing every key\n'




```python

```


```python

```
