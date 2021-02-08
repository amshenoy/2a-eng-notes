# Regression
See 3F3 Inference $ \large \underline{x} = G \underline{\theta} + \underline{e}  $

## Non-Linear Basis (General Linear Model)

$ X $ - **Basis function matrix** containing a set of data $ \underline{x}^{T} $ or evaluated data from functions $\{\phi_{i}(\underline{x})\}$. ($ X $ is a diagonal matrix if it is a vector $ \underline{x}^{T} $)

$$ \Large
\begin{align*}
\underline{y} &= X \underline{w} + \underline{e} \\
\underline{y} &= [\phi_{1}(\underline{x}), ..., \phi_{m}(\underline{x})]^{T} \underline{w} + \underline{e}
\end{align*}
$$

#### Note: We partially differentiate wrt to the parameter of the distribution $ \underline{w} $ (could consider both $ \underline{w} $ and $ \sigma^{2} $).

##### Note: We generally consider $ \underline{e} $ to be gaussian for ease of solving but this is an assumption of our scenario.

**ML for Gaussian $ \underline{e} $ is Least Squares solution**.
$ \Large \underline{w} = X^{+} \underline{y} $ 

</br>

## Bayesian Regression

**Linear combination of Gaussian random variables**
$$ \Large \underline{y} = W \underline{x} + \underline{e} $$

$ \underline{x} \sim \mathcal{N}(\underline{m}_{x}, C_{x}) $

$ \underline{e} \sim \mathcal{N}(\underline{m}_{e}, C_{e}) $

$ W $ &emsp; Weight matrix

$ p(\underline{y}) $ is therefore a **multivariate Gaussian** with: </br>
**Mean vector** &emsp; &emsp; &emsp; $ \underline{m}_{y} = E(\underline{y}) = W E(\underline{x}) + E(\underline{e}) = W \underline{m}_{x} + \underline{m}_{e} $ </br>
**Covariance matrix** &emsp; $ C_{y} = Var(\underline{y}) = E(\underline{y} \ \underline{y}^{T}) - E(\underline{y})E(\underline{y}^{T}) $ </br>







