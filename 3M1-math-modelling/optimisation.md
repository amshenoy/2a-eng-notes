# Optimisation

# Introduction

## Prerequisites
### Hessian Matrix

$$ \nabla(\nabla f(x)) = H(f(x)) $$

$$ H_{i,j}(f(x)) = \dfrac{\partial f^{2}}{\partial x_{i} \partial x_{j}} $$

If $ H $ is **positive definite** at $ x^{*} $ then $ x^{*} $ is a minimum. $ (x-x^{*})^{T} H(x^{*}) (x-x^{*}) > 0 $

</br>

### Stationary Point
$ \nabla f(x^{*}) = 0 $

$ x^{*} $ is either a minimum, maximum or saddle.

#### Minima Types

**Global** - Global minimum (with other possible global minima) </br>
**Strong Global** - Single global minimum </br>
**Weak Local** - Local minimum (with other possible local minima, ie. a plateau) </br>
**Strong Local** - Singular local minimum </br>

</br>

## Constraints
- **Equality constraints** can sometimes be eliminated by substitution
- **Inequality constraints** can sometimes be left out and candidate results checked (we will treat them formally with KKT multipliers)

In general, constrained optimization is more difficult to solve than unconstrained optimization.

</br>

## Landscape Properties

### Modality

**Unimodality** - Single extremum </br>
**Strong Unimodality** - Gradient is always toward extremum </br>


### Convexity

For any two points $x_{1}$ and $x_{2}$:
$$ f(x_{2}) - f(x_{1}) \ge (\nabla f(x_{1}))^{T} (x_{2}-x_{1}) $$

- **Convex functions** have a **global minimum**
- **Convex functions** are **unimodal**, but not all unimodal functions are convex



</br><hr></br>

# Unconstrained Optimisation

## Convergence Criteria

Many ways of defining tolerance for convergence:

**Norm of the residual** &emsp; $ \lVert f(x_{k+1}) - f(x_{k}) \rVert < \epsilon_{f} $

**Norm of the error** &emsp; $ \lVert x_{k+1}) - x_{k} \rVert < \epsilon_{x} $

**Norm of the gradient** &emsp; $ \lVert \nabla f(x_{k}) \rVert < \epsilon_{g} $

**Search methods** find a **local minimum**. 
**Convex functions** have **only one minimum**. Therefore, the local minimum is also a global minimum.

</br>

### Rate of Convergence

$$ \lim_{k \rightarrow \infty} \dfrac{||x_{k+1}-x^{*}||}{||x_{k} - x^{*}||^{p}} = \beta $$

$ \beta $ - Convergence Ratio (Lower the better) </br>
$ p $ - Order of Convergence (Higher the better) [Linear $ p=1 $, Quadratic $ p=2 $]

</br>

## Line Search (1D)

### Golden Section Search

Given $[A,D]$ and $f(x)$:

$ \hat{\phi} = \phi - 1 \approx 0.618 $

$$
\begin{align*}
C \enspace  &= \enspace A + \hat{\phi} \cdot (D-A) \\
B \enspace &= \enspace A + (1-\hat{\phi}) \cdot (D-A) \qquad = D - \hat{\phi} \cdot (D-A) \\ \\
\text{if } f(B) < f(C)&: \qquad [A, C] \\
\text{elif } f(C) < f(B)&: \qquad [B, D] \\
\end{align*}
$$

</br>

### Quadratic Fitting (at 3 points)


</br>

## Gradient methods

### Newton's Method

**Equivalent to quadratic fitting at one point** (Taylor Series)

$$ \large x_{k+1} = x_{k} - \dfrac{f^{'}(x_{k})}{f^{''}(x_{k+1})} $$


### Quasi-Newton Methods






</br><hr></br>

# Constrained Optimisation

## Simplex Algorithm (Linear Programming)

**Linear programming** algorithm for solving a **linear problem** with **linear constraints**.

[Simplex Calculator](https://www.zweigmedia.com/simplex/simplex.php?lang=en)


## Lagrange and Karush-Kuhn-Tucker (KKT) multipliers
Note that the Karush-Kuhn-Tucker (KKT) multipliers (Kuhn-Tucker (KT) multipliers)

## Barrier and Penalty Methods




</br><hr></br>

# Simulated Annealing (Global)












