# Optimisation

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

# Line Search (1D Optimisation)

## Golden Section Search


## Newton's Method

**Equivalent to fitting a quadratic at one point**

$$ x_{k+1} = x_{k} - \dfrac{f^{'}(x_{k})}{f^{''}(x_{k+1})} $$





