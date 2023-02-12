---
layout: post
title:  "Real Grassmannian"
categories: Math
published: false
---

Projective space over field \\(k\\) can be defined as 
\\[\mathbb{P}^n(k) = (k^{n+1} \setminus \\{ 0 \\})/(k \setminus \\{ 0 \\}).\\]
Then ther is a fiber bundle \\(S^n(k) \to \mathbb{P}^n(k)\\) with fiber \\(S^0(k)\\), where there sphere is defined as
\\[S^n(k) = \left\\{ x \in k^{n+1} \, \middle | \, \\| x \\| = 1 \right\\}.\\]

Consider the inclusion of the boundary \\(S^{k-1} \hookrightarrow  D^k\\), inducing an inclusion map
\\[S^{k-1} / R \cong \mathbb{P}^{k-1}(\mathbb{R}) \hookrightarrow  D^k / R \cong \mathbb{P}^k(\mathbb{R}).\\]
Then we obtain \\(\mathbb{P}^k(\mathbb{R})\\) from \\(\mathbb{P}^{k-1}(\mathbb{R})\\) by attaching \\(D^k\\) along the quotient map.[^1]

The CW complex of \\(\mathbb{P}^n(\mathbb{R})\\) has one and only one \\(k\\)-cell for \\(k\leq n\\). The composition 
\\[\chi_k : \partial D^{k} \cong \mathbb S^{k-1} \xrightarrow{\varphi} \mathbb{P}^{k-1}(\mathbb{R}) \xrightarrow{q} \mathbb{P}^{k-1}(\mathbb{R}) / \mathbb{P}^{k-2}(\mathbb{R}) \cong \mathbb S^{k-1} \\]
has degree \\(1 + (-1)^k \\) since \\(q \circ \varphi\\) maps two components of \\(S^{k-1} - S^{k-2}\\) onto \\(\mathbb{P}^{k-1}(\mathbb{R}) - \mathbb{P}^{k-2}(\mathbb{R})\\) and two homomorphisms are obtained from each other by precomposing with antipodal map of \\(S^{k-1}\\). Antipodal map of \\(S^{k-1}\\) has degree 
\\( (-1)^k \\) since it's the composition of \\(k\\) reflections.

Therefore the cellular chain complex is of the form
\\[\xrightarrow{0} C_{2k} \xrightarrow{2} C_{2k-1} \xrightarrow{0} \cdots \xrightarrow{2} C_1 \xrightarrow{0} C_0 \to 0, \\]
where \\(C_{i} \cong G\\) the coefficient for all \\(n\geq i \geq 0\\)
Hence the homology
<p>
\[H_{i}(\mathbb {RP} ^{n} ; \mathbb {Z})={\begin{cases}\mathbb {Z} &i=0{\text{ or }}i=n{\text{ odd,}}\\\mathbb {Z} /2\mathbb {Z} &0<i<n,\ i\ {\text{odd,}}\\0&{\text{else.}}\end{cases}}\]
</p>

The cochain complex
\\[\xleftarrow{0} C_{2k}^\ast \xleftarrow{2} C_{2k-1}^\ast \xleftarrow{0} \cdots \xleftarrow{2} C_1^\ast \xleftarrow{0} C_0^\ast \to 0, \\]
whence the homology
<p>
\[H^{i}(\mathbb {RP} ^{n} ; \mathbb {Z})={\begin{cases}\mathbb {Z} &i=0{\text{ or }}i=n{\text{ odd,}}\\\mathbb {Z} /2\mathbb {Z} &0<i<n,\ i\ {\text{even,}}\\0&{\text{else.}}\end{cases}}\]
</p>

### Reference

[^1]: [Justin Young](https://math.stackexchange.com/users/17892/justin-young), [CW complex structure of the projective space \\(\mathbb{RP}^n\\)](https://math.stackexchange.com/q/194742)