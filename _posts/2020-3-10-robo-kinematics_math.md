---
layout: post
title: "Kinematics & Math Foundations"
date: 2020-3-10 22:29:53 +0900
permalink: /robo/kmf/
header-includes:
- \usepackage{amsmath}
- \usepackage{mathtools}
---
Roadmap:
- Linear Transformations

&emsp;<a name="Linear Transformations"></a>
### Linear Transformations

- $i$ th training example: $(x^{(i)},y^{(i)}) \| x\in \mathbb{R}^n, y\in \{0,1\}$
- $m$ = # training examples
- $n$ = # features
- $x_j$ = the $j$th feature (assume $x_0=1$)
- $w_j$ = the weight for $j$th feature (assume $w_0=b:\sum_{i=1}^{n}w_i x_i+b = \sum_{i=0}^{n}w_i x_i$)
- $\hat{y}=h(x)$= the hypothetical model

&emsp;<a name="linreg"></a>
## Linear Regression

- Model

$$\begin{equation}
\hat{y}=\sum_{i=0}^{n}w_ix_i=w^Tx
\end{equation}$$

- **Cost Function (OLS)**

$$\begin{equation*}
\mathcal{L}(w)=\frac{1}{2}\sum_{i=1}^{m}(\hat{y}^{(i)}-y^{(i)})^2
\end{equation*}$$

- **Gradient Descent**

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
    
- **Normal Equation** (the exact solution)

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
        
    2. Likelihood Function
    
        $$\begin{equation}
        L(w)=\prod_{i=1}^{m}p(y^{(i)}|x^{(i)},w)=\prod_{i=1}^{m}\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(y^{(i)}-w^Tx^{(i)})^2}{2\sigma^2}}
        \end{equation}$$
        
    3. **Log Likelihoood**
      
        $$\begin{align}
        \mathcal{l}(w)&=\log{L(w)} \\
        &=\log{\prod_{i=1}^{m}\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(y^{(i)}-w^Tx^{(i)})^2}{2\sigma^2}}} \\
        &=\sum_{i=1}^{m}\log{\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(y^{(i)}-w^Tx^{(i)})^2}{2\sigma^2}}} \\
        &=m\log{\frac{1}{\sqrt{2\pi}\sigma}}-\frac{1}{2\sigma^2}\sum_{i=1}^{m}(y^{(i)}-w^Tx^{(i)})^2
        \end{align}$$
    
        Why log?
        
        1. log = monotonic & increasing on $[0,1]\rightarrow$  
        
            $$\mathop{\arg\max}_ {w}L(w)=\mathop{\arg\max}_ {w}\log{L(w)}$$
            
        2. log simplifies calculation (especially & obviously for $\prod$)
        
    4. **MLE** (Maximum Likelihood Estimation)
    
        $$\begin{align}
        \mathop{\arg\max}_ {w}\mathcal{l}(w)&=\mathop{\arg\max}_ {w}(m\log{\frac{1}{\sqrt{2\pi}\sigma}}-\frac{1}{2\sigma^2}\sum_{i=1}^{m}(y^{(i)}-w^Tx^{(i)})^2) \\
        &=\mathop{\arg\max}_ {w}(-\sum_{i=1}^{m}(y^{(i)}-w^Tx^{(i)})^2) \\
        &=\mathop{\arg\min}_ {w}\sum_{i=1}^{m}(y^{(i)}-w^Tx^{(i)})^2
        \end{align}$$

<br/><a name="lwr"></a>
### <strong>Locally Weighted Linear Regression (LWR)</strong>
1. Original LinReg

    $$\begin{equation}
    w\leftarrow\mathop{\arg\min}_ {w}\sum_{i=1}^{m}(y^{(i)}-w^Tx^{(i)})^2
    \end{equation}$$

    We find the $w$ that minimizes the cost function that in turn maximizes the likelihood function so that our linear regression model is optimized to fit the data.

