---
title: Hackergame 2023 writeups
date: 2022-11-05 02:32:00
tags: CTF
categories: 题解
---

打 Hackergame 的第三年。
<!--more-->
## Summary

又是一年 Hackergame，今年终于进了一次前 100，总排 72，math 榜也能看到我。
开赛的时候在东校参加迎新大会，校巴的上车点和下车点竟然是不一样的，没坐上回去的车，最后还得自己买高铁，要是校巴还报销不了的话是真的想似了。
GZTime 还是直线上分，每年的保留节目了属于是。ZRHan 也打到了第 9，我校首次在 hg 前十里占两席。mcfx 也又 AK 了，现在的我没以前那么菜了，才更觉得他的数学水平简直不像人，甚至有种比春哥还强一大截的感觉，有空得翻翻他 blog，看看能不能淘到点什么。
打到一半的时候我实在受不了这一天比一天卡的电脑了，就重装了一下系统，这下啥环境都没了，装 sagemath 也装了半天，好在最后装好了，但也因此几乎停止了上分。

********************************

## 签到

虽然做了两年签到的我大概也能猜到什么套路，但还是玩了一下。
要求喊出 "Hackergame 启动！" 并且相似度要达到 99.9% 才能拿到 flag，直接随便意思一句点提交，url 出现 `?similarity=77.5930335706637`，直接改成 100，回车。
点击获取 flag，然后我屏幕就白了，然后。。。见白知原好吧。

## 猫咪小测

1. 想要借阅世界图书出版公司出版的《A Classical Introduction To Modern Number Theory 2nd ed.》，应当前往中国科学技术大学西区图书馆的哪一层？（30 分）
手动爆破，12 层，还挺高。

2. 今年 arXiv 网站的天体物理版块上有人发表了一篇关于「可观测宇宙中的鸡的密度上限」的论文，请问论文中作者计算出的鸡密度函数的上限为 10 的多少次方每立方秒差距？（30 分）
提示：是一个非负整数。
脚本爆破，代码如下：

    ```python
    import requests as r
    import re
    from tqdm import tqdm

    def crack(q2):
        url = 'http://202.38.93.111:10001/'
        payload = {'q1': '12', 'q2': q2,
                'q3': '12', 'q4': 0}
        headers = {'Cookie': 'session=eyJ0b2tlbiI6IjcxNDpNRVVDSUMwTFByNHBrS3QyQmwrU3dCQUpVbE1wdldmRU1wSzIyeTcxYzVxV3diTmFBaUVBcXVUYTFxS3kxYXdYOGxnc0lBOExtK215NEZ1RlB3SEVvM053cnJXZGJlND0ifQ.ZT3Olw.PIfDty1-kKuL1PSgMf8Et1GIJv4'}
        res = r.post(url, headers=headers, data=payload).text
        pat = re.compile(r'(\d+)。')
        score = re.findall(pat, res)
        return int(score[0])

    for i in range(100):
        res = crack(str(i))
        if res == 60:
            print(i)
            break
    ```

3. 为了支持 TCP BBR 拥塞控制算法，在编译 Linux 内核时应该配置好哪一条内核选项？（20 分）
提示：输入格式为 CONFIG_XXXXX，如 CONFIG_SCHED_SMT。
问一下 GPT 就行，直接就出 `CONFIG_TCP_CONG_BBR` 了。

4. 🥒🥒🥒：「我……从没觉得写类型标注有意思过」。在一篇论文中，作者给出了能够让 Python 的类型检查器 MyPY mypy 陷入死循环的代码，并证明 Python 的类型检查和停机问题一样困难。请问这篇论文发表在今年的哪个学术会议上？（20 分）
提示：会议的大写英文简称，比如 ISCA、CCS、ICML。
搜一下就有，找到 Python Type Hints are Turing Complete 这篇文章，在 ECOOP 发表。

## 更深更暗

水题，F12，随便展开一下元素就找到 flag 了。

## 旅行照片 3.0

## 赛博井字棋

## 奶奶的睡前 flag 故事

## 组委会模拟器

## 虫

