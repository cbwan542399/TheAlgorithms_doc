# bit_manipulation 二进制位操作

- binary_and(a: int, b: int) -> str <br>
  整数二进制 and 操作 <br>
  对两个整形参数，先转换成二进制，对2个二进制数据进行 and 与操作，返回 二进制字符制 <br>
- binary_or(a: int, b: int) -> str <br>
   or 或 操作
- binary_xor(a: int, b: int) -> str <br>
   xor 异或 操作


- binary_count_setbits(a: int) -> int <br>
   转换二进制数，统计“1” 的数量 <br>
   其算法为： bin(a).count("1")

- binary_count_trailing_zeros(a: int) -> int <br>
    统计属随“0” 数量 <br>
    其算法为：int(log2(a & -a))
- binary_shift
    二进制移位，包含：
    - logical_left_shift(number: int, shift_amount: int) -> str <br>
      将 number: int 转换二进制后，左移 shift_amount: int 位，返回 二进制字符串
    - logical_right_shift(number: int, shift_amount: int) -> str <br>
      将 number: int 转换二进制后，左移 shift_amount: int 位，返回 二进制字符串
    
- twos_complement(number: int) -> str <br>
    二进制补码  <br>
    原码, 反码, 补码的基础概念和计算方法 <br>
    1. 原码 <br>
      原码就是符号位加上真值的绝对值, 即用第一位表示符号, 其余位表示值. 比如如果是8位二进制: <br>
       ```
       [+1]原 = 0000 0001
       [-1]原 = 1000 0001
       ```
    2. 反码 <br>
       反码的表示方法是: <br>
       正数的反码是其本身 <br>
       负数的反码是在其原码的基础上, 符号位不变，其余各个位取反. <br>
       ```
       [+1] = [00000001]原 = [00000001]反
       [-1] = [10000001]原 = [11111110]反
      ```
    3. 补码 <br>
       补码的表示方法是: <br>
       正数的补码就是其本身 <br>
       负数的补码是在其原码的基础上, 符号位不变, 其余各位取反, 最后+1. (即在反码的基础上+1)
      ```
       [+1] = [00000001]原 = [00000001]反 = [00000001]补
       [-1] = [10000001]原 = [11111110]反 = [11111111]补
      ```
    
## 算法

  

## 范例：


## 代码
[bit_manipulation\*.py]{..\src\bit_manipulation\*.py}





```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块

"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

## 案例一：
  binary_and(a: int, b: int) -> str  <br>
  并将其结果 与 (与操作） a & b 的二进制值（bin) 进行对比



```python
from bit_manipulation.binary_and_operator import binary_and
"""
"""

print(binary_and(25, 32))   #   '0b000000'
print (bin(25 & 32))

print(binary_and(37, 50))   #   '0b100000'
print (bin(37 & 50))
print(binary_and(21, 30))   #   '0b10100'
print (bin(21 & 30))
print(binary_and(58, 73))   #   '0b0001000'
print (bin(58 & 73))

print(binary_and(0, 255))   #   '0b00000000'
print (bin(0 & 255))
print(binary_and(256, 256)) #   '0b100000000'
print (bin(256 & 256))
'''
print(binary_and(0, -1))    #   ValueError
# print (bin(0 & (-1))
print(binary_and(0, 1.1))   #   TypeError
# print (bin(0 & 1.1))
print(binary_and("0", "1")) #   TypeError
# print (bin("0" & "1"))
'''


