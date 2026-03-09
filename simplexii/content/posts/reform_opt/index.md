+++
date = '2026-03-07T15:18:45Z'
draft = false
title = 'Reformulation Techniques in Optimization'
+++

## The motivation

In some optimization problems, the objective function or the constraint functions are not smooth, i.e. they have kinks and jumps. The smoothness of these function are useful because it guides the determination of `good (in what sense?)` search direction. Therefore, it is helpful to transform these functions into a different formulation in which they are represented with smooth function.

## Examples

### 1. The reformulation of a non-smooth objective function

$$
\min f(x) = \min(\max\{x, x^2\})
$$

can be reformulated as

$$
\begin{aligned}
\min t, &\quad \text{s.t. } \quad c_1(x) \le t, c_2(x) \le t, \\
\text{where} &\quad c_1(x) = x, c_2(x) = x^2.
\end{aligned}
$$

> 1. `Is` $t$ `a function of` $x$`?`
> 2. The components of the objective function in the original formulation become the constraint functions in the reformulation, and these constraint functions are compared `not with a constant`, but `with the new objective function` directly.
> 3. Note that $\min f(x) = \min(\max\{x, x^2\}) \neq \left\| y \right\|_\infty$, where $y=[x, x^2]$, because $\left\| y \right\|_\infty=\max\{|x|, |x^2|\}$.

<!-- $$
\begin{equation}
\begin{aligned}
\min t & \\
\text{subject to} & \\
t & \ge x \\
t & \ge x^2 
\end{aligned}
\end{equation}
$$ -->

### 2. The reformulation of a non-smooth constraint function

$$
\left\| x \right\|_1 = |x_1| + |x_2| \le 1, \quad \text{where } x = [x_1, x_2]
$$

can be reformulated as

$$
x_1 + x_2 \le 1, \quad x_1 - x_2 \le 1, \quad -x_1 + x_2 \le 1, \quad -x_1 - x_2 \le 1.
$$