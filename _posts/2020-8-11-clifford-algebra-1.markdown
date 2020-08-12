---
layout: post
title: "Clifford Algebra (1): Example"
categories: Math
---
  
  
<p>这里我们用一个非常简单的例子， 自然地构造出一个经典的Clifford代数。</p>
<p>考虑实多项式<span class="math inline">\(x^2+y^2\)</span>， 我们在复数域内可以将其分解为 <span class="math display">\[x^2+y^2 = (x+iy)(x-iy).\]</span> 这是对 <span class="math inline">\(\mathbb{R}^2\)</span> 中的2范数的一种分解。 这使得我们思考， 是否可以找到一种分解， 使得 <span class="math inline">\(x^2+y^2\)</span> 表示为另一个数的平方的形式 （即找到 <span class="math inline">\(x^2+y^2\)</span> 的平方根）。</p>
<p>我们我们可以 考虑 <span class="math inline">\(\mathbf{e}_1, \mathbf{e}_2\)</span> 两元素使得 <span class="math display">\[x^1x^1+x^2x^2 = (x^1 \mathbf{e}_1 + x^2 \mathbf{e}_2)^2, \quad \forall (x^1,x^2) \in \mathbb{R}^2.\]</span></p>
<p>展开上述等式，我们就可以得到两个元素满足条件： <span class="math display">\[\mathbf{e}_i \mathbf{e}_j + \mathbf{e}_j \mathbf{e}_i = 2 \delta_{i,j},\]</span> 等价于 <span class="math display">\[\begin{aligned}
    \mathbf{e}_1 \mathbf{e}_2 + \mathbf{e}_2 \mathbf{e}_1 = 0,\\
    \mathbf{e}_1 \mathbf{e}_1 = \mathbf{e}_2 \mathbf{e}_2 = 1.\end{aligned}\]</span></p>
<p>注意到<span class="math inline">\(\mathbf{e}_1 \mathbf{e}_2 = - \mathbf{e}_2 \mathbf{e}_1\)</span>， 即乘法中交换相邻<span class="math inline">\(\mathbf{e}_1, \mathbf{e}_2\)</span>，结果只差一个正负号， 暂时不考虑正负号的影响， 任意数量的元素的乘积<span class="math inline">\(\mathbf{e}_{i_1} \mathbf{e}_{i_2} \cdots \mathbf{e}_{i_n} (i_n \in \{1,2\})\)</span>， 可以表示为 <span class="math display">\[\pm \underbrace{\mathbf{e}_1 \mathbf{e}_1 \cdots \mathbf{e}_1}_{p \text{ factors}} \underbrace{\mathbf{e}_2 \mathbf{e}_2 \cdots \mathbf{e}_2}_{q \text{ factors}} = \pm \left\{ \begin{matrix}
        1 &amp; \text{if } p \text{ even, } q \text{ even} \\
        \mathbf{e}_1 &amp; \text{if } p \text{ odd, } q \text{ even} \\
        \mathbf{e}_2 &amp; \text{if } p \text{ even, } q \text{ odd} \\
        \mathbf{e}_1 \mathbf{e}_2 &amp; \text{if } p \text{ odd, } q \text{ odd}
    \end{matrix} \right. .\]</span> 从而我们可以考虑形如 <span class="math display">\[\mathbf{a} = a^0 + a^1 \mathbf{e}_1 + a^2 \mathbf{e}_2 + a^{1,2} \mathbf{e}_1 \mathbf{e}_2 \quad (a^i \in \mathbb{R}, \forall i=0,1,2,3)\]</span> 的元素组成的数域（其中加减乘除运算显然是封闭的<a href="#fn2" class="footnote-ref" id="fnref2"><sup>2</sup></a>）。 该数域上的乘法即为 <span class="math display">\[\begin{aligned}
        \mathbf{a} \cdot \mathbf{b} = &amp; \quad a^0b^0 + a^1b^1 + a^2b^2 + a^{1,2} b^{1,2} \\
        &amp; + (a^0b^1 + a^1b^0 - a^2b^{1,2} + a^{1,2}b^2 ) \mathbf{e}_1\\
        &amp; + (a^0b^2 + a^1b^{1,2} + a^2b^0 - a^{1,2}b^1  ) \mathbf{e}_1\\
        &amp; + (a^0b^{1,2} + a^1b^2 - a^2b^1 + a^{1,2} b^0 ) \mathbf{e}_1 \mathbf{e}_2.
    \end{aligned}\]</span> 值得注意的是，这一乘法并不是交换的，我们有 <span class="math display">\[\begin{aligned}
        \mathbf{a} \cdot \mathbf{b} - \mathbf{b} \cdot \mathbf{a} = &amp; \quad 2(- a^2b^{1,2} + a^{1,2}b^2 ) \mathbf{e}_1\\
        &amp; + 2(a^1b^{1,2}- a^{1,2}b^1  ) \mathbf{e}_1\\
        &amp; + 2(a^1b^2 - a^2b^1 ) \mathbf{e}_1 \mathbf{e}_2.
    \end{aligned}\]</span></p>
<p>仿照复数域，我们也可以定义该数域上的共轭、模和逆 <span class="math display">\[\begin{aligned}
    \overline{\mathbf{a}} &amp;= a^0 - a^1 \mathbf{e}_1 - a^2 \mathbf{e}_2 + a^{1,2} \mathbf{e}_1 \mathbf{e}_2; \nonumber \\
    |\mathbf{a}|^2 &amp;= \mathbf{a} \overline{\mathbf{a}} = a^0 a^0 - a^1 a^1 - a^2 a^2 + a^{1,2} a^{1,2}; \nonumber\\
    \mathbf{a}^{-1}&amp;= \frac{\overline{\mathbf{a}}}{|\mathbf{a}|^2}. \label{eqn:reverse}\end{aligned}\]</span></p>
<p>通过该数域上的的线性变换我们可以导出该数域的一个矩阵表示，只是限于篇幅，不再赘述。</p>
<p>对于 <span class="math inline">\(\mathbb{R}^n\)</span> 的元素的2范数 ，这一分解就可以表示为<a href="#fn3" class="footnote-ref" id="fnref3"><sup>3</sup></a> <span class="math display">\[\delta_{i,j}x^ix^j = (x^i \mathbf{e}_i)^2.\]</span> 我们可以将这种构造推广到实对称矩阵 <span class="math inline">\(G\)</span> ： <span class="math display">\[g_{i,j}x^ix^j = (x^i \mathbf{e}_i)^2.\]</span> 那么所构造的元素满足 <span class="math display">\[\mathbf{e}_i \mathbf{e}_j + \mathbf{e}_j \mathbf{e}_i = 2g_{i,j}.\]</span> 而 <span class="math inline">\(\{\mathbf{e}_1, \cdots,  \mathbf{e}_n\}\)</span> 生成的数域，就是一种Clifford代数。 对 <span class="math inline">\(G\)</span> 进行标准正交化我们就得到了正交Clifford代数： <span class="math display">\[\mathbf{e}_i \mathbf{e}_j + \mathbf{e}_j \mathbf{e}_i =\left\{ \begin{matrix}-1,0,+1&amp;i=j,\\0&amp;i\not =j.\end{matrix}\right..\]</span> 若令 <span class="math inline">\(n=2, g_{i,j} = - \delta_{i,j}\)</span> ，我们就得到了经典的四元数。</p>