```

    0b000000
    0b0
    0b100000
    0b100000
    0b10100
    0b10100
    0b0001000
    0b1000
    0b00000000
    0b0
    0b100000000
    0b100000000
    




    '\nprint(binary_and(0, -1))    #   ValueError\n# print (bin(0 & (-1))\nprint(binary_and(0, 1.1))   #   TypeError\n# print (bin(0 & 1.1))\nprint(binary_and("0", "1")) #   TypeError\n# print (bin("0" & "1"))\n'



## 案例二： 
binary_or(a: int, b: int) -> str  <br>
并将其结果 与 (或操作）a | b 的二进制值（bin) 进行对比


```python
from bit_manipulation.binary_or_operator import binary_or
"""
"""
print(binary_or(25, 32))  #    '0b111001'
print (bin(25 | 32))
print(binary_or(37, 50))  #    '0b010111'
print (bin(37 | 50))
print(binary_or(21, 30))  #    '0b01011'
print (bin(21 | 30))
print(binary_or(58, 73))  #    '0b1110011'
print (bin(58 | 73))
print(binary_or(0, 255))  #    '0b11111111'
print (bin(0 | 255))
print(binary_or(256, 256))  #    '0b000000000'
print (bin(256 | 256))
'''
print(binary_or(0, -1))   #   ValueError
# print (bin(0 | （-1）))
print(binary_or(0, 1.1))  #  TypeError
# print (bin(0 | 1.1))
print(binary_or("0", "1")) # TypeError
# print (bin("0" | "1"))
'''
    
```

    0b111001
    0b111001
    0b110111
    0b110111
    0b11111
    0b11111
    0b1111011
    0b1111011
    0b11111111
    0b11111111
    0b100000000
    0b100000000
    




    '\nprint(binary_or(0, -1))   #   ValueError\n# print (bin(0 | （-1）))\nprint(binary_or(0, 1.1))  #  TypeError\n# print (bin(0 | 1.1))\nprint(binary_or("0", "1")) # TypeError\n# print (bin("0" | "1"))\n'



## 案例三： 
binary_xor(a: int, b: int) -> str  <br>
并将其结果 与 (异或操作） a ^ b 的二进制值（bin) 进行对比


```python
from bit_manipulation.binary_xor_operator import binary_xor
"""
"""
print(binary_xor(25, 32))  #    '0b111001'
print (bin(25 ^ 32))
print(binary_xor(37, 50))  #    '0b010111'
print (bin(37 ^ 50))
print(binary_xor(21, 30))  #    '0b01011'
print (bin(21 ^ 30))
print(binary_xor(58, 73))  #    '0b1110011'
print (bin(58 ^ 73))
print(binary_xor(0, 255))  #    '0b11111111'
print (bin(0 ^ 255))
print(binary_xor(256, 256))  #    '0b000000000'
print (bin(256 ^ 256))
'''
print(binary_xor(0, -1))   #   ValueError
# print (bin(0 ^ （-1）))
print(binary_xor(0, 1.1))  #  TypeError
# print (bin(0 ^ 1.1))
print(binary_xor("0", "1")) # TypeError
# print (bin("0" ^ "1"))
'''

```

    0b111001
    0b111001
    0b010111
    0b10111
    0b01011
    0b1011
    0b1110011
    0b1110011
    0b11111111
    0b11111111
    0b000000000
    0b0
    




    '\nprint(binary_xor(0, -1))   #   ValueError\n# print (bin(0 ^ （-1）))\nprint(binary_xor(0, 1.1))  #  TypeError\n# print (bin(0 ^ 1.1))\nprint(binary_xor("0", "1")) # TypeError\n# print (bin("0" ^ "1"))\n'



## 案例四
binary_count_setbits 二进制统计集合位的数量 <br>
binary_count_setbits(a: int) -> int <br>
  = bin(a).count("1")


```python
from bit_manipulation.binary_count_setbits import binary_count_setbits
"""
"""
print(binary_count_setbits(25))  #    3
print(binary_count_setbits(36))  #    2
print(binary_count_setbits(16))  #    1
print(binary_count_setbits(58))  #    4
print(binary_count_setbits(4294967295)) #    32
print(binary_count_setbits(0))  #    0
'''
print(binary_count_setbits(-10)) #   ValueError
print(binary_count_setbits(0.8)) #    TypeError
print(binary_count_setbits("0"))  #  TypeError
'''
```

    3
    2
    1
    4
    32
    0
    




    '\nprint(binary_count_setbits(-10)) #   ValueError\nprint(binary_count_setbits(0.8)) #    TypeError\nprint(binary_count_setbits("0"))  #  TypeError\n'



## 案例五
binary_count_trailing_zeros(a: int) -> int <br>
统计属随“0” 数量  <br>
其算法为：int(log2(a & -a)) <br>


```python
from bit_manipulation.binary_count_trailing_zeros import binary_count_trailing_zeros
"""
"""
print(bin(25))
print(bin(25 & (-25)))
print(binary_count_trailing_zeros(25))  #    0