2. LWR

    $$\begin{equation}
    w\leftarrow\mathop{\arg\min}_ {w}\sum_{i=1}^{m}e^{-\frac{(x^{(i)}-x)^2}{2\tau^2}}\cdot(y^{(i)}-w^Tx^{(i)})^2
    \end{equation}$$

    We add the weight function $W^{(i)}=e^{-\frac{(x^{(i)}-x)^2}{2\tau^2}}$ to change the game.

    What game?
    - **Underfitting**: the model barely fits the data points.

        <center><img src="../../images/ML/underfit.png" height="200"/></center>

        One single line is usually not enough to capture the pattern of $x\ \&\ y$. In order to get a better fit, we add more polynomial features ($x^j$) to the original model:

    - **Overfitting**: the model fits the given data points too well that it cannot be used on other data points

        <center><img src="../../images/ML/overfit.png" height="200"/></center>

        When we add too much (e.g. $y=\sum_{j=0}^{6}w_jx^j$), the model captures the pattern of the given data points $(x^{(i)},y^{(i)})$ too much that it cannot perform well on new data points.

    How can LWR change the game?
    - When we would like to estimate $y$ at a certain $x$, instead of applying the original LinReg, we take a subset of data points $(x^{(i)},y^{(i)})$ around $x$ and try to do LinReg on that subset only so that we can get a more accurate estimation. 
    - numerator

    $$\begin{align}
    &\text{If}\ |x^{(i)}-x|=\text{small} \longrightarrow W^{(i)}\approx 1 \\
    &\text{If}\ |x^{(i)}-x|=\text{large} \longrightarrow W^{(i)}\approx 0
    \end{align}$$

    - bandwidth parameter: $\tau$ (how fast the weight of $x^{(i)}$ falls off the query point $x$)

