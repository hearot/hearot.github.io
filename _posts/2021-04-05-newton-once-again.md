---
title: "Newton, once again..."
published: false
---

Another year has passed and the [COVID-19 pandemic](https://en.wikipedia.org/wiki/COVID-19_pandemic) is yet to be gone. During this time, I've been daydreaming about my *good old days* when I was still going to school without any restriction.

It was during these moments that I remembered one thing I've always wanted to prove to myself. And, once again, it involved [Isaac Newton](https://en.wikipedia.org/wiki/Isaac_Newton).

## Table of Contents
  - [The elementary problem](#the-elementary-problem)
    - [Computing roots first](#computing-roots-first)
    - [Vieta's formulas](#vietas-formulas)
  - [Generalizing the problem](#generalizing-the-problem)
    - [Newton-Girard's identity](#newton-girards-identity)

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

In general, given $f(x)=a_n x^n + a_{n-1} x^{n-1} + \ldots + a_1 x + a_0$, we have that $a_m = \displaystyle (-1)^{n-m} \sum_{\mathrm{cyc}} \underbrace{\lambda_i \lambda_j \cdots \lambda_k}_{(n - m)\ \text{times}} \$ where $\lambda_w$ is a root of $f(x)$. These relationships are called [Vieta's formulas](https://en.wikipedia.org/wiki/Vieta%27s_formulas).

The benefit we get in using this approach is that we do not have to compute the roots of the polynomial $p(x)$.

## Generalizing the problem

What if the problem asked to compute $\lambda_1^3 + \lambda_2^3$? We can once again factor $\lambda_1^3 + \lambda_2^3$ as $(\lambda_1 + \lambda_2)(\lambda_1^2 + \lambda_2^2 - \lambda_1\lambda_2)$, getting $4(10 - 3) = 28$. We can check the result using the roots we had already computed: $\lambda_1^3 + \lambda_2^3 = 3^3 + 1^3 = 28$.

It is worth noting that, in order to calculate $\lambda_1^3 + \lambda_2^3$, we had to make use of $\lambda_1^2 + \lambda_2^2$ and $\lambda_1 + \lambda_2$.

So, is there a generalization of this kind of relationship between the sums of powers of the roots of a polynomial? Of course there is, and it is the [Newton-Girard's identity](https://en.wikipedia.org/wiki/Newton%27s_identities).

### Newton-Girard's identity

Newton's identity states that given $e_m = \|\frac{a_m}{a_n}\|$ and $P_k = \lambda_1^k + \lambda_2^k + \ldots + \lambda_n^k = \displaystyle \sum_{i=1}^n \lambda_i^k$, the following identity holds:

<center>$m e_m = e_{m-1} P_1 - e_{m-2} P_2 + e_{m-3} P_3 - \ldots = \displaystyle \sum_{i=0}^{m-1} (-1)^i e_{m-i-1} P_{i+1}$</center>

We can even rearrange this identity by noticing that $e_0$ must always be equal to $1$ and get:

<center>$m e_m = \displaystyle \sum_{i=0}^{m-2} (-1)^i e_{m-i-1} P_{i+1} + (-1)^{m-1} P_m$</center>

Hence, we obtain:

<center>$P_m = (-1)^m \left( \displaystyle \sum_{i=0}^{m-2} (-1)^i e_{m-i-1} P_{i+1} - m e_m \right)$</center>

This proves the relationship between all the sums of the powers of the roots of a polynomial we wanted to prove to ourselves earlier and gives us a powerful tool to compute the result of the kind of problems we discussed earlier.