---
title: "Newton, once again..."
published: true
---

Another year has passed and the [COVID-19 pandemic](https://en.wikipedia.org/wiki/COVID-19_pandemic) is yet to be gone. During this time, I've been daydreaming about my *good old days* when I was still going to school without any restriction.

It was during these moments that I remembered one thing I've always wanted to prove to myself. And, once again, it involved [Isaac Newton](https://en.wikipedia.org/wiki/Isaac_Newton).

## Table of Contents
  - [The elementary problem](#the-elementary-problem)
    - [Computing roots first](#computing-roots-first)
    - [Vieta's formulas](#vietas-formulas)
  - [Generalizing the problem](#generalizing-the-problem)
    - [Newton-Girard's identity](#newton-girards-identity)
      - [Proof of Newton-Girard's identity](#proof-of-newton-girards-identity)
        - [First step: defining a polynomial $p(x)$](#first-step-defining-a-polynomial-px)
        - [Second step: defining the function $g(x)$](#second-step-defining-the-function-gx)
        - [Third step: comparing $p(x)$ with its own Taylor-Maclaurin series](#third-step-comparing-px-with-its-own-taylor-maclaurin-series)
        - [Fourth step: taking the $i$-th derivative of $p(x)$](#fourth-step-taking-the-i-th-derivative-of-px)
        - [Final step: comparing the $i$-th derivative of $p(0)$](#final-step-comparing-the-i-th-derivative-of-p0)
      - [Application to the stated problem](#application-to-the-stated-problem)

## The elementary problem

There was a time when, during maths classes, the teacher would always have asked questions like this one:

> Given $p(x)=x^2-4x+3$ and $\lambda_1, \lambda_2$ such that $p(\lambda_1)=p(\lambda_2)=0$ (i.e. $\lambda_1, \lambda_2$ are the roots of the polynomial $p(x)$), compute $\lambda_1^2+\lambda_2^2$.

It was not difficult to answer this problem and there were two main approaches to this problem.

### Computing roots first

We can compute $\lambda_1$ and $\lambda_2$ using the [quadratic formula](https://en.wikipedia.org/wiki/Quadratic_formula). We get $\lambda_1=\frac{4 +\sqrt{(-4)^2 -4\cdot1\cdot3}}{2\cdot1}=3$ and $\lambda_2=\frac{4 - \sqrt{(-4)^2 -4\cdot1\cdot3}}{2\cdot1}=1$.

Hence, $\lambda_1^2+\lambda_2^2=3^2+1^2=10$.

The problem given by this kind of approach is that we have to find the roots of $p(x)$ in terms of sums, products and radicals, which is not always possible for polynomials with degree greater than $4$ by the [Abel-Ruffini theorem](https://en.wikipedia.org/wiki/Abel%E2%80%93Ruffini_theorem).

Furthermore, we have to compute the result of the sum of all the roots raised to a certain power, which may be difficult to compute if we had irrational roots.

### Vieta's formulas

We know by the [factor theorem](https://en.wikipedia.org/wiki/Factor_theorem) that $p(x)=x^2-4x+3=(x-\lambda_1)(x-\lambda_1)=x^2-(\lambda_1 + \lambda_2)x+\lambda_1\lambda_2$. Therefore, $\lambda_1 + \lambda_2 = 4$ and $\lambda_1\lambda_2=3$.

We have to compute $\lambda_1^2 + \lambda_2^2$, which can be rearranged as $(\lambda_1 + \lambda_2)^2 - 2\lambda_1\lambda_2$ and therefore is equal to $4^2 - 2 \cdot 3 = 10$.

In general, given $f(x)=a_n x^n + a_{n-1} x^{n-1} + \ldots + a_1 x + a_0$, we have that $a_m = \displaystyle (-1)^{n-m} a_n \sum_{\mathrm{cyc}} \underbrace{\lambda_i \lambda_j \cdots \lambda_k}_{(n - m)\ \text{times}} \$ where $\lambda_w$ is a root of $f(x)$. These relationships are called [Vieta's formulas](https://en.wikipedia.org/wiki/Vieta%27s_formulas).

The benefit we get in using this approach is that we do not have to compute the roots of the polynomial $p(x)$.

## Generalizing the problem

What if the problem asked to compute $\lambda_1^3 + \lambda_2^3$? We can once again factor $\lambda_1^3 + \lambda_2^3$ as $(\lambda_1 + \lambda_2)(\lambda_1^2 + \lambda_2^2 - \lambda_1\lambda_2)$, getting $4(10 - 3) = 28$. We can check the result using the roots we had already computed: $\lambda_1^3 + \lambda_2^3 = 3^3 + 1^3 = 28$.

It is worth noting that, in order to calculate $\lambda_1^3 + \lambda_2^3$, we had to make use of $\lambda_1^2 + \lambda_2^2$ and $\lambda_1 + \lambda_2$.

So, is there a generalization of this kind of relationship between the sums of powers of the roots of a polynomial? Of course there is, and it is the [Newton-Girard's identity](https://en.wikipedia.org/wiki/Newton%27s_identities). What I was seeking in the first place was its proof, that I'm now going to explain.

### Newton-Girard's identity

Newton's identity states that given $e_m = \|\frac{a_{n-m}}{a_n}\|$ and $P_k = \lambda_1^k + \lambda_2^k + \ldots + \lambda_n^k = \displaystyle \sum_{i=1}^n \lambda_i^k$, the following identity holds:

$$m e_m = e_{m-1} P_1 - e_{m-2} P_2 + e_{m-3} P_3 - \ldots = \displaystyle \sum_{i=1}^{m} (-1)^{i-1} e_{m-i} P_i$$

We can even rearrange this identity by noticing that $e_0$ must always be equal to $1$ and get:

$$m e_m = \displaystyle \sum_{i=1}^{m-1} (-1)^{i-1} e_{m-i} P_i + (-1)^{m-1} P_m$$

Hence, we obtain:

$$P_m = (-1)^m \left( \displaystyle \sum_{i=1}^{m-1} (-1)^{i-1} e_{m-i} P_i - m e_m \right)$$

This proves the relationship between all the sums of the powers of the roots of a polynomial we wanted to prove to ourselves earlier and gives us a powerful tool to compute the result of the kind of problems we discussed earlier.

#### Proof of Newton-Girard's identity

The following proof makes use of [calculus](https://en.wikipedia.org/wiki/Calculus), [Taylor-Maclaurin series expansion](https://en.wikipedia.org/wiki/Taylor_series), [Vieta's formulas](https://en.wikipedia.org/wiki/Vieta%27s_formulas), the $n$-th derivative of the [natural logarithm](https://en.wikipedia.org/wiki/Natural_logarithm) and [Leibniz's rule](https://en.wikipedia.org/wiki/Product_rule?#Higher_derivatives).[^1]

##### First step: defining a polynomial $p(x)$

The first thing we do is defining a polynomial $p(x) = \displaystyle \prod_{i=1}^n \left(1 + \lambda_i x \right)$. It is worth noting that $p(x)$ is equal to $e_0 + e_1 x + e_2 x^2 + \cdots + e_n x^n$. This expression can also be expressed as an infinite sum, given that $e_k = 0$ for $k > n$, therefore giving us the following identity:

$$p(x) = \displaystyle \sum_{i=0}^\infty e_i x^i$$

##### Second step: defining the function $g(x)$

Then, we take the natural logarithm of the polynomial $p(x)$, getting:

$$\ln(p(x)) = \ln((1+\lambda_1 x)(1+\lambda_2 x)(1+\lambda_3 x)\cdots(1+\lambda_n x)) = \displaystyle \sum_{i=1}^n \ln(1+\lambda_i x)$$

Hence, we compute the first derivative of each side of the equation and we define it as $g(x)$:

$$g(x)=\dfrac{\dot p(x)}{p(x)}=\frac{\lambda_1}{1+\lambda_1 x} + \ldots + \frac{\lambda_n}{1+\lambda_n x}=\displaystyle \sum_{i=1}^n \frac{\lambda_i}{1 + \lambda_i x}$$

It is easily provable by induction that the following identity holds:

$$\overset{i}{\dot g}(x)=(-1)^i i! \displaystyle \sum_{j=1}^n \left[ \left( \frac{\lambda_j}{1+\lambda_j x} \right) ^{i+1} \right]$$

If we set $x$ to be equal to $0$, we get:

$$\overset{i}{\dot g}(0)=(-1)^i i! \displaystyle \sum_{j=1}^n \lambda_j^{i+1}=(-1)^i P_{i+1}$$

##### Third step: comparing $p(x)$ with its own Taylor-Maclaurin series

The polynomial $p(x)$ is also representable by its own [Taylor-Maclaurin series](https://en.wikipedia.org/wiki/Taylor_series) (i.e. its Taylor series with $a$ set to be equal to $0$), which is $\displaystyle \sum_{i=0}^\infty \frac{\overset{i}{\dot p}(0)}{i!} x^i$.

Each term of the series must coincide with its corresponding term we found in the [first step](#first-step-defining-a-polynomial-px).

Hence, we get:

$$e_i = \frac{\overset{i}{\dot p}(0)}{i!} \Longrightarrow \overset{i}{\dot p}(0) = e_i i!$$

##### Fourth step: taking the $i$-th derivative of $p(x)$

Due to the fact that we defined $g(x)$ as $\frac{\dot p(x)}{p(x)}$, we also know that $\dot p(x) = p(x) g(x)$. Taking the $n$-th derivative using the [Leibniz's rule](https://en.wikipedia.org/wiki/Product_rule?#Higher_derivatives), we get:

$$\overset{i}{\dot p}(x) = \displaystyle \sum_{j=1}^{i} \binom{i-1}{j-1} \overset{i-j}{\dot p}(x) \overset{j-1}{\dot g}(x)$$

Hence, setting $x$ to be equal to $0$:

$$\overset{i}{\dot p}(0) = \displaystyle \sum_{j=1}^{i} \binom{i-1}{j-1} \overset{i-j}{\dot p}(0) \overset{j-1}{\dot g}(0)$$

##### Final step: comparing the $i$-th derivative of $p(0)$

If we compare the $i$-th derivative of $p(0)$ we found in the [third step](#third-step-comparing-px-with-its-own-taylor-maclaurin-series) and the one we found in the [fourth step](#fourth-step-taking-the-i-th-derivative-of-px), we get:

$$e_i i! = \displaystyle \sum_{j=1}^{i} \binom{i-1}{j-1} \overset{i-j}{\dot p}(0) \overset{j-1}{\dot g}(0)$$

Hence, by replacing all the terms with the corresponding ones we found in the [third step](#third-step-comparing-px-with-its-own-taylor-maclaurin-series) and the [second step](#second-step-defining-the-function-gx) and simplifying the expression we get, the following identity holds:

$$i e_i = \displaystyle \sum_{j=1}^{i} (-1)^{j-1} e_{i-j} P_j$$

$$\tag*{$\blacksquare$}$$

#### Application to the stated problem

We had to compute $P_2 = \lambda_1^2 + \lambda_2^2$ given that $\lambda_1$ and $\lambda_2$ are the roots of $p(x)=x^2-4x+3$.

Comparing the coefficients of $x$ in $p(x)$, we get $e_0 = 1$, as we'd already said earlier, $e_1 = 4$ and $e_2=3$.

Using the [Newton-Girard's identity](https://en.wikipedia.org/wiki/Newton%27s_identities), we notice that:

$$2 e_2 = e_1 P_1 - e_0 P_2 \Longrightarrow P_2 = e_1 P_1 - 2 e_2$$

$P_1$ is the same as $e_1$, hence, rearranging the expression, we obtain:

$$P_2 = {e_1}^2 - 2 e_2 = 4^2 - 2 \cdot 3 = 10$$

We can follow the same steps to compute $P_3 = \lambda_1^3 + \lambda_2^3$:

$$3 e_3 = e_2 P_1 - e_1 P_2 + e_0 P_3 \Longrightarrow P_3 = 3 e_3 - e_2 P_1 + e_1 P_2$$

Due to the fact that $e_k = 0$ for $k > n$, $e_3$ must be equal to $0$. Therefore, we obtain:

$$P_3 = - e_2 P_1 + e_1 P_2 = - 3 \cdot 4 + 4 \cdot 10 = 28$$

In conclusion, we have found a generalized solution for the kind of problems we'd stated in the first place. *Newton, we did it, once again!*

<hr/>

[^1]: The concept of the shown proof is taken from [ProofWiki](https://proofwiki.org/wiki/Newton%27s_Identities/Proof_2), which I recommend you to visit.
