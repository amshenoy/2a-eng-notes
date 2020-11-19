# Line Search (1D Optimisation)

## Convergence Criteria

Many ways of defining tolerance for convergence:

**Norm of the residual** &emsp; $ \lVert f(x_{k+1}) - f(x_{k}) \rVert < \epsilon_{f} $

**Norm of the error** &emsp; $ \lVert x_{k+1}) - x_{k} \rVert < \epsilon_{x} $

**Norm of the gradient** &emsp; $ \lVert \nabla f(x_{k}) \rVert < \epsilon_{g} $

**Search methods** find a **local minimum**. 
**Convex functions** have **only one minimum**. Therefore, the local minimum is also a global minimum.

</br>

## Rate of Convergence



</br><hr>

# Methods

## Golden Section Search


## Quadratic Fitting (at 3 points)



## Newton's Method

**Equivalent to quadratic fitting at one point**

$$ x_{k+1} = x_{k} - \dfrac{f^{'}(x_{k})}{f^{''}(x_{k+1})} $$


## Quasi-Newton Methods




</br><hr>



