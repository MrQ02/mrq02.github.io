---
layout: post
title: "Regression"
date: 2019-12-01 22:29:53 +0900
permalink: /ML/Regression/
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



