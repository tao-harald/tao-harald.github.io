---
layout: post
title: "Clifford Algebra (1): Example"
categories: Math
use_math: true
---

<p>
这里我们用一个非常简单的例子， 自然地构造出一个经典的Clifford代数。

考虑实多项式\(x^2+y^2\)， 我们在复数域内可以将其分解为

\[x^2+y^2 = (x+iy)(x-iy).\]

这是对 \(\mathbb{R}^2\) 中的2范数的一种分解。 这使得我们思考， 是否可以找到一种分解， 使得 \(x^2+y^2\) 表示为另一个数的平方的形式 （即找到 \(x^2+y^2\) 的平方根）。

我们我们可以 考虑 \( \mathbf{e}_1, \mathbf{e}_2\) 两元素使得

\[x^1x^1+x^2x^2 = (x^1 \mathbf{e}_1 + x^2 \mathbf{e}_2)^2, \quad \forall (x^1,x^2) \in \mathbb{R}^2.\]

展开上述等式，我们就可以得到两个元素满足条件：

\[\mathbf{e}_i \mathbf{e}_j + \mathbf{e}_j \mathbf{e}_i = 2 \delta_{i,j},\]

等价于

\[\begin{aligned}
    \mathbf{e}_1 \mathbf{e}_2 + \mathbf{e}_2 \mathbf{e}_1 = 0,\\
    \mathbf{e}_1 \mathbf{e}_1 = \mathbf{e}_2 \mathbf{e}_2 = 1.\end{aligned}\]

注意到\(\mathbf{e}_1 \mathbf{e}_2 = - \mathbf{e}_2 \mathbf{e}_1\)， 即乘法中交换相邻\(\mathbf{e}_1, \mathbf{e}_2\)，结果只差一个正负号， 暂时不考虑正负号的影响， 任意数量的元素的乘积\(\mathbf{e}_{i_1} \mathbf{e}_{i_2} \cdots \mathbf{e}_{i_n} (i_n \in \{1,2\})\)， 可以表示为

\[\pm \underbrace{\mathbf{e}_1 \mathbf{e}_1 \cdots \mathbf{e}_1}_{p \text{ factors}} \underbrace{\mathbf{e}_2 \mathbf{e}_2 \cdots \mathbf{e}_2}_{q \text{ factors}} = \pm \left\{ \begin{matrix}
        1 & \text{if } p \text{ even, } q \text{ even} \\
        \mathbf{e}_1 & \text{if } p \text{ odd, } q \text{ even} \\
        \mathbf{e}_2 & \text{if } p \text{ even, } q \text{ odd} \\
        \mathbf{e}_1 \mathbf{e}_2 & \text{if } p \text{ odd, } q \text{ odd}
    \end{matrix} \right. .\]

从而我们可以考虑形如

\[\mathbf{a} = a^0 + a^1 \mathbf{e}_1 + a^2 \mathbf{e}_2 + a^{1,2} \mathbf{e}_1 \mathbf{e}_2 \quad (a^i \in \mathbb{R}, \forall i=0,1,2,3)\]

的元素组成的数域（其中加减乘除运算显然是封闭的）。 该数域上的乘法即为

\[\begin{aligned}
        \mathbf{a} \cdot \mathbf{b} = & \quad a^0b^0 + a^1b^1 + a^2b^2 + a^{1,2} b^{1,2} \\
        & + (a^0b^1 + a^1b^0 - a^2b^{1,2} + a^{1,2}b^2 ) \mathbf{e}_1\\
        & + (a^0b^2 + a^1b^{1,2} + a^2b^0 - a^{1,2}b^1  ) \mathbf{e}_1\\
        & + (a^0b^{1,2} + a^1b^2 - a^2b^1 + a^{1,2} b^0 ) \mathbf{e}_1 \mathbf{e}_2.
    \end{aligned}\]

值得注意的是，这一乘法并不是交换的，我们有

\[\begin{aligned}
        \mathbf{a} \cdot \mathbf{b} - \mathbf{b} \cdot \mathbf{a} = & \quad 2(- a^2b^{1,2} + a^{1,2}b^2 ) \mathbf{e}_1\\
        & + 2(a^1b^{1,2}- a^{1,2}b^1  ) \mathbf{e}_1\\
        & + 2(a^1b^2 - a^2b^1 ) \mathbf{e}_1 \mathbf{e}_2.
    \end{aligned}\]

仿照复数域，我们也可以定义该数域上的共轭、模和逆

\[\begin{aligned}
    \overline{\mathbf{a}} &= a^0 - a^1 \mathbf{e}_1 - a^2 \mathbf{e}_2 + a^{1,2} \mathbf{e}_1 \mathbf{e}_2; \nonumber \\
    |\mathbf{a}|^2 &= \mathbf{a} \overline{\mathbf{a}} = a^0 a^0 - a^1 a^1 - a^2 a^2 + a^{1,2} a^{1,2}; \nonumber\\
    \mathbf{a}^{-1}&= \frac{\overline{\mathbf{a}}}{|\mathbf{a}|^2}. \label{eqn:reverse}\end{aligned}\]

通过该数域上的的线性变换我们可以导出该数域的一个矩阵表示，只是限于篇幅，不再赘述。

对于 \(\mathbb{R}^n\) 的元素的2范数 ，这一分解就可以表示为

\[\delta_{i,j}x^ix^j = (x^i \mathbf{e}_i)^2.\]

我们可以将这种构造推广到实对称矩阵 \(G\) ：

\[g_{i,j}x^ix^j = (x^i \mathbf{e}_i)^2.\]

那么所构造的元素满足

\[\mathbf{e}_i \mathbf{e}_j + \mathbf{e}_j \mathbf{e}_i = 2g_{i,j}.\]

而 \(\{\mathbf{e}_1, \cdots,  \mathbf{e}_n\}\) 生成的数域，就是一种Clifford代数。 对 \(G\) 进行标准正交化我们就得到了正交Clifford代数：

\[\mathbf{e}_i \mathbf{e}_j + \mathbf{e}_j \mathbf{e}_i =\left\{ \begin{matrix}-1,0,+1&i=j,\\0&i\not =j.\end{matrix}\right..\]

若令 \(n=2, g_{i,j} = - \delta_{i,j}\) ，我们就得到了经典的四元数。
</p>
