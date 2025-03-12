---
title: testing equations in quarto `hugo-md` export
from: markdown+tex_math_single_backslash
html-math-method: webtex
format:
  hugo-md:
    toc: false
    preserve_yaml: true
output:
  hugo-md:
    maths: true
    variant: gfm+footnotes+tex_math_gfm
---


I am losing my ![\sigma](https://latex.codecogs.com/svg.latex?%5Csigma "\sigma")!

-   webtex works with inline `$` because it is included as webtex.
-   mathjax cannot handle the inline dollar signs.
-   gladtex, mathml... do not work

The yaml option `variant: gfm+footnotes+tex_math_gfm` seems to be irrelevant

# dollar signs

![c\_{n} = \frac{1}{T}\sum\limits\_{t=0}^{T} e^{-2\pi i n \frac{t}{T}} \cdot f(t)](https://latex.codecogs.com/svg.latex?c_%7Bn%7D%20%3D%20%5Cfrac%7B1%7D%7BT%7D%5Csum%5Climits_%7Bt%3D0%7D%5E%7BT%7D%20e%5E%7B-2%5Cpi%20i%20n%20%5Cfrac%7Bt%7D%7BT%7D%7D%20%5Ccdot%20f%28t%29 "c_{n} = \frac{1}{T}\sum\limits_{t=0}^{T} e^{-2\pi i n \frac{t}{T}} \cdot f(t)")

This is executed ![\forall n\>0](https://latex.codecogs.com/svg.latex?%5Cforall%20n%3E0 "\forall n>0")

# brackets

\[ f(t) = \sum\limits_{n=0}^{N} (2\cdot c_{n})\cdot e^{2\pi i n \frac{t}{T}} \]

becomes:

![f(t) = \sum\limits\_{n=0}^{N} (2\cdot c\_{n})\cdot e^{2\pi i n \frac{t}{T}}](https://latex.codecogs.com/svg.latex?f%28t%29%20%3D%20%5Csum%5Climits_%7Bn%3D0%7D%5E%7BN%7D%20%282%5Ccdot%20c_%7Bn%7D%29%5Ccdot%20e%5E%7B2%5Cpi%20i%20n%20%5Cfrac%7Bt%7D%7BT%7D%7D "f(t) = \sum\limits_{n=0}^{N} (2\cdot c_{n})\cdot e^{2\pi i n \frac{t}{T}}")

> **Tip**
>
> this was solved by adding yaml
> `from: markdown+tex_math_single_backslash`

# the hugo example

[(from here)](https://gohugo.io/content-management/mathematics)

This is an inline ![a^\*=x-b^\*](https://latex.codecogs.com/svg.latex?a%5E%2A%3Dx-b%5E%2A "a^*=x-b^*") equation.

These are block equations:

![a^\*=x-b^\*](https://latex.codecogs.com/svg.latex?a%5E%2A%3Dx-b%5E%2A "a^*=x-b^*")

![a^\*=x-b^\*](https://latex.codecogs.com/svg.latex?a%5E%2A%3Dx-b%5E%2A "a^*=x-b^*")

![a^\*=x-b^\*](https://latex.codecogs.com/svg.latex?a%5E%2A%3Dx-b%5E%2A "a^*=x-b^*")

These are also block equations:

![a^\*=x-b^\*](https://latex.codecogs.com/svg.latex?a%5E%2A%3Dx-b%5E%2A "a^*=x-b^*")

![a^\*=x-b^\*](https://latex.codecogs.com/svg.latex?a%5E%2A%3Dx-b%5E%2A "a^*=x-b^*")

![a^\*=x-b^\*](https://latex.codecogs.com/svg.latex?a%5E%2A%3Dx-b%5E%2A "a^*=x-b^*")

# resources

-   <https://quarto.org/docs/reference/formats/markdown/gfm.html#format-options>
-   <https://pandoc.org/chunkedhtml-demo/3.6-math-rendering-in-html.html>
-   <https://quarto.org/docs/output-formats/gfm.html#webtex-math>
-   <https://github.com/quarto-dev/quarto-cli/issues/12263>
-   <https://github.com/quarto-dev/quarto-cli/discussions/11753>

<!-- -->

    pandoc --list-extensions=gfm

**from:** markdown+tex_math_single_backslash

**to:**
I have tested the different `html-math-method` options.
`webtex` and `gladtex` work with dollars:
`html-math-method: gladtex`
