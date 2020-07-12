---
title: MathJax rendering
date: 2020-07-06 10:31:26
tags: ["latex", "mathjax", "katex"]
categories: ["Hexo"]
---

https://www.latexlive.com

You'll need to swap out the default Markdown renderer (`hexo-renderer-marked`) for Latex rendering without workaround escape charactors such as `\`, `_`.

<!-- more -->

## Setup

Some of the guide is from [Hexo Next docs](https://theme-next.js.org/docs/third-party-services/math-equations.html)

First, uninstall the default Markdown renderer (`hexo-renderer-marked`)

```bash
npm un hexo-renderer-marked
```

### Option 1: `hexo-renderer-pandoc`

`pandoc` need to be installed in your `PATH`.

```bash
npm un hexo-renderer-marked
```

### Option 2: `hexo-renderer-markdown-it`

You could use `markdown-it-katex` with `hexo-renderer-markdown-it` as in the [Hexo Next docs](https://theme-next.js.org/docs/third-party-services/math-equations.html).

However, I recommend another plugin, `markdown-it-latex2img`[^makergyt], which does server-side rendering of math formulae, powered by <https://math.now.sh/>

## MathJax rendering

See [MathJax quick reference](https://math.meta.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference) for syntax.

The delimiters `$`, `$$` follow the pandoc rule.

### Inline formulae

The left `$` must be followed by a non white-space character. And the right `$` must follow  a non white-space character

- Pythagoras theorem: $a^2+b^2=c^2$
- Sum of arithmetic sequence: $S_{n}=n a_{1}+\frac{n(n-1)}{2} d, n \in N^{*}$
- Fundamental theorem of calculus: $\int_{a}^{b} f(x) d x=F(b)-F(a)=\left.F(x)\right|_{a} ^{b}$
- Binomial distribution: $P_{n}(k)=C_{n}^{k} p^{k} q^{n-k} \quad k=0,1,2 \ldots \ldots, n$

### Block formulae

Normaldistribution $X \sim N(\mu,\sigma^2)$:
$$f(x) = \frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^2}{2\sigma^2}}$$

Fibonacci Sequence $A_n=A_{n-1}+A_{n-2}$, the ratio of two consecutive numbers converges to golden ratio
$$\lim_{n\to \infty}\frac{A_{n-1}}{A_n}=\frac{\sqrt{5}-1}{2}.$$

Factorisation
$$\begin{split}(x−1)(x−3)&=x^2−4x+3 \\ 
&=x^2−4x+4−1 \\ 
&=(x−2)^2−1
\end{split}
$$

Dirichlet function

$$
D(x)=
\begin{cases}
1,& x \in Q \\
0,& x \notin Q
\end{cases}
$$

Gauss's law
$$
\iiint_{\Omega}\left(\frac{\partial P}{\partial x}+\frac{\partial Q}{\partial y}+\frac{\partial R}{\partial z}\right) d v=\iint_{\Sigma} P d y d z+Q d z d x+R d x d y
$$

Vandermonde matrix
$$D_{n-1}=\left|\begin{array}{cccc}
1 & 1 & \dots & 1 \\
x_{2} & x_{3} & \dots & x_{n} \\
\vdots & \vdots & & \vdots \\
x_{2}^{n-2} & x_{3}^{n-2} & \dots & x_{n}^{n-2}
\end{array}\right|=\prod_{2 \leq j<i \leq n}\left(x_{i}-x_{j}\right)$$

System of linear equations

$$\left\{\begin{aligned}
a_{11} x_{1}+a_{12} x_{2}+\cdots+a_{1 n} x_{n} &=b_{1} \\
a_{21} x_{1}+a_{22} x_{2}+\cdots+a_{2 n} x_{n} &=b_{2} \\
\cdots \cdots \cdots \\
a_{m 1} x_{1}+a_{m 2} x_{2}+\cdots+a_{m n} x_{n} &=b_{m}
\end{aligned}\right.$$

### Physics
- Newton's first law: $\sum \vec{F}_{i}=\frac{\mathrm{d} \vec{v}}{\mathrm{d} t}=0$
- Newton's second law: $\vec{F}=\frac{\mathrm{d} m}{\mathrm{d} t} \vec{v}+m \frac{\mathrm{d} \vec{v}}{\mathrm{d} t}=\frac{\mathrm{d} m}{\mathrm{d} t} \vec{v}+m \vec{a}=\frac{\mathrm{d} m}{\mathrm{d} t} \vec{v}+m \frac{\mathrm{d}^{2} \vec{r}}{\mathrm{d} t^{2}}$
- Newton's third law: $\overrightarrow{F_{12}}=-\overrightarrow{F_{21}}$
- Mass–energy equivalence: $E=mc^2$

Law of gravity: $F=\frac{G M m}{r^{2}}$
$$G \frac{m M}{(r+h)^{2}}=m \frac{\nu^{2}}{(r+h)}$$

Kirchhoff Laws
$$\left[\frac{\partial\left(\Delta_{r} H_{m}\right)}{\partial T}\right]_{p}=\sum_{B} v_{B} C_{p, m}(B)$$

Second lawof thermodynamics
$$d S \geq \frac{\delta Q}{T}$$

## Chemistry
Ions and precipitation: $\ce{SO4^2- + Ba^2+ -> BaSO4 v}$

Ammonia synthesis
$$
\ce{N2 + 3H2 <=>T[ heat , pressure][catalyst] 2NH3}
$$

Equilibrium constant:$\mathrm{Zn}+2 \mathrm{HCl}(\mathrm{aq})=\mathrm{H}_{2}+\mathrm{ZnCl}_{2} \quad(\mathrm{aq})$
$$K^{\theta}=\frac{\left[p\left(\mathrm{H}_{2}\right) / p^{\theta}\right]\left[c\left(\mathrm{ZnCl}_{2}\right)\right]}{c^{2}(\mathrm{HC})}$$

## Biology
Photosynthesis
$$\ce{CO2 + 2H2O ->T[Photons][enzymes] CH2O + H2O + O2}$$

[^makergyt]: https://github.com/MakerGYT/markdown-it-latex2img