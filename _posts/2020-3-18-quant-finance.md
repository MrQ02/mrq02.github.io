---
layout: post
title: "Glossary of Finance"
date: 2019-12-01 22:29:53 +0900
permalink: /quant/finance/
header-includes:
- \usepackage{amsmath}
- \usepackage{mathtools}
---

Roadmap:
- Financial Markets
- [Forwards & Futures](#ff)

&emsp;<a name="tvm"></a>
### Financial Markets

- **Stock** (i.e. equity/share): the ownership of a small piece of a company.

- **Commodities**: raw products (e.g. gold, silver, oil, etc.).

- **Forex** (i.e. foreign exchange/FX): exchange of currencies.

- **Index**: a number generated from the weighted sum of a basket of representative stocks to measure the performance of the stock market.


- **Premium**: #money paid for the contract initially.

- **Underlying (asset)**: the financial instrument on which the option value depends.

- **Strike (price)** (i.e. exercise price): #money for which the underlying can be bought (call) or sold (put)

- **Simple Interest**: interest based on initial investment
    
- **Compound Interest**: interest based on initial investment + interest
    - **Discrete Compounding**: 
    
        $$\begin{equation}
        M(n)=M(0)\big(1+\frac{r}{m}\big)^{mn}
        \end{equation}$$
        
        - $M(n)$: FV of your investment
        - $M(0)$: PV of your investment
        - $r$: annual interest rate
        - $m$: #times you receive interest per annum
        - $n$: #years  
    <br>
    - **Continuous Compounding**:
    
        $$\begin{align}
        &\text{FV}=M(t)=M(0)\cdot e^{rt} \\
        &\text{PV}=M(t)=M(T)\cdot e^{-r(T-t)}
        \end{align}$$

        Derivation 1:
        
        $$\begin{align}
        \lim_{m\to\infty} \big(1+\frac{r}{m}\big)^{mt}&=\lim_{a\to 0} e^{\frac{rt}{a}\ln{(1+a)}} \\
        &=e^{rt\lim_{a\to 0} \frac{\ln{(1+a)}}{a}} \\
        &=e^{rt}
        \end{align}$$
        
        Derivation 2:
        
        $$\begin{align}
        &M(t+dt)-M(t)\approx\frac{dM}{dt}dt+\cdots \\
        &\Rightarrow\frac{dM}{dt}=rM(t)
        \end{align}$$
        
&emsp;<a name="ff"></a>
### Forwards & Futures
