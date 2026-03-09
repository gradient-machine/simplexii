+++
date = '2026-03-06T05:06:19Z'
draft = false
title = 'Constrained Optimization'
+++

## Formulation

{{< equation id="eq-optimization" >}}
$$
\min_{x \in \mathbb{R}^n} f(x) \quad \text{subject to} \quad 
\begin{cases} 
c_i(x) = 0, & i \in \mathcal{E}, \\ 
c_i(x) \geq 0, & i \in \mathcal{I}, 
\end{cases} \tag{1}
$$
{{< /equation >}}

<!--more-->

where

1. $f(x)$ and $c_i(x)$ are smooth and real-valued functions
2. Good

## The goals

1. Deriving the solution of [Eq. (1)](#eq-optimization)
2. Deriving the optimality conditions satisfied by the solution, including both necessary and sufficient conditions

## Important concepts

1. The contour of the objective function $f(x)$
2. Strict local solutions
3. Isolated local solutions
4. Active set

### 1. The contours of the objective function

{{< img-resize src="constrained_opt_fig12_1_contour.png" display_width="60%" title="Example in Figure 12.1" caption="Source: Notes on Numerical Optimization" >}}

### 2. Strict local solutions

$x^* \in \mathcal{R^d}$ is a strict local solution if $x^* \in \Omega \subseteq \mathcal{R^d}$, where $\Omega$ denotes the feasible region, and there exists a neighborhood $\mathcal{N} \subseteq \mathcal{R^d}$ of $x^*$, in which $f(x^*) < f(x)$ for all $x \in \Omega \cap \mathcal{N} $ with $x \neq x^*$.

> 1. It is a strict one because $x^*$ is the minimal value in a certain region around it.
> 2. A strict `local` solution is also referred to as a `strong` local solution. If not a strict one, it is called a `weak` local solution.

### 3. Isolated local solutions

$x^* \in \mathcal{R^d}$ is an isolated local solution if $x^* \in \Omega \subseteq \mathcal{R^d}$ and there exists a neighborhood $\mathcal{N} \subseteq \mathcal{R^d}$ of $x^*$, in which $x^*$ is the only local solution in $\Omega \cap \mathcal{N}$.

> 1. An isolated local solution must be a strict one, `not` vice versa.
> 2. A strict local solution may not be an isolated one because:
>    * No matter how small the region $\Omega \cap \mathcal{N}$ is, in which $x^*$ is a strict local solution
>    * There is still another strict one $x_1^* \in \Omega \cap \mathcal{N}_1$, where $\mathcal{N}_1 \subset \mathcal{N}$ and $x_1^* > x^*$
>    * In other words, this is mainly because of the local fluctuation around $x^*$, rather than being monotonic decreasing therein
>    * An example of $x_1^*$ is the solution of $f(x) = \begin{cases} x^4 \cos\left(\frac{1}{x}\right) + 2x^4, & x \neq 0, \\ 0, & x = 0. \end{cases}$, as shown in the figure below.

{{< img-resize src="constrained_opt_strnotiso.png" display_width="100%" title="An example of a strict local solution but not an isolated one. No matter how small the region around the strict local solution is, there is always another strict one within its own local region and having a greater value." caption="Source: Notes on Numerical Optimization" >}}

### 4. Active set

There are two aspects of the definition of an active set $\mathcal{A}(x)$.

1. `What is it defined to be?` $\mathcal{A}(x)$ is a set of indexes, defined as $\mathcal{A}(x) = \mathcal{E} \cup \{\, i \in \mathcal{I} \mid c_i(x) = 0 \,\}$.

> Take a constraint function, as long as its value is zero at $x$, it is active.

2. `For whom is it defined?` A set is associated with each $x \in \Omega$, i.e. for every feasible $x$ according to the constraints.

## Three cases illustrating the two afore-mentioned goals

1. A single equality constraint

The optimal solution to the problem below is $x^* = [-1, -1]^T$,
$$
\min\; x_1 + x_2 \quad \text{s.t.} \quad x_1^2 + x_2^2 - 2 = 0
$$

At $x^*$, the gradients of the objective function and the constraint function `must be parallel to each other`,

{{< equation id="eq-co_sec_onc" >}}
$$
\nabla f(x^{*}) = \lambda_{1}^{*}\,\nabla c_{1}(x^{*}).\tag{2}
$$
{{< /equation >}}

The general procedure to analyze the condition is as follows.

> 1. Consider what $f(x)$ is?
> 2. Consider what $\mathcal{C} = \{c_i(x) | i \in \{\mathcal{E}, \mathcal{I}\}\}$ is?
> 3. Consider what $\Omega$ is based on $\mathcal{C}$?
> 4. Consider an obvious optimal solution $x^*$.
> 5. Consider the conditions to be satisfied by $x^*$, using first-order Taylor series approximation.

Based on [Eq. (2)](#eq-co_sec_onc), a method to find $x^*$ is using the Lagrangian function,

$$
\nabla_x \mathcal{L}(x, \lambda_1) = 0, \quad \text{where } \mathcal{L}(x, \lambda_1)=f(x) - \lambda_1 c_1(x),
$$

based on what is equivalent to [Eq. (2)](#eq-co_sec_onc),

$$
\nabla_x \mathcal{L}(x^*, \lambda_1^*) = \nabla_x f(x^*) - \lambda_1 \nabla_x c_1(x^*) = 0,
$$

It is worth noting that

> 1. The condition in [Eq. (2)](#eq-co_sec_onc) is only necessary, not sufficient,
> 2. The condition is independent of the form of $f(x)$ and $c_i(x)$,
> 3. The condition only states the parallelization of the two gradients, not identical direction,
> 4. Although $c_i(x)$ is usually considered for $x$ where $c_i(x) = 0$, $c_i(x)$ itself is also a function in the same as $f(x)$ does. If $x \in \mathbb{R}^2$, $c_i(x)$ is still a function in $\mathbb{R}^3$ as $f(x)$ does. Therefore, when analyzing $\nabla_x c_i(x)$, e.g. in the particular case of $x \in \mathbb{R}^2$, the arrow drawn in the plane of $\mathbb{R^2}$ reflects the direction of the fastest increase of the value of $c_i(x)$ in $\mathbb{R}^3$.
> 5. $\mathcal{A}(x)$ is not mentioned in this case because $\mathcal{E} \ne \varnothing, \mathcal{I} = \varnothing$, resulting in $\mathcal{A}(x) = \mathcal{E}, \forall x \in \Omega$.

2. A single inequality constraint
3. Two inequality constraint

### 1. A single equality constraint

### 2. A single inequality constraint

### 3. Two inequality constraint