<br/><a name="newton"></a>
### Gradient Descent: <strong>Newton's Method</strong>
1. Newton's formula

    $$\begin{equation}
    w := w-\frac{f(w)}{f'(w)}
    \end{equation}$$

2. Newton-Raphson Method in GD

    $$\begin{equation}
    w := w-H^{-1}\nabla_wl(w)
    \end{equation}$$

    $H$: Hessian Matrix

    $$\begin{equation}
    H_{ij}=\frac{\partial^2l(w)}{\partial w_i \partial w_j}
    \end{equation}$$

3. Newton vs normal GD
    - YES: faster convergence, fewer iterations
    - NO:  expensive computing (inverse of a matrix)

&emsp;<a name="logreg"></a>
## Logistic Regression (Classification)

- Model

    $$\begin{equation}
    \hat{y}=g(w^Tx)
    \end{equation}$$

    $g(z)$: a function that converts $w^Tx$ to binary value

- Sigmoid Function (see Deep Learning for more funcs)

    $$\begin{equation}
    g(z)=\sigma(z)=\frac{1}{1+e^{-z}}
    \end{equation}$$
    
    - Derivative (you will know why we need this in Deep Learning)
    
        $$\begin{align}
        g'(z)&=\frac{d}{dz}\frac{1}{1+e^{-z}} \\
        &=\frac{e^{-z}(+1-1)}{(1+e^{-z})^2} \\
        &=g(z)(1-g(z))
        \end{align}$$

- Cost Function


    1. single training example (derivation later)
    
        $$\begin{equation}
        \mathcal{L}(\hat{y},y)=-(y\log{\hat{y}}+(1-y)\log{(1-\hat{y})})
        \end{equation}$$
        
        If $y=1\rightarrow\mathcal{L}(\hat{y},y)=-\log{\hat{y}}\rightarrow$ want "$\mathcal{L}\downarrow\leftrightarrow\hat{y}\uparrow$"$\rightarrow\hat{y}=1$   
        If $y=0\rightarrow\mathcal{L}(\hat{y},y)=-\log{(1-\hat{y})}\rightarrow$ want "$\mathcal{L}\downarrow\leftrightarrow\hat{y}\downarrow$"$\rightarrow\hat{y}=0$ 
        
    2. entire training set
    
        $$\begin{equation}
        \mathcal{J}(w)=\frac{1}{m}\sum_{i=1}^{m}\mathcal{L}(\hat{y}^{(i)},y^{(i)})=\text{mean}(\mathcal{L})
        \end{equation}$$

- Probabilistic Interpretation

    1. Assumptions
    
        $$\begin{align}
        P(y=1|x,w)&=\hat{y} \\
        P(y=0|x,w)&=1-\hat{y}
        \end{align}$$

    2. Probabilistic Model of LogReg
    
        $$\begin{equation}
        p(y|x,w)=\hat{y}^y(1-\hat{y})^{1-y}
        \end{equation}$$
        
    3. Likelihood Function
    
        $$\begin{equation}
        L(w)=\prod_{i=1}^{m}(\hat{y}^{(i)})^{y^{(i)}}(1-\hat{y}^{(i)})^{1-y^{(i)}}
        \end{equation}$$
        
    4. Log Likelihood
    
        $$\begin{align}
        l(w)&=\sum_{i=1}^{m}(y^{(i)}\log{\hat{y}^{(i)}}+(1-y^{(i)})\log{(1-\hat{y}^{(i)})}) \\
        l(w)&=-\sum_{i=1}^{m}\mathcal{L}(\hat{y},y)
        \end{align}$$
        
    5. MLE
        
        $$\begin{align}
        \frac{\partial l(w)}{\partial w_j}&=(\frac{y}{g(w^Tx)}-\frac{1-y}{1-g(w^Tx)})\frac{\partial g(w^Tx)}{\partial w_j} \\
        &=(\frac{y}{g(w^Tx)}-\frac{1-y}{1-g(w^Tx)})g(w^Tx)(1-g(w^Tx))\frac{\partial(w^Tx)}{\partial w_j} \\
        &=(y(1-g(w^Tx))-(1-y)g(w^Tx))x_j \\
        &=(y-\hat{y})x_j
        \end{align}$$

- Gradient Descent

    $$\begin{align}
    w_j &:= w_j-\alpha\frac{\partial\mathcal{L}(w)}{\partial w_j} \\
    &=w_j+\alpha(y-\hat{y})x_j
    \end{align}$$
    
    Why is it also called "Gradient Ascent"?  
    $\because$ we are trying to minimize the loss function $\Leftrightarrow$ maximize the likelihood function

&emsp;<a name="glm"></a>
## Generalized Linear Models (GLM)

- What are **GLM**s?  

    Remember the two models we had in the last post?  
    Regression:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$p(y|x,w)\sim N(\mu,\sigma^2)$  
    Classification: &nbsp;&nbsp;$p(y|x,w)\sim \text{Bernoulli}(\phi)$  
    
    They belong to GLM, a collection of models that can be applied to Supervised Learning problems. We will show more examples of GLMs in this markdown.

- **Exponential Family**

    $$\begin{equation}
    p(y,\eta)=b(y)\cdot e^{\eta^TT(y)-a(\eta)}
    \end{equation}$$
    
    1. $\eta$: natural parameter (i.e. canonical parameter)  
        
        &emsp;different $\eta \rightarrow$ different distributions within the family
        
    2. $T(y)$: sufficient statistic (usually, $T(y)=y$)  
        
    3. $a(\eta)$: log partition function  
        
    4. $e^{-a(\eta)}$: normalization constant (to ensure that $\int{p(y,\eta)dy}=1$) 
        
    5. $T,a,b$: fixed choice that defines a family of distributions parametrized by $\eta$

<br/><a name="bernoulli"></a>
- **Bernoulli Distribution** (Classification)

    $$\begin{align}
    p(y|\phi)&=\phi^y(1-\phi)^{1-y} \\
    &=e^{y\log{\phi}+(1-y)\log{(1-\phi)}} \\
    &=e^{y\log{\frac{\phi}{1-\phi}}+\log{(1-\phi)}} \\
    \end{align}$$
    
    1. $\eta=\log{\frac{\phi}{1-\phi}}\Leftrightarrow \phi=\frac{1}{1+e^{-\eta}}$
        
    2. $T(y)=y$
        
    3. $a(\eta)=\log{(1+e^\eta)}$
        
    4. $b(y)=1$

<br/><a name="gaussian"></a>
- **Gaussian Distribution** (Regression)

    $$\begin{align}
    p(y|\mu,\sigma^2)&=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{1}{2\sigma^2}(y-\mu)^2} \\
    &=\frac{1}{\sqrt{2\pi}}e^{\frac{\mu}{\sigma^2}y-\frac{1}{2\sigma^2}y^2-\frac{1}{2\sigma^2}\mu^2-\log{\sigma}}
    \end{align}$$
    
    1. $\eta=\begin{bmatrix}
           \frac{\mu}{\sigma^2} ;
           \frac{-1}{2\sigma^2}
          \end{bmatrix}$
              
    2. $T(y)=\begin{bmatrix}
           y;
           y^2
          \end{bmatrix}$
              
    3. $a(\eta)=\frac{1}{2\sigma^2}\mu^2-\log{\sigma}=-\frac{\eta_1^2}{4\eta_2}-\frac{1}{2}\log{(-2\eta_2)}$
        
    4. $b(y)=\frac{1}{\sqrt{2\pi}}$

<br/><a name="poisson"></a>
- **Poisson Distribution** (count-data)

    $$\begin{align}
    p(y|\lambda)&=\frac{\lambda^ye^{-\lambda}}{y!}\\
    &=\frac{1}{y!}e^{y\log{\lambda}-\lambda}
    \end{align}$$
    
    1. $\eta=\log{\lambda}$
        
    2. $T(y)=y$
        
    3. $a(\eta)=e^\eta$
        
    4. $b(y)=\frac{1}{y!}$  

