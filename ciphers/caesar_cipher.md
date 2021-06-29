# caesar_cipher  凯撒密码

## 概念

凯撒密码是一种简单的替代密码，根据苏维托尼乌斯的记载，凯撒密码是由罗马共和国独裁官盖乌斯·尤利乌斯·恺撒发明的，他曾用凯撒密码来加密重要的军事情报。<br>
作为一种替代加密算法，凯撒密码在如今看来，并非那么安全，它的加密方式只是简单的移位和替换，例如，如果明文移位1，则A被B替代，B将变为C，依此类推。<br>


如果知道偏移位密钥，对密文解密是很简单的，只需用移位密钥表替换回正常字母表字母即可
移位密钥表的规律很简单，不管偏移几位数，这些字母都移动到正常字母表的最后。<br>

如果不知道偏移位数密钥，怎么解密密文呢，方式其实也并不困难，因为凯撒密码只有25种偏移位数的可能性，所以，只需要计算出这25种结果，必然有一种结果是明文。<br>



## 算法
- encrypt 加密
```
def encrypt(input_string: str, key: int, alphabet: Optional[str] = None) -> str:
    """
    encrypt
    =======
    Encodes a given string with the caesar cipher and returns the encoded
    message

    Parameters:
    -----------
    *   input_string: the plain-text that needs to be encoded
    *   key: the number of letters to shift the message by

    Optional:
    *   alphabet (None): the alphabet used to encode the cipher, if not
        specified, the standard english alphabet with upper and lowercase
        letters is used

    Returns:
    *   A string containing the encoded cipher-text
```
- decrypt 解密
```
def decrypt(input_string: str, key: int, alphabet: Optional[str] = None) -> str:
```
- brute_force  暴力破解
```
def brute_force(input_string: str, alphabet: Optional[str] = None) -> Dict[int, str]:
    """
    brute_force
    ===========
    Returns all the possible combinations of keys and the decoded strings in the
    form of a dictionary

    Parameters:
    -----------
    *   input_string: the cipher-text that needs to be used during brute-force

    Optional:
    *   alphabet:  (None): the alphabet used to decode the cipher, if not
        specified, the standard english alphabet with upper and lowercase
        letters is used
```
## 代码
[caesar_cipher.py]{..\src\ciphers\caesar_cipher.py}


```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块

"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

## 案例一： 
encrypt 加密


```python
from ciphers.caesar_cipher import encrypt,decrypt,brute_force
"""
    
"""

'''
encrypt('The quick brown fox jumps over the lazy dog', 8)
    'bpm yCqks jzwEv nwF rCuxA wDmz Bpm tiHG lwo'
'''
input_string = 'The quick brown fox jumps over the lazy dog'
key= 8+52
result = encrypt(input_string,key)

print(f'input_string:{input_string}' )
print(f'key：{key}' )
print(f'encrypt result:{result}' )
'''
encrypt('A very large key', 8000)
's nWjq dSjYW cWq'
'''

input_string = 'A very large key'
key= 8000
result = encrypt(input_string,key)

print(f'input_string:{input_string}' )
print(f'key：{key}' )
print(f'encrypt result:{result}' )

'''
encrypt('a lowercase alphabet', 5, 'abcdefghijklmnopqrstuvwxyz')
    'f qtbjwhfxj fqumfgjy'
'''

input_string = 'a lowercase alphabet'
key= 5
alphabet ='abcdefghijklmnopqrstuvwxyz'
result = encrypt(input_string,key,alphabet)
print(f'input_string:{input_string}' )
print(f'key：{key}' )
print(f'encrypt result:{result}' )

```

    input_string:The quick brown fox jumps over the lazy dog
    key：60
    encrypt result:bpm yCqks jzwEv nwF rCuxA wDmz Bpm tiHG lwo
    input_string:A very large key
    key：8000
    encrypt result:s nWjq dSjYW cWq
    input_string:a lowercase alphabet
    key：5
    encrypt result:f qtbjwhfxj fqumfgjy
    

## 案例二： 
decrypt 解密


```python
from ciphers.caesar_cipher import encrypt,decrypt,brute_force
"""
    
"""
'''
>>> decrypt('bpm yCqks jzwEv nwF rCuxA wDmz Bpm tiHG lwo', 8)
    'The quick brown fox jumps over the lazy dog'
>>> decrypt('s nWjq dSjYW cWq', 8000)
    'A very large key'
>>> decrypt('f qtbjwhfxj fqumfgjy', 5, 'abcdefghijklmnopqrstuvwxyz')
    'a lowercase alphabet'
'''

