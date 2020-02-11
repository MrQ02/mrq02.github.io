---
layout: post
title: "Products & Markets"
date: 2019-12-01 22:29:53 +0900
permalink: /quant/promar/
header-includes:
- \usepackage{amsmath}
- \usepackage{mathtools}
---

- **Products & Markets**
    - [Time Value of Money](#tvm)
    - [Activation Functions](#af)
    - Training
        - [Forward Propagation](#fp)
        - [Backward Propagation](#bp)
        - Example: [Forward & Backward Step: Stochastic](#fbss)
        - Example: [Forward & Backward Step: Mini-batch](#fbsb)
        - [Reverse Differentiation](#rd) (for a clearer understanding of backpropagation)
    - [Gradient Descent](#gd)
    
&emsp;<a name="tvm"></a>
## Time Value of Money

- **Interest**:

- **Simple Interest**: interest based on initial investment
    
- **Compound Interest**: interest based on initial investment + interest
    - **Discrete Compounding**: 
    
        $$\begin{equation}
        FV=PV\big(1+\frac{r}{m}\big)^{mn}
        \end{equation}$$
        
        - $PV$: present value of your investment
        - $FV$: future value of your investment
        - $r$: annual interest rate
        - $m$: #times you receive interest per annum
        - $n$: #years

    - **Continuous Compounding**:
    
        $$\begin{equation}
        \lim_{m\to\infty} \big(1+\frac{r}{m}\big)^{m}=e^r \\
        FV=PV\cdot e^{rn}
        \end{equation}$$
