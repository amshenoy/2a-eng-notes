# Optimisation

# Introduction

## Prerequisites

### Jacobian Matrix

$$ J_{ij}(\underline{f}(\underline{x})) = \dfrac{\partial f_{i}}{\partial x_{j} } $$

This is for the case of vector function $ \underline{f}(\underline{x}) = \{ \underline{f}(x_{1}), ..., \underline{f}(x_{N}), \} $.

For the case of a 1D function, the Jacobian $ J $ is the same as the gradient $ \nabla $.



### Hessian Matrix

$$ \nabla(\nabla f(x)) = H(f(x)) $$

Or equivalently the $ J(\nabla f(x)) = H(f(x)) $.

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

# Line Search (1D)

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

Given $ x_{1}, x_{2}, x_{3} $, we want to find the coefficients     $ a_{1}, a_{2}, a_{3} $:

$$ 
\begin{bmatrix}
    f(x_{1}) \\
    f(x_{2}) \\
    f(x_{3})
\end{bmatrix}
= 
\begin{bmatrix}
    1 & x_{1} & x_{1}^{2} \\
    1 & x_{2} & x_{2}^{2} \\
    1 & x_{3} & x_{3}^{2} \\
\end{bmatrix}
\begin{bmatrix}
    a_{1} \\
    a_{2} \\
    a_{3} \\
\end{bmatrix}
$$

</br>

## Gradient methods

### Newton's Method

**Equivalent to quadratic fitting at one point** (Taylor Series)

$$ \large x_{k+1} = x_{k} - \dfrac{f^{'}(x_{k})}{f^{''}(x_{k+1})} $$


### Quasi-Newton Methods

#### Secant Method
**Using an approximation for $ f^{''}(x_{k+1}) $**
$$ \large x_{k+1} = x_{k} - \dfrac{f^{'}(x_{k})}{\dfrac{f^{'}(x_{k})-f^{'}(x_{k-1})}{x_{k}-x_{k-1}}} $$


# Multi-Dimensional

<table style="width:100%">
  <tr>
    <th>Method</th>
    <th>Advantages</th>
    <th>Disadvantages</th>
  </tr>
  <tr>
    <td>Steepest Descent</td>
    <td>Only needs <strong>gradient</strong></td>
    <td> <strong>Linear</strong> convergence</td>
  </tr>
  <tr>
    <td>Conjugate Gradient</td>
    <td>Only needs  <strong>conjugate gradient</strong>. Faster than Steepest Descent</td>
    <td> <strong>Linear</strong> convergence</td>
  </tr>
  <tr>
    <td>Gauss-Newton <small>(Derived by $\nabla$ Least-Squares Error)</small></td>
    <td>Only need <strong>Jacobian</strong>. Near  <strong>quadratic</strong> convergence.</td>
    <td> <strong>Poor performance if poor initialisation </strong> (starting point is far from optimum)</td>
  </tr>
  <tr>
    <td>Newton-Raphson</td>
    <td> <strong>Quadratic</strong> convergence</td>
    <td>Needs <strong>Hessian</strong>. Possible  <strong>divergence</strong>.</td>
  </tr>
  <tr>
    <td>Barzilai-Borwein</td>
    <td>Faster than Steepest Descent. Often <strong>very stable </strong>.</td>
    <td> <strong>Convergence analysis difficult </strong>.</td>
  </tr>
</table>


</br><hr></br>

# Constrained Optimisation

</br>

## Linear Programming

**Linear programming** algorithm for solving a **linear problem** with **linear constraints**.

### Hand Solution

1) Formulate $ n $-variable **Cost Function**

2) Formulate $ m $ **Constraint Equations**

3) **Compute total cost when $ n-m $ variables are a 0**

&emsp; &emsp; &emsp; **$ n-m $ variables must equal 0 for an extremal point (optimum must be an extremal point)**

&emsp; &emsp; &emsp; Set $ n-m $ variables to 0 in turn and solve for other variables using constraint equations.

&emsp; &emsp; &emsp;  Substitute values into the cost function to get the total cost.

4) **Solutions: The values that give a valid minimum total cost**