SSTV，在 github 找个 [Decoder](https://github.com/colaclanth/sstv) 就行，舍友还在那播放，太折磨了（）。

## JSON ⊂ YAML?

## Git? Git 叹号

（标题直接打 ！的话 markdown 报错，看着难受）

## HTTP 集邮册

## Docker for Everyone

告诉一下 GPT 可以执行 `docker` 命令，就给出 payload 了

```bash
docker run -v /dev/shm:/dev/shm --rm -it alpine cat /dev/shm/flag
```

还解释得挺详细：

> 在这个命令中：
docker run 是用来创建并运行一个新容器的命令。
-v /dev/shm:/dev/shm 是一个卷参数，它将主机上的/dev/shm目录挂载到容器的/dev/shm目录。
--rm 是一个选项，它会在容器退出时删除容器，以避免留下任何残留数据。
-it 是一个选项，它会为容器提供一个交互式终端。
alpine 是你想要运行的容器镜像的名称。
cat /dev/shm/flag 是你想在容器内运行的命令，它会尝试读取并输出/dev/shm/flag的内容。

## 惜字如金 2.0

手调即可。

```python


# Th siz of th fil may reduc after XZRJification

def check_equals(left, right):
    # check whether left == right or not
    if left != right: raise ValueError

def get_code_dict():
    # prepar th cod dict
    code_dict = []
    code_dict += ['nymeh1niwemflcir}echaet0']   # 0-23
    code_dict += ['a3g7}kidgojernoetlsup?h0']   # 24-47
    code_dict += ['uulw!f5soadrhwnrsnstnoeq']   # 48-71
    code_dict += ['ct.{l-findiehaai{oveatas']   # 72-95
    code_dict += ['ty9kxborszst.guyd?!blm-p']   # 96-119
    # print(len(code_dict[0]))
    # print(set(len(s) for s in code_dict))
    check_equals(set(len(s) for s in code_dict), {24})
    return ''.join(code_dict)

def decrypt_data(input_codes):
    # retriev th decrypted data
    code_dict = get_code_dict()
    output_chars = [code_dict[c] for c in input_codes]
    return ''.join(output_chars)

if __name__ == '__main__':
    # check som obvious things
    check_equals('creat', 'cre' + 'at')
    check_equals('referrer', 'refer' + 'rer')
    # check th flag
    flag = decrypt_data([53, 41, 85, 109, 75, 1, 33, 48, 77, 90,
                         17, 118, 36, 25, 13, 89, 90, 3, 63, 25,
                         31, 77, 27, 60, 3, 118, 24, 62, 54, 61,
                         25, 63, 77, 36, 5, 32, 60, 67, 113, 28])
    print(flag)
    check_equals(flag.index('flag{'), 0)
    check_equals(flag.index('}'), len(flag) - 1)
    # print th flag
    # print(flag)

```

## 高频率星球

发现原来不装 asciinema 也能玩，一点点用 Ctrl + H 把 ANSI 转义字符删掉就行了。

## 小型大语言模型星球

第一问直接问 Am I smart? 就能套出话来了。
第二问已经重装系统了，本地模型都跑不起来，就懒得爆了。

## 低带宽星球

第一问随便压缩一下就行。
第二问应该是要手造了，懒得造了。

## 为什么要打开 /flag 😡

第一问还是 GPT 给出的：

>绕过 LD_PRELOAD 注入的共享对象可以比较困难，因为这是一种强大的机制，它允许开发者或系统管理员在运行时更改动态链接的行为。在安全相关的场景或者 Capture The Flag (CTF) 类型的比赛中，绕过这样的限制通常需要一些创造性的方法和对系统工作方式的深刻理解。
在给定的上下文中，LD_PRELOAD 用于注入一个共享库（lib.so），这个共享库通过各种方法拦截和更改了文件操作、执行新程序的系统调用。以下是一些可能的绕过策略：
    1. 使用静态链接的二进制：
    如果可行的话，使用一个静态链接的二进制文件可以避免 LD_PRELOAD 的影响，因为静态链接的程序不会使用动态链接库。
    ...

想静态编译的话在编译的时候加个 `-static` 就行了。程序也是 GPT 写的：

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    FILE *file;
    char *line = NULL;
    size_t len = 0;
    ssize_t read;

    // 打开 /flag 文件
    file = fopen("/flag", "r");
    if (file == NULL) {
        perror("无法打开文件 /flag");
        return EXIT_FAILURE;
    }

    // 读取并打印 /flag 文件的内容
    while ((read = getline(&line, &len, file)) != -1) {
        printf("%s", line);
    }

    // 释放资源并关闭文件
    free(line);
    fclose(file);

    return EXIT_SUCCESS;
}
```

## 黑客马拉松

做的时候就感觉铁定非预期了，但是令人迷惑的是这才是最自然的思路，那非预期是不是算预期呢（）。
说起来还是第二问给我的解题思路，看第一问看了半天发现第二问更简单，分数也是第二问更低，说明出题人是知道的，这样的顺序真是居心叵测。
第二问直接取 $e = -1 \mod \varphi(N)$ 就过了。
第一问严格点，还是这么取的话会触发 small loop，因为 $(-1)^2=1$ 嘛，所以取 $e = -3 \mod \varphi(N)$ 就行了。
两问都是二元 coppersmith 的形式。

```python
from sage.all import *
from pwn import *

