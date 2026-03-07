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

Theoretically, there exists a neighborhood $\mathcal{N}$ of $x^*$, in which $f(x) < f(x^*)$ for $ x \neq x^*$. But $\mathcal{N}$ may not be practically specified.

### Isolated local solutions

There exists a neighborhood $\mathcal{N}$ of $x^*$, in which $f(x) < f(x^*)$ for $ x \neq x^*$. And $\mathcal{N}$ may not be practically identified.
