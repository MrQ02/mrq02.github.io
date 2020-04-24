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
- [Options](#opt)

&emsp;<a name="tvm"></a>
### Time Value of Money

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
- **Law of 72**: the calculation of how many years it takes to double my money

    $$\begin{equation}
    n\times (r\times100)\approx72
    \end{equation}$$

    Derivation:
    
    $$\begin{align}
    (1+r)^n&=2 \\
    n&=\log_{1+r}{2} \\
    n&\approx\frac{72}{r\times100}  
    \end{align}$$

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

- **Forwards vs Futures**

    | Forwards | Futures |
    |:--------:|:-------:|
    | the **obligation** to buy an asset<br>at some **specific time** (i.e. **maturity**)<br>at some **specific price** | the **obligation** to buy an asset<br>with a **gradual price settling** (daily) until maturity |
    | Can be privately negotiated | highly standardized |
    | OTC | exchange |
    | high counterparty risk (one party defaults) | high liquidity (can be traded whenever) | 

- **No-Arbitrage Principle**: There is <strong><u>NO risk-free profit</u></strong> in the financial markets

    - Example: simple portfolio
    
        <center><img src="../../images/quant/simpleport.png" height="200"/></center>
    
        1. $A$ receives a forward contract from $B$.
        
        2. At time $t$, $A$ goes short (sells the asset to $C$) and receives $S(t)$, the spot price of the forward contract at $t$.
        
        3. $A$ puts $S(t)$ into the bank and receives interest till time $T$.
        
        4. At time $T$, i.e. maturity date, $A$ receives the asset and gives $F$ to $B$. $A$'s net position becomes $S(t)e^{r(T-t)}-F$.
        
            Eventually, the following holds:
        
            - If you perceive that $S(t)e^{r(T-t)}>F$, you go along with the forward contract and make riskless profit.
            - If you perceive that $S(t)e^{r(T-t)}<F$, you short the forward contract and make riskless profit.  
            
            But macro-wise, this will never happen since investors will smell this fresh meat and come for it. Price will automatically adjust to eliminate such riskless profit.
            
        5. Eventually, you end up with:
        
            $$\begin{equation}
            S(t)e^{r(T-t)}=F
            \end{equation}$$

&emsp;<a name="opt"></a>
### Options

- **Call Option**: the **right** to **buy** a particular asset for an agreed amount at a specific time.

    - **Exercise/Strike Price**: the agreed amount
    - **Expiry**: the specific time
    - **Underlying Asset**: the particular asset
    
    - **Payoff Function**: our return on the option
    
        $$\begin{equation}
        \max{(S-E,0)}
        \end{equation}$$
        
        - $S$: asset price
        - $E$: strike price
        - $S>E\Rightarrow$ let's do this
        - $S<E\Rightarrow$ nahh let's chill  
<br>
- **Put Option**: the **right** to **sell** a particular asset for an agreed amount at a specific time.

    - **Payoff Function**:
    
        $$\begin{equation}
        \max{(E-S,0)}
        \end{equation}$$
        
<br>
- Factors affecting derivatives prices:

    - **Variables**:
    
        - $S$: underlying
        - $t$: time to expiry  
    <br>
    - **Parameters**:
    
        - interest rate
        - strike price
        - **volatility**: a measure of #fluctuation in $S$ (i.e. a measure of randomness)  
<br>
<br>
- **Leverage**

    - Today is 2020/04/08. The price of Microsoft (MSFT)'s stock is $163.49.
    - The cost of a 165 call option with expiry 2020/04/15 is $10.
    - You would like to profit off the expectation that the stock price will rise dramatically within this week. You have two choices:
    
        1. Buy the stock
        
            - You buy the stock at $163.49 on 2020/04/08.
            - The stock price becomes $180 on 2020/04/15.
            - Your return on investment will be: $\frac{180-163.49}{163.49}\times 100\% =10.10\%$.  
        <br>
        2. Buy the call
        
            - You buy the call at $10 on 2020/04/08.
            - The stock price becomes $180 on 2020/04/15.
            - Your return on investment will be: $\frac{180-165-10}{10}\times 100\% =50\%$.  
    <br>
    - This is an example of leverage, where you expect to get a significantly higher payoff for a small investment. The downside is the risk of facing 100% loss with buying the option.
    
    - **Hedging**: the offsetting of the writer's risk of writing a highly-leveraged contract by buying other related contracts.  
<br>
<br>
- The confusing & fancy terms

    - **Premium**: the amount paid for the contract
    
    - **Intrinsic value**: the payoff that would be received if the underlying is at its current level when the option expires
    
    - **Time value**: any value that the option has above its intrinsic value
    
    - **In the money**: an option with positive intrinsic value
    
    - **Out of the money**: an option with no intrinsic value
    
    - **At the money**: a call/put with a strike $\approx$ current asset level
    
    - **Long position**: a positive amount of a quantity
    
    - **Short position**: a negative amount of a quantity
    
    - **Writing options**: The writer of an option promises to deliver the underlying asset, if the option is a call or buy the asset if the option is a put. The writer receives the premium but faces obligations in the future.
    
        The purchaser faces a <u>limited downside</u> of initial premium but an <u>unlimited upside</u>.  
        The writer faces a <u>limited upside</u> of guaranteed payment but an <u>unlimited downside</u>.  
        
    - **Clearing houses**: register & settle options on the deposit of a margin by the writers (<s>default risk)
    
    - **Initial margin**: the amount deposited at the intiation of the contract.  
<br>
<br>
- Types of options by exercise:

    - **European Options**: exercise is only permitted at expiry.
    
    - **American Options**: exercise is permitted at any time before expiry.
    
    - **Bermudan Options**: exercise is permitted on specified dates / in specified periods.  
<br>
<br>
- **Put-Call Parity**

    - On day $t$, you buy an European call option with a strike of $E$ and an expiry of $T$ and write an European put option with the same values.
    - You now hold a portfolio of a long call and a short put with the payoff of:
    
        $$\begin{align}
        &\text{Today (at t): }\ \ \ \ \ \ \ C-P=S(t)-Ee^{-r(T-t)} \\
        &\text{Future (at T):}\ \ \ \ \ \ \max{(S(T)-E,0)}-\max{(E-S(T),0)}=S(T)-E
        \end{align}$$
        
    - Note that the first equation shows that: long call + short put = long asset + short cash
    - <u>Put-Call Parity</u>: this equality of CF is independent of the future, meaning that it holds at any time up to expiry.  
<br>
<br>
- **Binary/Digital Options**: options with a fixed payoff discontinuous in $S$

    - <u>Intuition</u>: instead of getting the difference between the underlying $S$ and the strike $E$ as your payoff, you get a **fixed** amount of payoff that is irrelevant to the value of the underlying.
    
        | Binary Call | Binary Put |
        |:-:|:-:|
        | <center><img src="../../images/quant/binary_call.png" height="200"/></center> | <center><img src="../../images/quant/binary_put.png" height="200"/></center> |

        <br>
        As shown in the table, $E=100$.

        For binary call, when $S>E$, you get $1 regardless of how big the difference is.

        For binary put, when $S<E$, you get $1 regardless of how big the difference is.
    
    - <u>Put-Call Parity</u>:
    
        $$\begin{equation}
        \text{Binary call}+\text{Binary put}=E'e^{-r(T-t)}
        \end{equation}$$
        
        where $E'$ represents the payoff value of the binary options.

