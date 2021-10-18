---
layout: post
title:  "Quick introduction to Chern Class"
categories: Math
---

Let \\(\xi\\) be an rank \\(n\\) vector bundle with total space \\(E\\). Define \\(\mathbf{R}^n_{0} := \mathbf {R} ^{n}\setminus \\{0\\}\\), \\(E_b = \\pi^{-1}(b) \\) and \\(E_0\\) is the complement of \\(\xi\\)'s zero section. By default, (co)homology groups use integer coefficients.

<div class="theorem" type="Proposition">
\[
H^{r}(\mathbf {R} ^{n},\mathbf {R} ^{n}_0 )\cong H^{r-1}(S^{n-1} ).
\]
</div>
<div class="proof">
By the long exact sequence:
\[
\cdots \leftarrow 0 \cong H^{r-1}( \mathbf {R} ^{n} ) \leftarrow H^{r}(\mathbf {R} ^{n},\mathbf {R} ^{n}_0 ) \leftarrow H^{r-1}( \mathbf {R} ^{n}_0 ) \cong H^{r-1}(S^{n-1} ) \leftarrow \cdots.
\]
</div>

### Euler class

<div class="definition">
An orientation for \(\xi\) is a function which assigns an preferred generator
\(u_{E_b} \in H^{n}\left(\mathbf{R}^n, \mathbf{R}^n_{0}\right)\)
to each fiber \(E_b\) of \(\xi\).
The local compatibility condition implies that for every point \(b_0\) in the base space \(B\) there exists a neighborhood \(N\) and a cohomology class
\[
u \in H^{n}\left(\pi^{-1}(N), \pi^{-1}(N)_{0}\right),
\]
so that for every fiber \(E_b\) over \(N\) the restriction
\[
u \vert_{\left(E_b, E_{b,0}\right)} \in H^{n}\left(\mathbf{R}^n, \mathbf{R}^n_{0}\right)
\]
is equal to \(u_{E_b}\).
</div>


<div class="theorem">
To any orientated vector bundle \(\xi\), the cohomology group \(H^{i}\left(E, E_{0}\right)\) is zero for \(i < n \) , and \(H^{n}\left(E, E_{0}\right)\) contains one and only one cohomology class \(u\) whose restriction
\[
u \vert_{\left(E_b, E_{b,0}\right)} \in H^{n}\left(\mathbf{R}^n, \mathbf{R}^n_{0}\right)
\]
is equal to the preferred generator \(u_{E_b}\) for every fiber \(E_b\) of \(\xi\). Furthermore the correspondence \(y \mapsto y \smile u\) maps \(H^{k}(E)\) isomorphically onto \(H^{k+n}\left(E, E_{0}\right)\) for every integer \(k\).
</div>


<p>
Given an oriented n-plane bundle \(\xi\), the inclusion \((E, \text{empty set}) \subset \left(E, E_{0}\right)\) gives rise to a restriction homomorphism
\[
H^{*}\left(E, E_{0}\right) \rightarrow H^{*}(E),
\]
which we denote by \(y \mapsto y \vert_E .\) In particular, applying this homomorphism to the fundamental class \(u \in H^{n}\left(E, E_{0}\right)\), we obtain a new cohomology class
\[
u \vert_E \in H^{n}(E).
\]
But \(H^{n}(E)\) is canonically isomorphic to the cohomology group \(H^{n}(B)\) of the base space.
</p>

<div class="definition">
The Euler class of an oriented \(n\)-plane bundle \(\xi\) is the cohomology class
\[
e(\xi) \in H^{n}(B),
\]
which corresponds to \(u \vert_E\) under the canonical isomorphism \(\pi^{*}: H^{n}(B) \rightarrow\) \(H^{n}(E)\)
</div>

### Gysin sequence

<div class="theorem" type="Proposition">
To any orientated vector bundle \(\xi\), there is associated an exact sequence of the form
\[
\cdots \rightarrow H^i(B) \xrightarrow{\smile e} H^{i+n}(B) \xrightarrow{\pi_0^*} H^{i+n}(E_0) \rightarrow  H^{i+1}(B) \xrightarrow{\smile e} \cdots.
\]
Here the symbol \(\;\smile e : a \mapsto a \smile e(\xi)\).
</div>

### Chern class

<div class="definition">
The Chern class \(c_i(\omega) \in H^{2i}(B)\) are defined by induction on the complex dimension \(n\) of \(\omega\). \(c_n(\omega) = e(\omega_{\mathbf R})\) the Eular class.
For \(i < n\) we set 
\[
c_i(\omega) = {\pi_0^{*}}^{-1} c_i(\omega_0).
\]
</div>

### Refrerences [^1]

[^1]: Milnor, John and Stasheff, James D.. Characteristic Classes. (AM-76), Princeton: Princeton University Press, 2016.
