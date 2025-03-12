---
title: testing equations in quarto hugo-md export
format:
  hugo-md:
    toc: false
    preserve_yaml: true
output:
  hugo-md:
    maths: true
---


This file should be rendered with

    quarto render hugomd_testing.qmd --to hugo-md

# Fourier Series Decomposition

$$ c_{n} = \frac{1}{T}\sum\limits_{t=0}^{T} e^{-2\pi i n \frac{t}{T}} \cdot f(t) $$

This is executed $\forall n>0$

# ... and its inversion

\[ f(t) = \sum\limits_{n=0}^{N} (2\cdot c_{n})\cdot e^{2\pi i n \frac{t}{T}} \]

becomes:

\[ f(t) = *{n=0}^{N} (2c*{n})e^{2i n } \]

I am losing my ( )!

# the hugo example

[(from here)](https://gohugo.io/content-management/mathematics)

This is an inline (a^*=x-b^*) equation.

These are block equations:

\[a^*=x-b^*\]

\[ a^*=x-b^* \]

\[
a^*=x-b^*
\]

These are also block equations:

$$a^*=x-b^*$$

$$ a^*=x-b^* $$

$$
a^*=x-b^*
$$

# resources

-   <https://quarto.org/docs/reference/formats/markdown/gfm.html#format-options>
-   <https://pandoc.org/chunkedhtml-demo/3.6-math-rendering-in-html.html>
-   <https://quarto.org/docs/output-formats/gfm.html#webtex-math>

<!-- -->

    pandoc --list-extensions=gfm

I have tested the different `html-math-method` options.
`gladtex` might work with dollars:
`html-math-method: gladtex`