print(bin(36))
print(bin(36 & (-36)))
print(binary_count_trailing_zeros(36))  #    2


print(bin(16))
print (bin(16 & (-16)))
print(binary_count_trailing_zeros(16))  #    4


print(bin(58))
print(bin(58 & (-58)))
print(binary_count_trailing_zeros(58))  #    1

print(bin(4294967295))
print(bin(4294967295 & (-4294967295)))
print(binary_count_trailing_zeros(4294967295)) #    32

print(bin(0))
print(bin(0 & (-0)))
print (0 & (-0))
print(binary_count_trailing_zeros(0))  #    0

'''
print(binary_count_trailing_zeros(-10)) #   ValueError
print(binary_count_trailing_zeros(0.8)) #    TypeError
print(binary_count_trailing_zeros("0"))  #  TypeError
'''
```

    0b11001
    0b1
    0
    0b100100
    0b100
    2
    0b10000
    0b10000
    4
    0b111010
    0b10
    1
    0b11111111111111111111111111111111
    0b1
    0
    0b0
    0b0
    0
    0
    




    '\nprint(binary_count_trailing_zeros(-10)) #   ValueError\nprint(binary_count_trailing_zeros(0.8)) #    TypeError\nprint(binary_count_trailing_zeros("0"))  #  TypeError\n'



## 案例六
binary_shift
二进制移位，包含：
- logical_left_shift(number: int, shift_amount: int) -> str <br>
   将 number: int 转换二进制后，左移 shift_amount: int 位，返回 二进制字符串
- logical_right_shift(number: int, shift_amount: int) -> str <br>
  将 number: int 转换二进制后，左移 shift_amount: int 位，返回 二进制字符串
  


```python
from bit_manipulation.binary_shifts import logical_left_shift,logical_right_shift
"""
"""
print ('binary_shift of logical_left_shift:')
print(logical_left_shift(0, 1)) #    '0b00'
print(logical_left_shift(1, 1)) #    '0b10'
print(logical_left_shift(1, 5))  #   '0b100000'
print(logical_left_shift(17, 2)) #    '0b1000100'
print(logical_left_shift(1983, 4)) #    '0b111101111110000'
# print(logical_left_shift(1, -1))  #   ValueError
print ('binary_shift of logical_right_shift:')
print(logical_right_shift(0, 1)) #   '0b0'
print(logical_right_shift(1, 1)) #   '0b0'
print(logical_right_shift(1, 5)) #   '0b0'
print(logical_right_shift(17, 2)) #   '0b100'
print(logical_right_shift(1983, 4)) #    '0b1111011'
#  print( logical_right_shift(1, -1)) #  ValueError
    
```

    binary_shift of logical_left_shift:
    0b00
    0b10
    0b100000
    0b1000100
    0b111101111110000
    binary_shift of logical_right_shift:
    0b0
    0b0
    0b0
    0b100
    0b1111011
    

## 案例七
twos_complement(number: int) -> str <br>
二进制补码 <br>
参数：number: int 为负数或0 <br> 
返回：二进制补码的二进制字符串 <br>



```python
from bit_manipulation.binary_twos_complement import twos_complement
"""
"""
print(bin(0))
print(twos_complement(0)) #  '0b0'

print(bin(-1))
print(twos_complement(-1)) #    '0b11'

print(bin(-5))
print(twos_complement(-5)) #  '0b1011'

print(bin(-17))
print(twos_complement(-17))#    '0b101111'

print(bin(-207))
print(twos_complement(-207)) #   '0b100110001'

# print(bin(1))
# print( twos_complement(1)) #  ValueError


```

    0b0
    0b0
    -0b1
    0b11
    -0b101
    0b1011
    -0b10001
    0b101111
    -0b11001111
    0b100110001
    


```python

```