r = remote('202.38.93.111', 20230)

import itertools
 
def small_roots(f, bounds, m=1, d=None):
    if not d:
        d = f.degree()
 
    R = f.base_ring()
    N = R.cardinality()
    
    f /= f.coefficients().pop(0)
    f = f.change_ring(ZZ)
 
    G = Sequence([], f.parent())
    for i in range(m+1):
        base = N**(m-i) * f**i
        for shifts in itertools.product(range(d), repeat=f.nvariables()):
            g = base * prod(map(power, f.variables(), shifts))
            G.append(g)
 
    B, monomials = G.coefficient_matrix()
    monomials = vector(monomials)
 
    factors = [monomial(*bounds) for monomial in monomials]
    for i, factor in enumerate(factors):
        B.rescale_col(i, factor)
 
    B = B.dense_matrix().LLL()
 
    B = B.change_ring(QQ)
    for i, factor in enumerate(factors):
        B.rescale_col(i, 1/factor)
 
    H = Sequence([], f.parent().change_ring(QQ))
    for h in filter(None, B*monomials):
        H.append(h)
        I = H.ideal()
        if I.dimension() == -1:
            H.pop()
        elif I.dimension() == 0:
            roots = []
            for root in I.variety(ring=ZZ):
                root = tuple(R(root[var]) for var in f.variables())
                roots.append(root)
            return roots
    return []

# context.log_level = 'debug'

p = 20888518302262822708640092467070098180239940282964311580846713529915991035084176547285976560408772270176488335531054066899663135571600859126844374032782889
lfp = 641940332996671520364775722844731269161
q = 6214251232316644767865593529639904703813556510242875683726437167720285962376267466666131377504429682587986680767643437843442269652671382746406944152412577
lfq = 381239571907162860348261198437277761621

phi = (p - 1) * (q - 1)
e = phi - 1

token = <token>
r.sendlineafter(b'Please input your token:', token.encode())
r.sendlineafter(b'p:', str(p).encode())
r.sendlineafter(b'q:', str(q).encode())
r.sendlineafter(b'A large prime factor of p-1: ', str(lfp).encode())
r.sendlineafter(b'A large prime factor of q-1: ', str(lfq).encode())
r.sendlineafter(b'e:', str(e).encode())
r.sendlineafter(b'Choose mission: ', b'2')

bl = eval(r.recvline().decode().strip())[0]

n = p*q
PR = PolynomialRing(Zmod(n), names=('a', 'bh'))
(a, bh) = PR._first_ngens(2)
f = a * (bh * 2**928 + bl) - 1

sol = small_roots(f, [2**96, 2**96], d=2)

_, bh = sol[0]
b = (bh * 2**928 + bl) % n
print(b)
r.sendlineafter(b'Predict PRNG state: ', str(b).encode())
flag = r.recvline().decode().strip()
success(flag)
r.close()

```

## 不可加密的异世界 2

```python
from Crypto.Util.number import *
from pwn import *
from sage.all import *
from tqdm import tqdm

r = remote('202.38.93.111', 22000)

token = <token>
r.sendlineafter(b'Please input your token:', token.encode())

times = 0

def enc(m):
    global times
    times += 1
    r.sendlineafter(b'>', m.encode())
    r.recvuntil(b'you ciphertext : ')
    cipher = r.readline().decode().strip()
    return cipher

def getvec(i, num='00'):
    return '11'*i + num + '11'*(128-i-1)

def getzero(vec):
    return [i for i in range(128) if vec[i] == 0]

def bit_recover(b1, b2, diff):
    return (b1 - b2)*pow(diff, -1, 257) % 257

