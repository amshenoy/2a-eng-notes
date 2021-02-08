# Optimisation

# Introduction

## Prerequisites
### Hessian Matrix

$$ \nabla(\nabla f(x)) = H(f(x)) $$

$$ H_{i,j}(f(x)) = \dfrac{\partial f^{2}}{\partial x_{i} \partial x_{j}} $$

If $ H $ is **positive definite** at $ x^{*} $ then $ x^{*} $ is a minimum. $ (x-x^{*})^{T} H(x^{*}) (x-x^{*}) > 0 $

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

## Line search
## Gradient methods


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













