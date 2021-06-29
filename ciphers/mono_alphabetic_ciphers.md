# mono_alphabetic_ciphers 单字母密码

定义
在网络上传送报文的过程中使用的一种简单的加密机制。它把明文中的一个字母总是用另一个字母替换

## 代码
[mono_alphabetic_ciphers.py]{..\src\ciphers\mono_alphabetic_ciphers.py}



```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块

"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

## 案例一：

约束，设置只处理26个大写字母
```
LETTERS = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
```



```python
from ciphers.mono_alphabetic_ciphers import encrypt_message,decrypt_message
"""
"""

key = "QWERTYUIOPASDFGHJKLZXCVBNM"
message = "Hello World"
cipper  = encrypt_message(key, message)
print(f"Using the key : {key}")
print(f"the message is: {message},the encrypt_message is: {cipper}")
print(f"the crypt message is: {cipper},the decrypt_message is: {decrypt_message(key, cipper)}")
    

```

    Using the key : QWERTYUIOPASDFGHJKLZXCVBNM
    the message is: Hello World,the encrypt_message is: Pcssi Bidsm
    the crypt message is: Pcssi Bidsm,the decrypt_message is: Hello World
    
