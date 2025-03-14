---
title: ''
from: markdown+tex_math_single_backslash
html-math-method: mathjax
format:
  hugo-md:
    toc: false
    preserve_yaml: true
    maths: true
    variant: '-tex_math_dollars+tex_math_single_backslash'
---


I am *not* losing my \(\sigma\) anymore!

(thanks to help here: <https://github.com/quarto-dev/quarto-cli/discussions/12272>)

... because I can convert tex maths with the `variant` yaml-options:

``` yaml
    variant: -tex_math_dollars+tex_math_single_backslash
```

So I get the output I expect!

\[ f(t) = \sum\limits_{n=0}^{N} (2\cdot c_{n})\cdot e^{2\pi i n \frac{t}{T}} \]

exports perfectly equivalent to

\[ f(t) = \sum\limits_{n=0}^{N} (2\cdot c_{n})\cdot e^{2\pi i n \frac{t}{T}} \]

as do \(\sigma\) and \(\sigma\).

# quarto markdown syntax

Official **quarto markdown** syntax for maths are the dollar signs.

On the "pandoc input" side, one can steer the interpreter to a different document type with `from:` yaml option, but then the `qmd` file type is misleading.
For example:

``` yaml
from: markdown+tex_math_single_backslash
```

For "pandoc output", the `format` block is crucial, and `variant` gives options.

A **list of applicable pandoc extensions** can be found with `pandoc --list-extensions=markdown`.
The `-/+` prefix indicates whether they are active by default.

The yaml option `variant: gfm+footnotes+tex_math_gfm` ~~seems to be irrelevant~~ must be in the `format` options

# note on html math engine

There are several options for the `html-math-method`:

-   webtex works with inline `$` because it is included as webtex.
-   mathjax, gladtex, mathml... cannot handle the inline dollar signs.

# Testing

## dollar signs

\[ c_{n} = \frac{1}{T}\sum\limits_{t=0}^{T} e^{-2\pi i n \frac{t}{T}} \cdot f(t) \]

This is executed \(\forall n>0\)

## brackets

\[ f(t) = \sum\limits_{n=0}^{N} (2\cdot c_{n})\cdot e^{2\pi i n \frac{t}{T}} \]

becomes:

\[ f(t) = \sum\limits_{n=0}^{N} (2\cdot c_{n})\cdot e^{2\pi i n \frac{t}{T}} \]

> **Tip**
>
> this was solved by adding yaml
> `from: markdown+tex_math_single_backslash`

## the hugo example

[(from here)](https://gohugo.io/content-management/mathematics)

This is an inline \(a^*=x-b^*\) equation.

These are block equations:

\[a^*=x-b^*\]

\[ a^*=x-b^* \]

\[
a^*=x-b^*
\]

These are also block equations:

\[a^*=x-b^*\]

\[ a^*=x-b^* \]

\[
a^*=x-b^*
\]

# resources

-   <https://quarto.org/docs/reference/formats/markdown/gfm.html#format-options>
-   <https://pandoc.org/chunkedhtml-demo/3.6-math-rendering-in-html.html>
-   <https://quarto.org/docs/output-formats/gfm.html#webtex-math>
-   <https://github.com/quarto-dev/quarto-cli/issues/12263>
-   <https://github.com/quarto-dev/quarto-cli/discussions/11753>
-   <https://github.com/quarto-dev/quarto-cli/discussions/12272>

<!-- -->

    pandoc --list-extensions=gfm
    pandoc --list-extensions=markdown
