---
layout: post
title:  "Publish LaTeX on Jekyll"
categories: General
abstract: "As I wrote most of my documents in LaTeX, it's important to find a convenient way to publish them on the web platform like Jekyll. Here is my way to publish it."
---


First we need to use pandoc to convert file form LaTeX to markdown:
```
pandoc -s essay.tex -o essay.md -t gfm
```

Jekyll uses kramdown to handle markdown file while it will change syntax in LaTeX equation.
To show the equation properly, we need to disable these changes.
Putting the content having equations between  `<p>` and `</p>` will do so.

The last step is to render these equations.
By adding 
```html
    <script type="text/javascript" id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>
```
in the `<head>` of `_layouts/default.html`, the inline equation (between `\(` and `\)`) and display equation (between `\[` and `\]`) will be rendered automatically.

For example:

<p> \[ x^n + y^n = z^n \] </p>
