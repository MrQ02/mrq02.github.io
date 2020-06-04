---
layout: post
title: "Differential Equations"
date: 2020-4-25 12:47:53 +0900
permalink: /math/diffeq/
header-includes:
- \usepackage{amsmath}
- \usepackage{mathtools}
---
Roadmap:
- [Linear 1st-Order ODE](#1oode)
- [Linear 2nd-Order ODE](#2oode)

&emsp;<a name="1oode"></a>
### Linear 1st-Order ODE

- Problem

    $$\begin{equation}
    y'+p(x)y=q(x)
    \end{equation}$$

- Solution

    $$\begin{equation}
    y=Ce^{-\int{p(x)dx}}+e^{-\int{p(x)dx}}\times\int{q(x)e^{\int{p(x)dx}}}dx
    \end{equation}$$

- Derivation

    1. Solve for $y_h$:
    
        $$\begin{align}
        y_h'+p(x)y_h&=0 \\
        \int{\frac{dy_h}{y_h}}&=\int{-p(x)dx} \\
        y_h&=e^{-\int{p(x)dx}}
        \end{align}$$

    2. Let $u(x)$ be an integrating factor. Multiply this on both sides:
    
        $$\begin{equation}
        u(x)y'+u(x)p(x)y=u(x)q(x)
        \end{equation}$$
        
    3. Recall product rule $(fg)'=f'g+fg'$. Notice:
    
        $$\begin{align}
        f=y &\Rightarrow f'=y'\\
        g=u(x) &\Rightarrow g'=u(x)p(x) \\
        (fg)'&=u(x)q(x)
        \end{align}$$
        
    4. Solve for $u(x)$:
    
        $$\begin{align}
        u'(x)&=u(x)p(x) \\
        \int{\frac{du}{u}}&=\int{p(x)dx} \\
        u(x)&=e^{\int{p(x)dx}}
        \end{align}$$
        
    5. Solve for $y_g$:
    
        $$\begin{align}
        \big(u(x)y_g\big)'&=u(x)q(x) \\
        u(x)y_g&=\int{u(x)q(x)dx} \\
        y_g&=\frac{\int{u(x)q(x)dx}}{u(x)} \\
        y_g&=\frac{\int{e^{\int{p(x)dx}}q(x)dx}}{e^{\int{p(x)dx}}}
        \end{align}$$
        