<br/><a name="gamma"></a>
- **Gamma Distribution** (continuous non-negative random variables)

    $$\begin{align}
    p(y|\lambda,a)&=\frac{\lambda^ay^{a-1}e^{-\lambda y}}{\Gamma(a)}\\
    &=\frac{y^{a-1}}{\Gamma(a)}e^{-\lambda y+a\log{\lambda}}
    \end{align}$$
    
    1. $\eta=-\lambda$
        
    2. $T(y)=y$
        
    3. $a(\eta)=-a\log{(-\eta)}$
        
    4. $b(y)=\frac{y^{a-1}}{\Gamma(a)}$  

<br/><a name="beta"></a>
- **Beta Distribution** (distribution of probabilities)

    $$\begin{align}
    p(y|\alpha,\beta)&=\frac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)\Gamma(\beta)}y^{\alpha-1}(1-y)^{\beta-1} \\
    &=\frac{(1-y)^\beta}{y(1-y)\Gamma(\beta)}e^{\alpha\log{y}- \log{\frac{\Gamma(\alpha)}{\Gamma(\alpha+\beta)}}} \\
    &=\frac{y^\alpha}{y(1-y)\Gamma(\alpha)}e^{\beta\log{(1-y)}- \log{\frac{\Gamma(\beta)}{\Gamma(\alpha+\beta)}}}
    \end{align}$$
    
    1. $\eta=\alpha\ \text{or}\ \beta$
        
    2. $T(y)=\log{y}\ \text{or}\ \log{(1-y)}$
        
    3. $a(\eta)=\log{\frac{\Gamma(\eta)}{\Gamma(\alpha+\beta)}}$
        
    4. $b(y)=\frac{(1-y)^\beta}{y(1-y)\Gamma(\beta)}\ \text{or}\ \frac{y^\alpha}{y(1-y)\Gamma(\alpha)}$  

<br/><a name="dirichlet"></a>
- **Dirichlet Distribution** (multivariate beta)

    $$\begin{align}
    p(y|\alpha)&=\frac{\Gamma(\sum_k\alpha_k)}{\prod_k\Gamma(\alpha_k)}\prod_k{y_k^{\alpha_k-1}} \\
    &=\exp{\big(\sum_k{(\alpha_k-1)\log{y_k}}-\big[\sum_k{\log{\Gamma(\alpha_k)}}-\log{\Gamma(\sum_k{\alpha_k})}\big]\big)}
    \end{align}$$
    
    1. $\eta=\alpha-1$
        
    2. $T(y)=\log{y}$
        
    3. $a(\eta)=\sum_k{\log{\Gamma(\alpha_k)}}-\log{\Gamma(\sum_k{\alpha_k})}$
        
    4. $b(y)=1$

<br/><a name="construct"></a>
### Method of Constructing GLMs

- 3 Assumptions
    
    1. $y\|x,w \sim \text{ExponentialFamily}(\eta)$
    
        $y$ given $x\&w$ follows some exponential family distribution with natural parameter $\eta$
        
    2. $h(x)=\text{E}[y\|x]$
    
        Our hypothetical model $h(x)$ should predict the expected value of $y$ given $x$
    
    3. $\eta=w^Tx$
    
        $\eta$ is linearly related to $x$
    
- Example 1: OLS (Ordinary Least Squares) (i.e. LinReg)

    $$\begin{align}
    h(x)&=\text{E}[y\|x,w]\ \ \ \ \ \ &\text{(Assumption 2)} \\
       &=\mu \\
       &=\eta\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ &\text{(Assumption 1)} \\
       &=w^Tx\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ &\text{(Assumption 3)}
    \end{align}$$
    
- Example 2: Logistic Regression

    $$\begin{align}
    h(x)&=\text{E}[y\|x,w]\ \ \ \ \ \ &\text{(Assumption 2)} \\
       &=\phi \\
       &=\frac{1}{1+e^{-\eta}}\ \ \ \ \ \ &\text{(Assumption 1)} \\
       &=\frac{1}{1+e^{-w^Tx}}\ \ \ \ \ \ &\text{(Assumption 3)}
    \end{align}$$
    
