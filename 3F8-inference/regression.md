# Regression
See 3F3 Inference $ \underline{x} = G \underline{\theta} + \underline{e}  $

### Maximum a Posteriori (MAP)

### Maximum Likelihood (ML)



## Non-Linear Basis

$ X $ - **Basis function matrix** containing a set of data $ \underline{x}^{T} $ or evaluated data from functions $\{\phi_{i}(\underline{x})\}$. ($ X $ is a diagonal matrix if it is a vector $ \underline{x}^{T} $)

$$ \Large
\begin{align*}
\underline{y} &= X \underline{w} + \underline{e} \\
\underline{y} &= [\phi_{1}(\underline{x}), ..., \phi_{m}(\underline{x})]^{T} \underline{w} + \underline{e}
\end{align*}
$$

#### Note: We partially differentiate wrt to the parameter of the distribution (could consider both $ \underline{w} $ and $ \sigma^{2} $).

##### Note: We generally consider $ \underline{e} $ to be gaussian for ease of solving but this is an assumption of our scenario.



## Bayesian Regression




