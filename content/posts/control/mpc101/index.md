---
title: "Model Predictive Control 101: The concept"
date: 2024-11-01T06:00:23+06:00
hero: hero.jpg
theme: Toha
menu:
  sidebar:
    name: Model Predictive Control 101
    identifier: mpc-101
    parent: control
    weight: 10
math: true
---

In this post, let's dive into the concept of Model Predictive Control (MPC) for discrete time linear systems with a finite prediction horizon. My major reference is [Predictive Control for Linear and Hybrid Systems](http://cse.lab.imtlucca.it/~bemporad/publications/papers/BBMbook.pdf).

### What is Model Predictive Control?

MPC, as known as receding horizon control (RHC) is an optimization-based control strategy where the control action is determined by solving a mathematical optimization problem at each time step. The key idea is to predict the future behavior of the system over a specified time horizon and choose the best control inputs accordingly, while respecting system constraints.

### The algorithm

Consider a discrete time system:

$$ x(t+1) = Ax(t) + Bu(t), x \in \mathbb{R}^n, u \in \mathbb{R}^m, A \in \mathbb{R}^{n \times n}, B \in \mathbb{R}^{n \times m}. $$

Without loss of generality, we set the target for the state $x$ to be the origin. Then we define the following cost function as penalty:

$$ J_t(x(t), U_{t \rightarrow t+N | t}) = p(x_{t \rightarrow t+N | t}) + \sum_{k=0}^{N-1} q(x_{t+k | t}, u_{t+k | t}), $$

where $U_{t \rightarrow t+N | t} = \lbrace u_{t|t}, \cdots, u_{t \rightarrow t+N-1 | t} \rbrace$, $p$ is the penalty on the final state, $q$ is the penalty on intermediate states and controls. 

Then, at $t=0$, MPC is essentially solving the following optimization problem:

{{< img src="optimization.png" height="150" width="500" align="center">}}

{{< vs 1>}}

Usually we take $p(x_N) = ||P x_N||_2 = x^\intercal_N P x_N$ and $q(x_k, u_k) = ||Q x_k||_2 + ||R u_k||_2 = x^\intercal_k Q x_k + u^\intercal_k R u_k$.

--------------------------------------------------------

MPC Algorithm:

1. Input: state $x(t)$ at time $t$

2. Solve the optimization problem for $U^*_0(x(t))$

3. If 'problem infeasible' Then stop

4. Return the first element $u^\*_0$ of $U^\*_0(x(t))$

5. Output: control input as $u(x(t))$ 

--------------------------------------------------------

### Advantages of MPC

- Handles Constraints: MPC inherently handles state and input constraints.
- Predictive Control: Optimizes future behavior, making it more robust to disturbances.
- Versatile: Works for a wide range of systems, from simple linear models to complex nonlinear dynamics.

### Disadvantages of MPC

- MPC relies on an accurate model of the system.
- The stability and feasiblity of MPC are not guaranteed.
- Solving an optimization problem at each time step can be computationally expensive, especially for high-dimensional systems, nonlinear models, and long prediction horizons.
