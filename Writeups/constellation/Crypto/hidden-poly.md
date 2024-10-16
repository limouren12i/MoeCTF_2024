# hidden-poly

完全靠自己解出的第一道格题。其实这题格的构造比背包加密的还要简单，不过后者有脚本给我偷，谁还管它难不难（
```py
root = 122536272320154909907460423807891938232
q = 264273181570520944116363476632762225021
m=Matrix(ZZ,[
    [q,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0],
    [root,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0],
    [root**2,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0],
    [root**3,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0],
    [root**4,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0],
    [root**5,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0],
    [root**6,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0],
    [root**7,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0],
    [root**8,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0],
    [root**9,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0],
    [root**10,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0],
    [root**11,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0],
    [root**12,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0],
    [root**13,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0],
    [root**14,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0],
    [root**15,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1]
])
print(m.LLL()[0])
```
根据题目能写出这样一个多项式： $a+bx+cx^2+dx^3+...-kq=0$ ，变形后得到 $bx+cx^2+dx^3+...-kq=-a$ 。已知key的每个字节最多是255，那么这个格的短向量有很大概率就是它。事实确实如此

……其实能做出来完全是因为我之前见过类似的题（见 https://github.com/C0nstellati0n/NoobCTF/blob/main/%E7%AC%94%E8%AE%B0/Crypto/%E6%95%B0%E5%AD%A6%E6%A6%82%E5%BF%B5%E4%B8%8E%E7%BB%93%E6%9E%84/Lattice%E5%AD%A6%E4%B9%A0.md ），模p后找多项式的系数什么的。完全就是一模一样的原理