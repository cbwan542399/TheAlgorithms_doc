# affine_cipher  仿射加密法

## 概念
仿射加密法与单码加密法没什么不同，因为明文的每个字母分别只映射到一个密文字母。仿射密码的加密算法就是一个线性变换，即对任意的明文字符x，对应的密文字符为$y\equiv ax+ b (mod(26))  $ ，其中，$a,b∈Z26$，且要求$gcd(a,26)$=1,函数e(x)称为仿射加密函数。

## 算法
- SYMBOLS :符号表
```
SYMBOLS = (
    r""" !"#$%&'()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ[\]^_`"""
    r"""abcdefghijklmnopqrstuvwxyz{|}~"""
)
```
- encrypt_message(key: int, message: str) -> str
  根据key 值，加密
- decrypt_message(key: int, message: str) -> str
  根据key 值，解密

## 代码
[affine_cipher.py]{..\src\ciphers\affine_cipher.py}


```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块

"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

## 案例一： 
 对明文进行加密
 对密文进行解密


```python
from ciphers.affine_cipher import encrypt_message,decrypt_message
"""
>>> encrypt_message(4545, 'The affine cipher is a type of monoalphabetic '
                        'substitution cipher.')
    'VL}p MM{I}p~{HL}Gp{vp pFsH}pxMpyxIx JHL O}F{~pvuOvF{FuF{xIp~{HL}Gi'
>>> decrypt_message(4545, 'VL}p MM{I}p~{HL}Gp{vp pFsH}pxMpyxIx JHL O}F{~pvuOvF{FuF'
                      '{xIp~{HL}Gi')
  'The affine cipher is a type of monoalphabetic substitution cipher.'
"""
sPlain_msg='''The affine cipher is a type of monoalphabetic \\                            substitution cipher.'''

sCipher_msg = ''
key = 4545
sCipher_msg = encrypt_message(key,sPlain_msg)
print("密文:"+sCipher_msg)
print("明文:"+decrypt_message(key,sCipher_msg))


```

    密文:VL}p MM{I}p~{HL}Gp{vp pFsH}pxMpyxIx JHL O}F{~pRppppppppppppppppppppppppppppvuOvF{FuF{xIp~{HL}Gi
    明文:The affine cipher is a type of monoalphabetic \                            substitution cipher.
    


```python

```
