---
layout:     post
title:      Notes on Probability and Stochastic Processes
date:       2024-10-14
author:     MazelTovy
header-img: img/tag-bg-o.jpg
catalog: true
tags:
    - Probability
    - Stochastic Processes
    - Lecture Notes
---
{% raw %}
# Probability and Stochastic Process

## Lecture 1

Scarlett lj2389@nyu.edu

De-Morgan's Laws
$$
\overline{A\cup B}=\overline{A}\cap\overline{B}\\\\
\overline{AB}=\overline{A}\cup\overline{B}\\\\
\overline{\overline{A}}=A
$$
Axioms of probability

1. $P(\Omega)=1$
2. $P(A)\leq 0$
3. $A\cap B=\emptyset$, which means $A$ and $B$ are mutually exclusive, then $P(A\cup B)=P(A)+P(B)$

### Conditional probability and Bayes' Theorem

What means $P(A\mid B)$? Probability of $A$ that $B$ is given, or to say $B$ has occurred.
$$
P(A\mid B)=\frac{P(AB)}{P(B)}
$$
Partition

Several $A_i$ makes the full-set $F$ parts. If $A_i\cap A_j=\emptyset$, then $\bigcup\limits_{n}^{i}A_i=\mathscr{F}$.



example 1.

$m$ black balls and $n$ white balls. Assume $m=10, n=6$, then the probability of "first pick black, second pick white" is
$$
P(B_1\cap W_2)=P(W_2B_1)=P(W_2\mid B_1)P(B_1)=\frac{n}{n+m-1}\cdot\frac{m}{m+n}
$$
If events $A,B$ are independent, $P(AB)=P(A)P(B)$.
$$
P(A_i\mid B)=\frac{P(B\mid A_i)P(A_i)}{P(B)}=\frac{P(B\mid A_i)P(A_i)}{\sum\limits_{j=1}^{n}P(B\mid A_j)P(A_j)}
$$
In a coin tossing game,
$$
P[k\ \text{Heads in}\ n\ \text{tosses}]=N\cdot p^k\cdot q^{n-k}
$$
where
$$
N=\frac{n(n-1)(n-2)\cdots(n-k+1)}{k!}=\frac{n!}{(n-k)!k!}={n \choose k}
$$
therefore
$$
P[k\ \text{Heads in}\ n\ \text{tosses}]={n \choose k}\cdot p^k\cdot q^{n-k}
$$

***

## Lecture 2

Review on $\text{Binomial}(n,p)$.

Assume we have a constant $c$, and $n\rightarrow \infty$, then $\displaystyle P=\frac{c}{n}$, we call event $X$ is a rare event.

If $X$ obeys binomial distribution, then
$$
\begin{eqnarray}
P(X=k)&=&{n\choose k}p^k q^{n-k}\\\\
&=&e^{-\lambda}\frac{\lambda^k}{k!}
\end{eqnarray}
$$
When $X=0$,
$$
P(X=0)=e^{-\lambda}
$$

### Negative-Binomial

$k^{\text{th}}$ success at $n^{\text{th}}$ trial
$$
P(Z)={n-1 \choose k-1}p^{k-1}q^{n-1-(k-1)}\cdot p={n-1\choose k-1}p^kq^{n-k},n=k,k+1,\dots,+\infty
$$
Team $A$ and team $B$ are in a game. The team wins 4 in 7 games wins the game.

Which means $X_k=4^{\text{th}} \text{\ success\ at\ } n^{\text{th}} \text{\ game\ for\ } A$, $A$ can win at $4^{\text{th}}$, $5^{\text{th}}$, $6^{\text{th}}$, $7^{\text{th}}$ game.
$$
\begin{eqnarray}
P(A \text{\ wins})&=& X_4\cup X_5\cup X_6\cup X_7\\\\
&=&\sum^7_{n=4}P(X_n)\\\\
&=&\sum^7_{n=4}{n-1\choose 3}p^{n-1}q^3\cdot q
\end{eqnarray}
$$

### Random variables

$$
\{\xi\mid X(\xi)\leq x \}
$$

$$
P[\xi\mid X(\xi)\leq x]=P(A_x)=\mathcal{F}_X(x)\geq0
$$

Distribution Function Properties $g(x)$

1. $g(x)\geq0$
2. Non-decreasing
3. Right-continuous $g(x_0)=g(x_0^+)$

