---
layout: post
title: "Regression"
date: 2019-12-01 22:29:53 +0900
permalink: /ML/Regression/
header-includes:
- \usepackage{amsmath}
---

## Notations

- $i$ th training example: $(x^{(i)},y^{(i)}) \| x\in \mathbb{R}^n, y\in \{0,1\}$
- $m$ = # training examples
- $n$ = # features
- $x_j$ = the $j$th feature (assume $x_0=1$)
- $w_j$ = the weight for $j$th feature (assume $w_0=b:\sum_{i=1}^{n}w_i x_i+b = \sum_{i=0}^{n}w_i x_i$)
- $\hat{y}=h(x)$= the hypothetical model

## Linear Regression

- Model

$$\begin{equation}
\hat{y}=\sum_{i=0}^{n}w_ix_i=w^Tx
\end{equation}$$

- Cost Function (OLS)

$$\begin{equation*}
\mathcal{L}(w)=\frac{1}{2}\sum_{i=1}^{m}(\hat{y}^{(i)}-y^{(i)})^2
\end{equation*}$$

- Gradient Descent

    $$\begin{equation*}
    w_j := w_j-\alpha\frac{\partial\mathcal{L}(w)}{\partial w_j}
    \end{equation*}$$

    1. **Batch GD** (LMS) (using the whole training set for each GD step)
    
        $$\begin{equation*}
        w_j = w_j-\alpha\sum_{i=1}^{m}(\hat{y}^{(i)}-y^{(i)})x_j^{(i)}
        \end{equation*}$$
    
    2. **Stochastic GD** (using 1 training example for each GD step)
    
        $$\begin{equation*}
        w_j = w_j-\alpha(\hat{y}^{(i)}-y^{(i)})x_j^{(i)}
        \end{equation*}$$
    
    3. **Mini-batch GD** (using mini-batches of size $m'$ for each GD step)
    
        $$\begin{equation*}
        w_j = w_j-\alpha\sum_{i=1}^{m'}(\hat{y}^{(i)}-y^{(i)})x_j^{(i)}
        \end{equation*}$$
    
- Normal Equation (the exact solution)

    $$\begin{equation*}
    W=(X^TX)^{-1}X^Ty
    \end{equation*}$$

    1. Derivation
    
        $$\begin{align}
        \DeclareMathOperator{\Tr}{tr}
        \nabla_w\mathcal{L}(w)&=\nabla_w\frac{1}{2}(Xw-y)^T(Xw-y) \\
        &=\frac{1}{2}\nabla_w(w^TX^TXw-w^TX^Ty-y^TXw+y^Ty) \\
        &=\frac{1}{2}\nabla_w\Tr(w^TX^TXw-w^TX^Ty-y^TXw+y^Ty) \\
        &=\frac{1}{2}\nabla_w(\Tr(w^TX^TXw)-2\Tr(y^TXw)) \\
        &=\frac{1}{2}(2X^TXw-2X^Ty) \\
        &\Rightarrow X^TXw-X^Ty=0
        \end{align}$$
        
    2. Why GD instead of Normal Equation?  
      A: these matrix operations require too much computing power. GD is relatively much faster.

- Probabilistic Interpretation
    1. Probabilistic Model of Linear Regression
    
        $$\begin{equation}
        p(y^{(i)}|x^{(i)},w)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(y^{(i)}-w^Tx^{(i)})^2}{2\sigma^2}}
        \end{equation}$$
        
        where $y^{(i)}=w^Tx^{(i)}+\epsilon^{(i)}$ and $\epsilon^{(i)}\sim N(0,\sigma)$
        
        
        
        
        
        
        
        