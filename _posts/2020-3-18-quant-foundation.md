---
layout: post
title: "Financial Foundations"
date: 2020-3-18 22:29:53 +0900
permalink: /quant/foundation/
header-includes:
- \usepackage{amsmath}
- \usepackage{mathtools}
---

Roadmap:
- [Time Value of Money](#tvm)
- [Forwards & Futures](#ff)

&emsp;<a name="tvm"></a>
### Time Value of Money

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

- 

- Comparison: Forwards vs Futures

    | Forwards | Futures |
    |:--------:|:-------:|
    | Party **A** buys an asset from Party **B** at some **specific time** (i.e. **maturity**) at some **specific price** |

- **Forward Contract**: A promises to buy an asset from B at some **specific time** (i.e. **maturity**) in the future at some **specific price**.

- **Futures contract**: similar to a forward contract but the payment takes place gradually until maturity.