- Example 3: <a name="softmax"></a>**Softmax Regression**
    
    1. Softmax is a method used in **multiclass classification** to select one output value $\phi_i$ of the highest probability among all the output values.
        
        $$\begin{equation}
        \hat{y}=\begin{bmatrix}
        \phi_1 \\
        \vdots \\
        \phi_{k-1}
        \end{bmatrix}
        \end{equation}$$
        
    2. **One-hot Encoding**
        
        $$\begin{equation}
        y\in \{ 1,\cdots,k \} \Rightarrow T(y)\in \mathbb{R}^{k}
        \end{equation}$$  
        
        where
        
        $$\begin{equation}
        T(1)=\begin{bmatrix}
        1 \\ 0 \\ \vdots \\ 0
        \end{bmatrix},
        T(2)=\begin{bmatrix}
        0 \\ 1 \\ \vdots \\ 0
        \end{bmatrix},\cdots,
        T(k)=\begin{bmatrix}
        0 \\ 0 \\ \vdots \\ 1
        \end{bmatrix}
        \end{equation}$$
    
    3. **Dummy Encoding**

        
        $$\begin{equation}
        y\in \{ 1,\cdots,k \} \Rightarrow T(y)\in \mathbb{R}^{k-1}
        \end{equation}$$  
        
        where
        
        $$\begin{equation}
        T(1)=\begin{bmatrix}
        1 \\ 0 \\ \vdots \\ 0
        \end{bmatrix},
        T(2)=\begin{bmatrix}
        0 \\ 1 \\ \vdots \\ 0
        \end{bmatrix},\cdots,
        T(k-1)=\begin{bmatrix}
        0 \\ 0 \\ \vdots \\ 1
        \end{bmatrix},
        T(k)=\begin{bmatrix}
        0 \\ 0 \\ \vdots \\ 0
        \end{bmatrix}
        \end{equation}$$
        
        Why Dummy Encoding > One-hot Encoding? It reduces 1 entire column!
    
    4. Indicator Function
    
        $$\begin{equation}
        \text{I}\{ \text{True} \}=1,\ \text{I}\{ \text{False} \}=0
        \end{equation}$$
        
        Therefore,
        
        $$\begin{equation}
        T(y)_i =\text{I}\{ y=i \}
        \end{equation}$$
        
        Therefore,
        
        $$\begin{equation}
        \text{E}[T(y)_i] =P(y=i)=\phi_i
        \end{equation}$$
        
    5. Exponential Family form
    
        $$\begin{align}
        p(y|\phi)&=\prod_{i=1}^{k}{\phi_i^{\text{I}\{ y=i \}}} \\
        &=\prod_{i=1}^{k-1}{\phi_i^{T(y)_i}} \cdot \phi_k^{1-\sum_{i=1}^{k-1}{T(y)_i}} \\
        &=\exp{\big(\sum_{i=1}^{k-1}{T(y)_i\log{(\phi_i)}-\sum_{i=1}^{k-1}{T(y)_i}\log{(\phi_k)}}+\log{(\phi_k)}\big)} \\
        &=\exp{\big(\sum_{i=1}^{k-1}{T(y)_i\log{\big(\frac{\phi_i}{\phi_k}\big)}+\log{(\phi_k)}\big)}} \\
        \end{align}$$

        1. $\eta=\begin{bmatrix}\log{\big(\frac{\phi_1}{\phi_k}\big)}\ ;\ \cdots\ ;\ \log{\big(\frac{\phi_{k-1}}{\phi_k}\big)}\end{bmatrix}$
              
        2. $T(y)=\begin{bmatrix}T(y)_1\ ;\ \cdots\ ;\ T(y)_k-1\end{bmatrix}$

        3. $a(\eta)=-\log{(\phi_k)}$

        4. $b(y)=1$  
        &nbsp;
    
    6. **Softmax Function** (derived from $\eta_i=\log{\big(\frac{\phi_i}{\phi_k}\big)}$)
    
        $$\begin{equation}
        \phi_i=\frac{e^{\eta_i}}{\sum_{j=1}^k{e^{\eta_j}}}
        \end{equation}$$
        
    7. Probabilistic Interpretation of Softmax Regression
    
        $$\begin{equation}
        p(y=i|x,w)=\frac{e^{w_i^Tx}}{\sum_{j=1}^k{e^{w_i^Tx}}}
        \end{equation}$$
    
    8. Log Likelihood
    
        $$\begin{align}
        l(w)&=\sum_{i=1}^m{\log{p(y^{(i)}|x^{(i)},w)}} \\
        &=\sum_{i=1}^m{\log{\prod_{i=1}^{k}{\Bigg(\frac{e^{w_l^Tx^{(i)}}}{\sum_{j=1}^k{e^{w_l^Tx^{(i)}}}}\Bigg)^{\text{I}\{ y^{(i)}=l \}}}}}
        \end{align}$$
            