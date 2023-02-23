---
layout: post
title:  "Global Derived Hom"
categories: Math
---

When defining the derived version of gloabl hom \\(\\mathrm{Hom}\_{\\mathcal{O}\_X}(-,-)\\), a natural way is to view this bifunctor as the composition \\(\\Gamma(X,\\mathcal{H}om\_{\\mathcal{O}\_X}(-,-))\\). Then one may define
\\[ \\mathbf{R}\\mathrm{Hom}\_{\\mathcal{O}\_X}(-,-) = \\mathbf{R}\\Gamma(X,\\mathbf{R}\\mathcal{H}om\_{\\mathcal{O}\_X}(-,-)). \\]

In this way, if \\(E\\) is \\(K\\)-flat and \\(G\\) is \\(K\\)-injective, then \\(\\mathrm{Hom}\_{\\mathcal{O}\_X}(E,G)\\) represents \\(\\mathbf{R}\\mathrm{Hom}\_{\\mathcal{O}\_X}(E,G)\\). However, the result is also true even when only \\(G\\) is \\(K\\)-injective, as \\(\\mathcal{H}om\_{\\mathcal{O}\_X}(E,G)\\) is **weakly \\(K\\)-injective**[^1] in this situation and weakly \\(K\\)-injectivity implies computing \\(\\mathbf{R}\\Gamma(X, -)\\), which is well explained in Proposition 5.16[^1]. That's the reason why [^2] use the \\(K\\)-injectivity of \\(G\\) to compute \\(\\mathbf{R}\\mathrm{Hom}\_{\\mathcal{O}\_X}(E,G) \\).

### References

[^1]: *Spaltenstein, N.* Resolutions of unbounded complexes. Compositio Math. 65 (1988), no. 2, 121–154.
[^2]: *Hartshorne, Robin* Residues and duality. Lecture notes of a seminar on the work of A. Grothendieck, given at Harvard 1963/64. With an appendix by P. Deligne. Lecture Notes in Mathematics, No. 20 Springer-Verlag, Berlin-New York 1966 vii+423 pp.