# rot13  回转13位密码

ROT13（回转13位，rotate by 13 places，有时中间加了个连字符称作ROT-13）是一种简易的替换式密码。它是一种在英文网络论坛用作隐藏八卦（spoiler）、妙句、谜题解答以及某些脏话的工具，目的是逃过版主或管理员的匆匆一瞥。ROT13被描述成“杂志字谜上下颠倒解答的Usenet点对点体”。ROT13 也是过去在古罗马开发的凯撒加密的一种变体。<br>


## 密码描述

套用ROT13到一段文字上仅仅只需要检查字元字母顺序并取代它在13位之后的对应字母，有需要超过时则重新绕回26英文字母开头即可。$ A $ 换成 $ N $ 、$ B $ 换成 $ O $ 、依此类推到 $ M $ 换成 $ Z $ ，然后序列反转：$ N $ 换成A、$ O $ 换成 $ B $ 、最后 $ Z $ 换成 $ M $。只有这些出现在英文字母里头的字元受影响；数字、符号、空白字元以及所有其他字元都不变。因为只有在英文字母表里头只有26个，并且26=2×13，ROT13函数是它自己的逆反 <br>
对任何字元 $ x：ROT13(ROT13(x))=ROT26(x)=x $ 。 <br>
换句话说，两个连续的ROT13应用函式会回复原始文字（在数学上，这有时称之为对合（involution）；在密码学上，这叫做对等加密（reciprocalcipher））。<br>
转换可以利用查找表完成，如下例所示：<br>
$$ ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz $$ <br>
$$ NOPQRSTUVWXYZABCDEFGHIJKLMnopqrstuvwxyzabcdefghijklm $$ <br>
例如，下面的英文笑话，精华句为ROT13所隐匿：<br>
How can you tell an extrovert from an  <br>
introvert at NSA?Va gur ryringbef,  <br>
gur rkgebireg ybbxf ng gur BGURE thl'f fubrf. <br>
透过ROT13表格转换整片文字，该笑话的解答揭露如下：<br>
Ubj pna lbh gryy na rkgebireg sebz na  <br>
vagebireg ng AFN?In the elevators,     <br>
the extrovert looks at the OTHER guy's shoes. <br>
第二次ROT13函数将转回原始文字。<br>

## 主要用途
ROT13过去用在1980年代早期的net.jokes新闻群组。它被用来隐藏某些可能侮辱到特定读者的笑话、隐晦某个谜题的答案或八卦性的内容。之所以选一次13个字母的位移而不是其他值（例如原本凯撒加密里的3字母位移）乃因13位这个值刚刚好加密解密都是一样，故只要一行命令就可以简洁的满足两者需要。ROT13一般是新闻阅读软体内建支援的功能。Email位址有时也以ROT13编码以躲过较不复杂的垃圾邮件机器人耳目。 <br>
ROT13是凯撒密码加密演算法的特例。西元前一世纪尤利乌斯·凯撒发明凯萨加密法。更具体的例子是跋舍耶那加密（Vatsyayanacipher），该密码描述了《爱欲经》（Kama-Sutra）整本经文。<br>
ROT13并不意图用在重视机密性的场合—固定位移的使用意味着该加密实际上并没有金钥，而且解码不需要对ROT13实际上的使用有较深了解。即使没有ROT13使用的知识，该演算法也相当容易透过频率分析破解。正因为其完全不适合真正的机密用途，ROT13已经变成了一种警句，用来影射任何显著的弱加密体系；例如批评家可能会这样说：“56位元DES这些日子以来只比ROT13要好一点。”另外，作为对真正术语像“双重DES”的嘲讽，半路杀出的术语“双重ROT13”、“ROT26”、“2ROT13”、以及玩笑性质的学术论文“关于2ROT13加密演算法”都闪烁著幽默的心思。因为套用ROT13到已经加密过的ROT13文字，将会打回原形；也就是说，ROT26等于没有加密。延伸下去，三重ROT13(用来取笑其对比的3DES)等同于1次ROT13而已。
于1999年12月，人们发现网景通讯家利用ROT13作为其储存email密码的不安全体系。在2001年，俄罗斯程式设计师狄米区·史盖里亚罗夫（DimitrySklyarov）展示eBook贩卖商NewParadigmResearchGroup（NPRG）使用ROT13来对它们的文件加密；据推测NPRG可能把ROT13玩具样本——跟着AdobeeBook软件开发工具包一起提供——用错在重大加密体系上。WindowsXP也在某些注册机码上使用ROT13。
范例演示
ROT13为字母游戏提供了良机。许多字经过ROT13转换后，会产生另一个字。英文里字最长的范例是一组7个字母的字abjurer与nowhere；另一组七字母的是chechen与purpura。其他字的范例如表中所示。
1989年国际C语言混乱代码大赛（IOCCC）收录了一个来自布来恩·卫斯里（BrianWestley）的作品。卫斯里的计算机程序可被ROT13编解码，并且仍旧正确的通过编译。该程式主要是进行ROT13编码，或者反过来解码其输入。
新闻群组alt.folklore.urban创造了生字：furrfu，该字是常用状声辞“嘘”（sheesh）的ROT13编码。"Furrfu"在1992年中期首度出现，作为在alt.folklore.urban新闻群组里重复都会传奇的帖子，某些发帖人抱怨新手过度使用"Sheesh!"的回应。<br>