$\mathcal{F}_X(-\infty)=0,\mathcal{F}_X(+\infty)=1$. $(\xi\mid X(\xi)\leq x_2)=(x_1<x\leq x_2)\cup(x\leq x_1)$.

$P[x_1<X\leq x_2]=\mathcal{F}_X(x_2)-\mathcal{F}_X(x_1)$

$\mathcal{F}_X(x_0^+)=\mathcal{F}_X(x_0)\neq\mathcal{F}_X(x_0^-)$

Actually, $P(X=x_0)=\mathcal{F}_X(x_0)-\mathcal{F}_X(x_0^-)$
$$
\mathcal{f}_X(x)=\frac{\text{d}\mathcal{F}_X(x)}{\text{d}x}=\frac{\mathcal{F}_X(x+\Delta)-\mathcal{F}_X(x)}{\Delta}\geq 0,\Delta>0
$$

$$
\mathcal{F}_X(x_0)=\int_{-\infty}^{x_0}\mathcal{f}_X(x)\text{d}x
$$

$$
\mathcal{F}_X(+\infty)=\int_{-\infty}^{+\infty}\mathcal{f}_X(x)\text{d}x=1
$$

Continuous PDF example: Gaussian/normal distribution
$$
\mathcal{f}_X(x)=\frac{1}{\sqrt{2\pi\sigma^2}}e^{{-(x-\mu)^2}/(2\sigma^2)}
$$
$\text{Uniform}(a,b)$

$x^\alpha(1-x)^\beta\cdot k$

Density Function Properties $\mathcal{f}_X$

1. $\mathcal{f}_X(x)\geq0$
2. $\displaystyle\int^{+\infty}_{-\infty}\mathcal{f}_X(x)\text{d}x=1$

Linear Filter
$$
Y=aX+b
$$

$$
\mathcal{F}_Y(y)=P[Y\leq y]=P(aX+b\leq y)
$$