print(decrypt('bpm yCqks jzwEv nwF rCuxA wDmz Bpm tiHG lwo', 8))
print(decrypt('s nWjq dSjYW cWq', 8000))
print(decrypt('f qtbjwhfxj fqumfgjy', 5, 'abcdefghijklmnopqrstuvwxyz'))

```

    The quick brown fox jumps over the lazy dog
    A very large key
    a lowercase alphabet
    

## 案例三：
brute_force 暴力破解
```
brute_force(input_string: str, alphabet: Optional[str] = None) -> Dict[int, str]:
```



```python
from ciphers.caesar_cipher import encrypt,decrypt,brute_force
"""
"""
'''
>>> brute_force("jFyuMy xIH'N vLONy zILwy Gy!")[20]
    "Please don't brute force me!"
'''
s = brute_force("jFyuMy xIH'N vLONy zILwy Gy!")
print(type(s))
print(s)
print(s[20])
```

    <class 'dict'>
    {1: "iExtLx wHG'M uKNMx yHKvx Fx!", 2: "hDwsKw vGF'L tJMLw xGJuw Ew!", 3: "gCvrJv uFE'K sILKv wFItv Dv!", 4: "fBuqIu tED'J rHKJu vEHsu Cu!", 5: "eAtpHt sDC'I qGJIt uDGrt Bt!", 6: "dzsoGs rCB'H pFIHs tCFqs As!", 7: "cyrnFr qBA'G oEHGr sBEpr zr!", 8: "bxqmEq pAz'F nDGFq rADoq yq!", 9: "awplDp ozy'E mCFEp qzCnp xp!", 10: "ZvokCo nyx'D lBEDo pyBmo wo!", 11: "YunjBn mxw'C kADCn oxAln vn!", 12: "XtmiAm lwv'B jzCBm nwzkm um!", 13: "Wslhzl kvu'A iyBAl mvyjl tl!", 14: "Vrkgyk jut'z hxAzk luxik sk!", 15: "Uqjfxj its'y gwzyj ktwhj rj!", 16: "Tpiewi hsr'x fvyxi jsvgi qi!", 17: "Sohdvh grq'w euxwh irufh ph!", 18: "Rngcug fqp'v dtwvg hqteg og!", 19: "Qmfbtf epo'u csvuf gpsdf nf!", 20: "Please don't brute force me!", 21: "OkdZrd cnm's aqtsd enqbd ld!", 22: "NjcYqc bml'r Zpsrc dmpac kc!", 23: "MibXpb alk'q Yorqb cloZb jb!", 24: "LhaWoa Zkj'p Xnqpa bknYa ia!", 25: "KgZVnZ Yji'o WmpoZ ajmXZ hZ!", 26: "JfYUmY Xih'n VlonY ZilWY gY!", 27: "IeXTlX Whg'm UknmX YhkVX fX!", 28: "HdWSkW Vgf'l TjmlW XgjUW eW!", 29: "GcVRjV Ufe'k SilkV WfiTV dV!", 30: "FbUQiU Ted'j RhkjU VehSU cU!", 31: "EaTPhT Sdc'i QgjiT UdgRT bT!", 32: "DZSOgS Rcb'h PfihS TcfQS aS!", 33: "CYRNfR Qba'g OehgR SbePR ZR!", 34: "BXQMeQ PaZ'f NdgfQ RadOQ YQ!", 35: "AWPLdP OZY'e McfeP QZcNP XP!", 36: "zVOKcO NYX'd LbedO PYbMO WO!", 37: "yUNJbN MXW'c KadcN OXaLN VN!", 38: "xTMIaM LWV'b JZcbM NWZKM UM!", 39: "wSLHZL KVU'a IYbaL MVYJL TL!", 40: "vRKGYK JUT'Z HXaZK LUXIK SK!", 41: "uQJFXJ ITS'Y GWZYJ KTWHJ RJ!", 42: "tPIEWI HSR'X FVYXI JSVGI QI!", 43: "sOHDVH GRQ'W EUXWH IRUFH PH!", 44: "rNGCUG FQP'V DTWVG HQTEG OG!", 45: "qMFBTF EPO'U CSVUF GPSDF NF!", 46: "pLEASE DON'T BRUTE FORCE ME!", 47: "oKDzRD CNM'S AQTSD ENQBD LD!", 48: "nJCyQC BML'R zPSRC DMPAC KC!", 49: "mIBxPB ALK'Q yORQB CLOzB JB!", 50: "lHAwOA zKJ'P xNQPA BKNyA IA!", 51: "kGzvNz yJI'O wMPOz AJMxz Hz!", 52: "jFyuMy xIH'N vLONy zILwy Gy!"}
    Please don't brute force me!
    


```python

```