## 变体

ROT47是ROT13的衍生物，它除了打乱基本字母外，也对数字与常见符号做处理。除了使用A–Z系列外，ROT47使用较宽的ASCII字符集。具体而言，所有7-bit可列印字元，除空白以外，从十进位33'!'到126'~'都被毫无保留的用来做47位循环。使用较广的字母集原意是产生比ROT13更彻底的乱码，不过因为ROT47无差别的导入了数字与符号混合，这种方式较容易看出文字被动过手脚。<br>
范例：<br>
TheQuickBrownFoxJumpsOverTheLazyDog.<br>
加密成为<br>
%96"F:4AD~G6C%96{2KJs@8] <br>
程序设计里标准的GNUC函式库包含了一个函式—memfrob()—它与ROT13有类似的效果，尽管该函式使用对象是任意双位元组资料。memfrob()透过每个位元与双位元样板00101010（42）做互斥（XOR）运算合并。这个效果是一种简单的XOR操作。与ROT13相似，memfrob()也是自我逆反的，故提供的保全程度好不到哪里去。

- rot5：<br>
只将字符串中的数字进行加密，步数为5，同时在0-9十个数字进行循环，如1在rot5加密后为6，而6在rot5加密后为1 <br>
- rot13：<br>
只将字符串中的字母进行加密，步数为13，加密方式上最接近凯撒密码，分别在A-Z或a-z之间循环，如A在rot13加密后为N,Z在rot13加密后为M <br>
- rot18: <br>
字面意思(5+13=18) 即将上述两种加密方式结合，分别对数字和字母进行相应的操作 <br>
- rot47: <br>
由于无论是rot5、rot13或rot18都只能对数字和字母进行相应的加密，而对“！@#￥%&”之类的符号却缺少加密，因此在此基础上引入ASCII码
如果理解了上面的rot5、rot13、rot18，那么rot47也相当好理解了，只是将步数改为47而已（同样存在循环） <br>
对数字、字母、常用符号进行编码，按照它们的ASCII值进行位置替换，用当前字符ASCII值往前数的第47位对应字符替换当前字符，例如当前为小写字母z，编码后变成大写字母K，当前为数字0，编码后变成符号_。
## 代码
[rot13.py]{..\src\ciphers\rot13.py}



```python
"""
Prepare
   1. sys.path 中增加 TheAlgorithms\src 子模块

"""
import sys
sys.path.append('E:\dev\AI\TheAlgorithms\src')

```

## 案例一： dencrypt

对字符串进行 rot13 加密；
并检查原始字符串与 双重 rot13 加密 的字符串是否一致
```
def dencrypt(s: str,  -- 原始字符串
    n: int = 13)  # 默认 13 
     -> str:
```



```python
from ciphers.rot13 import dencrypt
"""
"""
s0 = "My secret bank account number is 173-52946 so don't tell anyone!!"

print("Input Message :", s0)
s1 = dencrypt(s0, 13)
print("Encryption:", s1)
s2 = dencrypt(s1, 13)
print("Decryption: ", s2)

print (f"the initial Message is equal the double rot13 dencrypt message:{s0==s2}")


```

    Input Message : My secret bank account number is 173-52946 so don't tell anyone!!
    Encryption: Zl frperg onax nppbhag ahzore vf 173-52946 fb qba'g gryy nalbar!!
    Decryption:  My secret bank account number is 173-52946 so don't tell anyone!!
    the initial Message is equal the double rot13 dencrypt message:True
    


```python

```
