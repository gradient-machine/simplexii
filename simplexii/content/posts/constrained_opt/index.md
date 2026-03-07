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

where

1. $f(x)$ and $c_i(x)$ are smooth and real-valued functions
2. Good

## The goals

1. Deriving the solution of [Eq. (1)](#eq-optimization)
2. Deriving the optimality conditions satisfied by the solution
   > Necessary conditions

   > Sufficient conditions
3. 


## Important attributes

1. The contour of the objective function $f(x)$
2. Local solutions, strict local solutions, and isolated local solutions

### The contours of the objective function

{{< img-resize src="constrained_opt_fig12_1_contour.png" display_width="60%" title="Example in Figure 12.1" caption="Source: Notes on Numerical Optimization" >}}

### Strict local solutions

$x^* \in \mathcal{R^d}$ is a strict local solution if $x^* \in \Omega \subseteq \mathcal{R^d}$ and there exists a neighborhood $\mathcal{N} \subseteq \mathcal{R^d}$ of $x^*$, in which $f(x^*) < f(x)$ for all $x \in \Omega \cap \mathcal{N} $ with $x \neq x^*$.

> 1. It is a strict one because $x^*$ is the minimal value in a certain region around it.
> 2. A strict `local` solution is also referred to as a `strong` local solution. If not a strict one, it is called a `weak` local solution.

### Isolated local solutions

$x^* \in \mathcal{R^d}$ is an isolated local solution if $x^* \in \Omega \subseteq \mathcal{R^d}$ and there exists a neighborhood $\mathcal{N} \subseteq \mathcal{R^d}$ of $x^*$, in which $x^*$ is the only local solution in $\Omega \cap \mathcal{N}$.

> 1. An isolated local solution must be a strict one, `not` vice versa.
> 2. A strict local solution may not be an isolated one because 
>    * no matter how small the region $\Omega \cap \mathcal{N}$ is, in which $x^*$ is a strict local solution,
>    * there is still another strict one $x_1^* \in \Omega \cap \mathcal{N}_1$, where $\mathcal{N}_1 \subset \mathcal{N}$ and $x_1^* > x^*$.
>    * An example of $x_1^*$ is the solution of $f(x) = \begin{cases} x^4 \cos\left(\frac{1}{x}\right) + 2x^4, & x \neq 0, \\ 0, & x = 0. \end{cases}$, as shown in the figure below.

{{< img-resize src="constrained_opt_strnotiso.png" display_width="100%" title="An example of a strict local solution but not an isolated one. No matter how small the region around the strict local solution is, there is always another strict one within its own local region and having a greater value." caption="Source: Notes on Numerical Optimization" >}}
