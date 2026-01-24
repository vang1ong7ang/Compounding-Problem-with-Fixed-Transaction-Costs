# Compounding Problem with Fixed Transaction Costs

## The Introduction

Compound interest is one of the core ideas in financial mathematics: gains themselves generate gains. In the idealized limit where compounding happens continuously, growth becomes exponential, and the constant e appears naturally as the fundamental “unit” of smooth multiplicative growth.

Real-world compounding, however, is not frictionless: reinvesting incurs costs. Some fees scale with the traded amount and can often be viewed, in a simplified model, as effectively reducing the nominal interest rate; they do not introduce a sharp “when to act” choice. To isolate that timing tradeoff, we focus on the case where each compounding action pays a constant cost, so acting more often captures growth sooner but also pays the fixed cost more often.

The goal of this note is to make that tradeoff precise and to identify an optimal rule for when to compound, based only on the current principal.

## The Problem

All variables are reals unless stated otherwise. Fix the nominal interest rate $r > 0$ and the compounding cost $c > 0$.

Given an initial principal $p_0 > 0$, find an optimal sequence of waiting times $(t_i)_{i\ge 0}$ with $t_i > 0$. Starting from $p_0$, you wait $t_i$ and then perform a compounding action, updating the principal by

$$
p_{i+1} = p_i + p_i r t_i - c
$$

We say $(t_i)$ is optimal if, for any other sequence $(\tau_i)_{i\ge 0}$ with $\tau_i > 0$, it is never dominated by $(\tau_i)$: there exists a threshold $T > 0$ such that for all $m,n \ge 0$,

$$
\sum_{i=0}^{n} t_i > \sum_{i=0}^{m} \tau_i > T
\implies
p_{n+1} > \rho_{m+1}
$$

where $(\rho_i)$ is defined by $\rho_0 := p_0$ and $\rho_{i+1} = \rho_i + \rho_i r \tau_i - c$.

# The Solution

Solve for a sequence $(x_i)_{i\ge 0}$ satisfying

$$
x_{i+1} - x_{i+2} = \frac{x_i - x_{i+1}}{1 + x_{i+1}}
$$

with boundary conditions $x_0 - x_1 = \frac{c}{p_0}$ and $x_i \to 0$ as $i\to\infty$

Set

$$
t_i = \frac{x_i}{r}
$$

# The Analysis

TODO PROOF AND LEMMAS

The waiting times satisfy, for all $i \ge 0$,

$$
t_{i+1} = t_i - \frac{c}{p_i r}
$$

Choose $t_0$ so that $t_i \to 0$ as $i\to\infty$; equivalently,

$$
t_0 = \frac{1}{r}\sum_{i=0}^{\infty} \frac{c}{p_i}
$$

# The Experiment

I implemented a small game to simulate the compounding process, along with a few numerical routines for solving/approximating the defining equations. See [exponium](https://github.com/vang1ong7ang/exponium).

# The Conclusion

Damn greedy.