$$
\mathcal{F}_X(\frac{y-b}{a})=
\left\{\begin{matrix}
P(X\leq \frac{y-b}{a})&,a>0\\\\
P(X> \frac{y-b}{a})&,a< 0
\end{matrix}\right.
$$

$$
\mathcal{f}_Y(y)=\frac{\text{d}\mathcal{F}_Y(y)}{\text{d}y}=
\left\{\begin{matrix}
\frac{1}{a}f_X(\frac{y-b}{a})&,a>0\\\\
-\frac{1}{a}f_X(\frac{y-b}{a})&,a< 0
\end{matrix}\right.
=\frac{1}{\mid a\mid}f_X(\frac{y-b}{a})
$$

***

## Lecture 3

Calculate the conditional probability $P(B\mid A)=P(A\mid B)P(B)$,
$$
P(A\mid X=x)=\frac{f_X(x\mid A)\cdot P(A)}{f_X(x)}
$$

$$
P(A)\int_{-\infty}^{+\infty}f_X(x\mid A)\text{d}x=\int_{-\infty}^{+\infty}P(A\mid X=x)f_X(x)\text{d}x
$$

Since
$$
\int_{-\infty}^{+\infty}f_X(x\mid A)\text{d}x=1
$$
Then
$$
P(A)=\int_{-\infty}^{+\infty}P(A\mid X=x)f_X(x)\text{d}x
$$
a-posteriori pdf $f_P(P\mid A)$
$$
P(A\mid p=P)=p^k q^{n-k}
$$

$$
\begin{eqnarray}
P(A)&=&\int^1_0 P(A\mid p)f_P(p)\text{d}P\\\\
&=&\int^1_0 p^k(1-p)^{n-k}\text{d}P\\\\
&=&\frac{(n+1)!}{k!(n-k)!}
\end{eqnarray}
$$

$$
\begin{eqnarray}
f(P\mid A)&=&\frac{P(A\mid p=P)f_P(P)}{P(A)}\\\\
&=&\frac{k!(n-k)!p^kq^{n-k}}{(n+1)!}\\\\
&\sim B
\end{eqnarray}
$$

For conditional event $B$,
$$
P(B)=\frac{k+1}{n+2}
$$
Expected value of $X$.
$$
E(X)=\frac{\sum X_i}{n}=\sum\frac{1}{n}X_i=\sum p_iX_i=\int xf_X(x)\text{d}x=\sum p_i\int_X\delta(x-x_i)\text{d}x
$$

$$
\mu_X=E(X)=\int_x f_X(x)\text{d}x
$$

$$
E\left[g(x)\right]=\int_yf_Y(y)\text{d}y=\int g(x)\sum_{i=1}^\infty \frac{1}{\frac{\text{d}y}{\text{d}x}}f_X(x_i)\Delta x
$$

$$
E[g(x)]=\int g(x)f_X(x)\text{d}x
$$

$$
\mu_n=E(X^n)=\int x^nf_X(x)\text{d}x
$$

$$
g_n=E[(x-\mu)^n]
$$

$$
\begin{eqnarray}
\mu&=&E(X)\\\\
&=&\int_{-\infty}^{+\infty}xf_X(x)\text{d}x\\\\
&=&\sum_i x_i P(X=x_c)
\end{eqnarray}
$$

$$
\text{Var}(X)=\sigma^2=E[(X-\mu)^2]
$$

$\sigma$ is dispersion

measure of spread of observation around mean
$$
\begin{eqnarray}
\text{Var}(X)&=&\sigma^2=E[(X-\mu)^2]\\\\
&=&E[X^2-2\mu X+\mu^2]\\\\
&=&\int(x^2-2\mu x+\mu^2)f_\lambda(x)\text{d}_x\\\\
&=&\int x^2f_X(x)\text{d}x-2\mu\int xf_X(x)\text{d}x+\mu^2
\end{eqnarray}
$$

Characteristic Function
$$
\begin{eqnarray}
\Phi_X(\omega)=E[e^{j\omega X}]&=&\int^{+\infty}_{-\infty}e^{j\omega X}f_X(x)\text{d}x\\\\
&=&\int(1+j\omega x+\frac{j^2\omega^2 x^2}{2!}+\cdots+\frac{j^n\omega^n x^n}{n!})f_X(x)\text{d}x\\\\
&=&1+j\omega \int xf_X(x)\text{d}x+\frac{j^2\omega^2}{2!} \int x^2f_X(x)\text{d}x+\cdots+\frac{j^n\omega^n}{n!} \int x^nf_X(x)\text{d}x\\\\
&=&1+E(X)+E(X^2)+\cdots+E(X^n)
\end{eqnarray}
$$
Which means
$$
\frac{1}{j}\frac{\text{d}\Phi_X(\omega)}{\text{d}\omega}=E(X)\\\\
\frac{1}{j^n}\frac{\text{d}^n\Phi_X(\omega)}{\text{d}^n\omega}=E(X^n)
$$

$$
\begin{eqnarray}
\Phi_X(\omega)&=&\sum_{k=0}^\infty e^{j\omega k}P(X=k)\\\\
&=&\sum_{k=0}^\infty e^{j\omega k}e^{-\lambda}\frac{\lambda^k}{k!}\\\\
&=&e^{-\lambda}\sum_{k=0}^\infty\frac{(\lambda e^{j\omega})^k}{k!}\\\\
&=& e^{-\lambda}e^{\lambda e^{j\omega}}
\end{eqnarray}
$$

$$
\frac{1}{j}\frac{\text{d}\Phi_X(\omega)}{\text{d}\omega}=e^{-\lambda}e^{\lambda e^{j\omega}}\lambda e^{j\omega}j=\frac{\lambda j}{j}=\lambda
$$

Another example $P[\mid X-\mu\mid>\varepsilon]$
$$
\begin{eqnarray}
\sigma_X^2&=&E[(X-\mu)^2]\\\\
&=&\int_{-\infty}^{+\infty}(x-\mu)^2f_X(x)\text{d}x\\\\
&=&\int\limits_{\mid X-\mu\mid>\varepsilon}(x-\mu)^2 f_X(x)\text{d}x+\int\limits_{\mid X-\mu\mid<\varepsilon}(x-\mu)^2 f_X(x)\text{d}x\\\\
&\geq \int\limits_{\mid X-\mu\mid>\varepsilon}(x-\mu)^2 f_X(x)\text{d}x
\end{eqnarray}
$$
We can make deduction of the Chebyshev's inequation
$$
P(Z)=E[Z^X]=\sum Z^kP(X=k)
$$

$$
\sigma_X^2\geq\int\limits_{\mid X-\mu\mid>\varepsilon}(x-\mu)^2 f_X(x)\text{d}x\geq \varepsilon^2\int\limits_{\mid X-\mu\mid>\varepsilon}f_X(x)\text{d}x
$$

Make $\displaystyle\int\limits_{\mid X-\mu\mid>\varepsilon}f_X(x)\text{d}x$ as $P[\mid X-\mu\mid \geq\varepsilon]$

Then
$$
P[\mid X-\mu\mid\geq\varepsilon]\leq\frac{\sigma_X^2}{\varepsilon^2}
$$

***

## Lecture 4

Characteristic Function
$$
\Phi_X(\omega)=E[e^{j\omega x}]
$$

$$
X\sim B(n,p)=P(X=k)={n \choose k}p^k q^{n-k} 
$$

$$
\Phi_X(\omega)=E[e^{j\omega x}]=\sum\limits_{k=o}^\infty e^{j\omega k}{n \choose k}p^k q^{n-k}=\sum\limits_{k=0}^\infty {n\choose k}(p e^\omega)^k q^{\omega k}=(pe^\omega+q)^n
$$

For Gaussian $X\sim N(\mu,\sigma^2)$
$$
f_X(x)=\frac{1}{\sqrt{2\pi\sigma^2}}e^{-(x-\mu)^2/2\sigma^2}
$$

$$
\Phi_X(\omega)=E[e^{\gamma\omega x}]=\int\limits_{-\infty}^\infty e^{j\omega x}\frac{1}{\sqrt{2\pi\sigma^2}}e^{-(x-\mu)^2/2\sigma^2}=\int\limits_{-\infty}^\infty e^{j\omega(\mu+\sigma y)}\frac{1}{\sqrt{2\pi\sigma^2}}e^{-y^2/2}=e^{j\mu\omega-\frac{1}{2}\sigma^2\omega^2}
$$

Specifically, For $X\sim N(0,1)$
$$
f_X(x)=\frac{1}{\sqrt{2\pi}}e^{-x^2/2}
$$

$$
\Phi_X(\omega)=e^{-\omega^2/2}
$$

$$
E[X^n]=\frac{1}{j^n}\frac{\text{d}^n\Phi_X(n)}{\text{d}\omega^n}\mid_{\omega=0}
$$

De-Mourne Laplace Theorem For $X\sim B(n,p)$
$$
\Phi_X(\omega)=(pe^{j\omega}+q)^n
$$

$$
y=\frac{x-np}{\sqrt{npq}}
$$

We can proof that $y$ follows Gaussian distribution

Notice that
$$
e^x=1+x+\frac{x^2}{2!}+\frac{x^3}{3!}+\cdots+\frac{x^n}{n!}
$$
Then
$$
\begin{eqnarray}
\Phi_X(\omega)&=&E[e^{j\omega y}]=E[e^{j\omega\frac{(x-np)}{\sqrt{npq}}}]\\\\
&=&e^{-\frac{jnp\omega}{\sqrt{npq}}}E[e^{e^{\frac{j\omega x}{\sqrt{npq}}}}]\\\\
&=&e^{-\frac{jnp\omega}{\sqrt{npq}}}(pe^{j\frac{\omega}{\sqrt{npq}}}+q)^n\\\\
&=&(pe^{j\frac{q\omega}{\sqrt{npq}}}+qe^{-\frac{p\omega}{\sqrt{npq}}})^n\\\\
&=&(p[1+\frac{jq\omega}{\sqrt{npq}}+\frac{j^2q^2\omega^2}{2npq}+o(\frac{\sigma}{n^{3/2}})]+q[1-\frac{jp\omega}{\sqrt{npq}}+\frac{j^2p^2\omega^2}{2npq}+o\cdots])^n\\\\
&=&(\frac{p+q}{1}+o-\frac{pq^2\omega^2}{2npq}-\frac{p^2q\omega^2}{2npq})^n\\\\
&=&\lim_{n\rightarrow\infty}(1-\frac{\omega^2}{2n})^n\\\\
&=&e^{-\omega^2/2}\\\\
&=&\mathcal{N}(0,1)
\end{eqnarray}
$$
The notation $it$ is the same as $j\omega$ in mathematical proof.

Leibnitz's Rule
$$
H(x)=\int\limits_{a(x)}^{b(x)} h(x,y)\text{d}y
$$

$$
\frac{\text{d}H(x)}{\text{d}x}=\frac{\text{d}h(x)}{\text{d}x}h(x,b)-\frac{\text{d}h(x)}{\text{d}x}h(x,a)+\int\limits_a^b\frac{\partial h(x,y)}{\partial x}\text{d}y
$$

### $n$ Random Variables $\rightarrow$ Joint Representation

$$
X\rightarrow F_X(x)=P(X\leq x)\rightarrow f_X(x)=\frac{\text{d}F_X(x)}{\text{d}x}\\\\
Y\rightarrow F_Y(y)=P(Y\leq y)\rightarrow f_Y(y)=\frac{\text{d}F_Y(y)}{\text{d}y}\\\\
$$

$$
F_{XY}(x,y)=P[(X\leq x)\cap(Y\leq y)]\geq0
$$

Properties:

1. $F_{X,Y}(-\infty,y)=0$
2. $P(-\infty,+\infty)=P(\mathcal{S})=1$

$$
\begin{eqnarray}
F_{XY}(x,y)=P(X\leq x,Y\leq y)\\\\
F_{XY}(x,+\infty)=P[(X\leq x)\cap(Y\leq +\infty)]=P(X\leq x)=F_X(x)\\\\
F_{XY}(+\infty,y)=P[(X\leq +\infty)\cap(Y\leq y)]=P(Y\leq y)=F_Y(y)
\end{eqnarray}
$$

$$
\begin{eqnarray}
f_{XY}(x,y)=\frac{\partial^2F_{XY}(x,y)}{\partial x\partial y}\geq 0\\\\
F_{XY}(x_0,y_0)=\int\limits_{-\infty}^{x_0}\int\limits_{-\infty}^{y_0}f_{XY}(x,y)\text{d}x\text{d}y
\end{eqnarray}
$$

$$
\frac{\text{d}F_X(x)}{\text{d}x}=f_X(x)\\\\
F_X(x_0)=\int\limits_{-\infty}^{x_0}f_X(x)\text{d}x
$$

$$
F_{XY}(x,y)=\int\limits_{-\infty}^{x}\int\limits_{-\infty}^yf_{XY}(u,v)\text{d}u\text{d}v\\\\
F_X(x)=F_{XY}(x,+\infty)=\int\limits_{-\infty}^{x}\int\limits_{-\infty}^{+\infty}f_{XY}(u,v)\text{d}u\text{d}v\\\\
f_X(x)=\int\limits_{-\infty}^{+\infty}f_{XY}(x,y)\text{d}y\\\\
f_Y(y)=\int\limits_{-\infty}^{+\infty}f_{XY}(x,y)\text{d}x
$$

Obviously, there is a character
$$
\int\limits_{-\infty}^{+\infty}\int\limits_{-\infty}^{+\infty}f_{XY}(x,y)\text{d}x\text{d}y=1
$$

***

## Lecture 5

### A Function of Two Random Variables

Given $f_{XY}(x,y),z=g(X,Y)$, find $f_Z(z)$.
$$
F_{X,Y}(x,y)=P(X\leq x,Y\leq y)\geq0
$$
For a rectangular region
$$
\begin{eqnarray}
P[x_1<X\leq x_2,y_1<Y\leq y_2]&=&F_{XY}(x_2,y_2)-F_{XY}(x_1,y_2)-F_{XY}(x_2,y_1)+F_{XY}(x_1,y_1)\\\\
&=&\int\limits_{x_1}^{x_2}\int\limits_{y_1}^{y_2}f_{XY}(x,y)\text{d}x\text{d}y
\end{eqnarray}
$$

$$
f_{XY}(x,y)=\frac{\partial^2F_{XY}(x,y)}{\partial x\partial y}
$$

If the region $D$ is of a random shape
$$
\begin{eqnarray}
P[(X,Y)\in D]&=&\mathop{\sum\sum}\limits_{D_{ij}}f_{XY}(x_i,y_i)\Delta x\Delta y\\\\
&=&\mathop{\int\int}\limits_{(X,Y)\in D}f_{XY}(x,y)\text{d}x
\end{eqnarray}
$$

Therefore
$$
f_X(x)=\int\limits_{-\infty}^{+\infty}f_{XY}(x,y)\text{d}y\\\\
f_Y(y)=\int\limits_{-\infty}^{+\infty}f_{XY}(x,y)\text{d}x
$$
If
$$
f_{XY}(x,y)=f_X(x)f_Y(y)
$$
We say $X$ and $Y$ are independent random variables.

Leibnitz Rule
$$
\ln(z)=\int\limits_{a(z)}^{b(z)}\ln(x,z)\text{d}x
$$
Proof:
$$
\frac{\text{d}\ln(z)}{\text{d}z}=\frac{\text{d}b(z)}{\text{d}z}\ln(b,z)-\frac{\text{d}a(z)}{\text{d}z}\ln(a,z)+\int\limits_a^b\frac{\partial \ln(x,z)}{\partial z}\text{d}x
$$

When two random variables are independent, we can use convolutional operation

$$
a(x)\circledast b(x)=z(x)=\int\limits_{-\infty}^{+\infty}a(z-x)b(x)\text{d}x
$$
For example, $f_{XY}(x,y)=e^{-x},x>y>0,Z=X+Y$
$$
\begin{eqnarray}
F_Z(z)&=&P(X+Y\leq Z)\\\\
&=&\int\limits_{y=0}^{z/2}\int\limits_{x=0}^{z-y}f_{XY}(x,y)\text{d}x\text{d}y
\end{eqnarray}
$$
Sum of any 2 Gaussian random variables (i.i.d. or not) is still Gaussian

Another example, $X+yY=Ze^{y\theta},x\sim\mathcal{N}(0,\sigma^2),X,Y,i.i.d.,Z=\sqrt{X^2+Y^2}$.



$Z=\frac{X}{Y}$, assume $\frac{X}{Y}\leq z$ as $A$, $Y>0$ as $B$,
$$
\begin{eqnarray}
F_Z(z)=P(Z\leq z)&=&P[(\frac{X}{Y}\leq z)\cap(Y>0)\cup(Y<0)]\\\\
&=&P[(A\cap(B\cup \overline{B}))]\\\\
&=&P(AB)+P(A\overline{B})\\\\
&=&P(\frac{X}{Y}\leq z, Y\geq 0)+P(\frac{X}{Y}\leq z, Y< 0)\\\\
&=&P(X\leq Yz, Y\geq 0)+P(X\leq Yz, Y< 0)\\\\
&=&\int\limits_{0}^{+\infty}\int\limits_{-\infty}^{yz}f_{XY}(x,y)\text{d}x\text{d}y+\int\limits_{0}^{+\infty}\int\limits_{y}^{+\infty}f_{XY}(x,y)\text{d}x\text{d}y
\end{eqnarray}
$$

$$
\begin{eqnarray}
f_Z(z)&=&\int\limits_0^\infty yf_{XY}(yz,y)\text{d}y+\int\limits_0^\infty (-y)f_{XY}(yz,y)\text{d}y\\\\
&=&\int\limits_{-\infty}^{+\infty}|y|f_{XY}(yz,y)\text{d}y
\end{eqnarray}
$$

If $X,Y\sim\mathcal{N}(\mu_X,\mu_Y,\sigma_X^2,\sigma_Y^2,\rho)$

$X,Y$ jointly Gaussian
$$
f_{XY}(x,y)=\frac{1}{\sqrt{2\pi\sigma_X\sigma_Y(1-\rho^2)}}\exp\{{-\frac{1}{2(1-\rho^2)}[\frac{(x-\mu_X)^2}{\sigma_X^2}-\frac{2\rho(x-\mu_X)(y-\mu_Y)}{\sigma_X\sigma_Y}+\frac{(y-\mu_Y)^2}{\sigma_Y^2}]}\}
$$
If $\rho=0$, they are independent.

***

## Lecture 6

### Review

$Z=g(X,Y)$, $f_{XY}(x,y)$ given, find $f_Z(z)$.

$F_Z(z)=P(Z\leq z)=P(g(x,y)\leq z)$
$$
P((x,y)\in D_z)=\mathop{\int\int}\limits_{(X,Y)\in D}f_{XY}(x,y)\text{d}x
$$

$$
x,y\quad i,i,d\sim \mathcal{N}(0,\sigma^2)
$$

$$
Z=\sqrt{X^2+Y^2}\sim \text{Rayleigh}
$$

$$
f_Z(z)=\frac{z}{\sigma^2}e^{-z^2/2\sigma^2},z\geq 0
$$

$$
W=\frac{Y}{X},Z\sim \text{Cauchy}(1),\theta=
$$


{% endraw %}












