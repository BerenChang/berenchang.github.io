---
title: "Model Predictive Control 102: The batch approach"
date: 2024-11-02T06:00:23+06:00
hero: hero.png
theme: Toha
menu:
  sidebar:
    name: Model Predictive Control 102
    identifier: mpc-102
    parent: control
    weight: 10
math: true
---

Reference: [Predictive Control for Linear and Hybrid Systems](http://cse.lab.imtlucca.it/~bemporad/publications/papers/BBMbook.pdf).

In this post, we transform the constrained optimization problem in 101 into a quadratic programming by the "batch approach". 

### The optimization problem

Suppose we have the following optimization problem (mentioned in 101).

{{< img src="optimization.png" height="150" width="500" align="center">}}
{{< vs 1>}}

Take $p(x_N) = ||P x_N||_2 = x^\prime_N P x_N$ and $q(x_k, u_k) = ||Q x_k||_2 + ||R u_k||_2 = x^\prime_k Q x_k + u^\prime_k R u_k$.

### The batch approach

The system is described as $ x(t+1) = Ax(t) + Bu(t) $, then 
$$ x(0) = I x(0) $$
$$ x(1) = Ax(0) + Bu(0) $$
$$ x(2) = Ax(1) + Bu(1) = A(Ax(0) + Bu(0)) + Bu(1) = A^2x(0) + ABu(0) + Bu(1) $$
$$ \cdots $$
Write all those in matrix form, set $x(t) = x_t, u(t) = u_t$, we have

{{< img src="system_matrix.png" height="170" width="580" align="center">}}
{{< vs 1>}}

Set $ U_0 = \[u_0^\prime \thickspace u_1^\prime \thickspace \cdots \thickspace u_{N-1}^\prime \]^\prime $, then

$$ \mathcal{X} = \mathcal{S}^x x(0) + \mathcal{S}^u U_0 $$

Do the same with the cost function, then we have

$$ J(x(0), U_0) = \mathcal{X}^\prime \bar{Q} \mathcal{X} + U_0^\prime \bar{R} U_0, $$

where $\bar{Q} = blockdiag \lbrace Q, \cdots, Q, P \rbrace $ and $\bar{R} = blockdiag \lbrace R, \cdots, R \rbrace $.

Then, 

{{< img src="cost_function_matrix.png" height="80%" width="80%" align="center">}}
{{< vs 1>}}

To deal with the constraints $ A_x x \leq b_x $, $ A_f x_N \leq b_f $, and $ A_u u \leq b_u $, we transform them into the following polyhedron 

$$ \mathcal{P}_i = \lbrace (U_i,x_i) \in \mathbb{R}^{m(N-i)+n} : G_i U_i - E_i x_i \leq w_i \rbrace, $$

where

{{< img src="GEw.png" height="80%" width="80%" align="center">}}
{{< vs 1>}}

The optimization problem is then transformed into the following:

{{< img src="batch_approach.png" height="65%" width="65%" align="center">}}
{{< vs 1>}}

### Summary

To compute the MPC, we transform the optimization into a quadratic programming problem. The QP-based MPC algorithm is described as follows.

{{< img src="qpmpc.png" height="75%" width="75%" align="center">}}
{{< vs 1>}}