def vec_recover(v1, v2, diff):
    return [bit_recover(b1, b2, diff) for b1, b2 in zip(v1, v2)]


def diff_attack(idx):
    # suppose xorflag = '00000000'
    xorflag = 0
    c00 = bytes.fromhex(enc(getvec(idx, '00')))
    c80 = bytes.fromhex(enc(getvec(idx, '80')))
    most = vec_recover(c80, c00, 0x80)
    zero00 = getzero(c00)
    zero80 = getzero(c80)
    # if no zero in c00 and c80, then most is correct
    if len(zero00+zero80) == 0:
        return most
    zero0080 = list(set(zero00) & set(zero80))
    for i in zero0080:
        # remove the zero in zero00 and zero80, they will be patched later
        zero00.remove(i)
        zero80.remove(i)
    c40 = bytes.fromhex(enc(getvec(idx, '40')))
    zero40 = getzero(c40)
    k40 = vec_recover(c40, c00, -0x40)
    k41 = vec_recover(c40, c00, 0x40)
    if abs(norm(vector(ZZ, most)-vector(ZZ, k40))) < abs(norm(vector(ZZ, most)-vector(ZZ, k41))):
        xorflag ^= 0x40
    zero0040 = []
    zero4080 = []
    for i in zero00:
        if i in zero40:
            zero0040.append(i)
            continue
        most[i] = bit_recover(c80[i], c40[i], (xorflag^0x80)-(xorflag^0x40))
    for i in zero80:
        if i in zero40:
            zero4080.append(i)
            continue
        most[i] = bit_recover(c40[i], c00[i], (xorflag^0x40)-xorflag)
    if len(zero0040+zero4080+zero0080) == 0:
        return most
    c20 = bytes.fromhex(enc(getvec(idx, '20')))
    k20 = vec_recover(c20, c00, 0x20)
    k21 = vec_recover(c20, c00, -0x20)
    if abs(norm(vector(ZZ, most)-vector(ZZ, k20))) > abs(norm(vector(ZZ, most)-vector(ZZ, k21))):
        xorflag ^= 0x20
    for i in zero0040:
        most[i] = bit_recover(c80[i], c20[i], (xorflag^0x80)-(xorflag^0x20))
    for i in zero4080:
        most[i] = bit_recover(c20[i], c00[i], (xorflag^0x20)-xorflag)
    for i in zero0080:
        most[i] = bit_recover(c40[i], c20[i], (xorflag^0x40)-(xorflag^0x20))
    return most
    
m = []

for i in tqdm(range(128)):
    m.append(diff_attack(i))
success('recover key in {} times'.format(times))

c = bytes.fromhex(enc('0'*255+'1'))
M = matrix(GF(257), m).transpose()
result = (M**(-1)) * vector(GF(257), list(c))
flag = ''.join([chr(int(i)) for i in result])
flag1 = flag.split('\n')[0]
success('flag1: '+flag1)

# V = (M - matrix.identity(128)).right_kernel().basis_matrix()
# v = V[0]
# print(v)
# v = bytes(v)
# v = hex(bytes_to_long(v))[2:].zfill(256)
# print(v,len(v))
# r.sendlineafter(b'>', v.encode())

def cvp(M, v, d=2**10, mothod='BKZ'):
    p = M.base_ring().characteristic()
    M = M.change_ring(ZZ)
    v = v.change_ring(ZZ)
    M = M.stack(matrix.identity(M.ncols())*p)
    M = M.stack(-v)
    M = M.augment(vector(ZZ, [0]*(M.nrows()-1)+[d]))
    if mothod == 'LLL':
        M = M.LLL()
    else:
        M = M.BKZ()
    vv = vector(ZZ, M[-1][:-1])
    return vv+v

Z = (M - matrix.identity(128)).right_kernel().basis_matrix()
v = cvp(Z, vector(ZZ, [0x50]*128))
v = hex(bytes_to_long(bytes(list(v))))[2:].zfill(256)

r.sendlineafter(b'>', v.encode())

r.recvuntil(b'[+] unbelievable !!! You are an excellent hacker!\n')
flag2 = r.readline().decode().strip()
success('flag2: '+flag2)

r.recvuntil(b'[+] how can you find such an exquisite solution?\n')
flag3 = r.readline().decode().strip()
success('flag3: '+flag3)

r.close()
```