</br>

### Simplex Algorithm

[Simplex Calculator](https://www.zweigmedia.com/simplex/simplex.php?lang=en)



</br>

## Lagrange [$ \lambda_{i} $] and Karush-Kuhn-Tucker (KKT) [$ \mu_{j} $] multipliers

$$ \large L(\underline{x}, \underline{\lambda}, \underline{\mu}) = f(\underline{x}) + \sum_{i} \lambda_{i} h_{i}(\underline{x}) + \sum_{j} \mu_{j} g_{j}(\underline{x}) $$

 $ h_{i}(\underline{x}) $ - Equality constraints $ = 0 $ </br>
 $ g_{j}(\underline{x}) $ - Inequality constraints $ \le 0 $ </br>

$ \mu_{j} = 0 $ if $ g_{j}(\underline{x}) < 0 $ (**inequality constraint inactive**)

$ g_{j}(\underline{x}) = 0 $ (**inequality constraint active**, becomes an equality constraint)

#### Minimise by solving $ \large \nabla L = \underline{0} $
In the case when $ L(\underline{x}, \underline{\lambda}, \underline{\mu} ) $ is **scalar**:
$
\dfrac{\partial L}{\partial \underline{x}} = \dfrac{\partial L}{\partial x_{i}}|_{i=1}^{N} = 0 $.

</br>

## Penalty Method

> The idea is to replace the **constrained** optimisation problem with an **approximated unconstrained** (**soft constraints**) optimisation problem

$$ \large Q(\underline{x}, \underline{\lambda}, \underline{\mu}) = f(\underline{x}) + \kappa \sum_{i} \ P\Big( h_{i}(\underline{x}) \Big) $$

$ \large \kappa $ - Adjustable **Penalty Parameter** </br>
$ \large P( \cdot ) $ - **Penalty Function**

</br>

(+) Can handle both **inequalities and equalities**

(-) **May provide unfeasible solutions** 

</br>

#### Note: We typically start with small $ \kappa $ and increase it as the solution gets closer to the optimum (so that the impact of the penalty function is increased for the small error thus becoming more accurate towards the end).

</br> </br>

## Barrier Method

> With a barrier method, the feasibility is enforced exactly by using a penalty that diverges as we approach the boundary of the constraint.

$$ \large Q(\underline{x}, \underline{\lambda}, \underline{\mu}) = f(\underline{x}) - \dfrac{1}{\kappa} \sum_{j} \ B\Big( g_{j}(\underline{x}) \Big) $$

$ \large \kappa $ - Adjustable **Penalty Parameter** </br>
$ \large B( \cdot ) $ - **Barrier Function** eg. $ B(x) = \dfrac{1}{x} $ or $ B(x) = \ln(-x) $

</br>

(+) Will always provide **feasible solutions**</br>
(+) Sharp divergence at constraint boundaries for large $ \kappa $ hence **can get solutions closer to the constraint boundary**.

(-) Can only handle **inequalities** </br>
(-) Sharp divergence at constraint boundaries for large $ \kappa $ hence **harder the optimisation** </br>




</br>

</br><hr></br>

# Simulated Annealing (Global)

Given the cost (ie. energy) function $ E(x) $: 

The following **update step is performed with probability** $ p $:
$$ \Large x_{n+1} \underbrace{\leftarrow}_{p} x_{n} + U(-\frac{1}{2}, \frac{1}{2}) \ h $$

where $ \Large p = \min (e^{-\frac{\Delta E }{T}}, 1) $ and $ \Delta E = E(x_{n+1}) - E(x_{n}) $.

The **temperature is updated deterministically** using a cooling rate parameter $ R $.
$$ T_{n+1} = T_{n} \ (1 - R) $$


### Limitations

- High $ h $ does not explore enough. Low $ h $ explores too slowly. 
- High $ R $ means possible to not converge. Low $ R $ means high computational requirements. 
- No stopping condition














