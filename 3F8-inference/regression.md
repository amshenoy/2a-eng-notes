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

# Bayesian Regression

$$ \Large \underline{y} = X \underline{w} + \underline{e} $$

$ \underline{x} \sim \mathcal{N}(\underline{m}_{x}, C_{x}) $

Assuming zero-mean noise:</br>
$ \underline{e} \sim \mathcal{N}(\underline{m}_{e}=\underline{0}, C_{e}= \sigma_{e}^{2} I) $

</br>

## Formulation

### Likelihood

$$ \large 
\begin{align*}
p(\underline{y}|\underline{w}) &= \prod_{i}^{N} \mathcal{N}(y_{i}-\underline{w}^{T} \underline{x}_{i}-\mu_{e}, \sigma_{e}^{2}) = \mathcal{N}(\underline{y} - X\underline{w} - \underline{m}_{e}, C_{e}) \\
&\propto \exp(-\dfrac{1}{2} (\underline{y} - X\underline{w} - \underline{m}_{e})^{T} C_{e}^{-1} (\underline{y} - X\underline{w} - \underline{m}_{e}) ) \\
&\propto \exp(-\dfrac{1}{2} \sigma_{e}^{-2} \big( (X\underline{w})^{T} (X\underline{w}) - 2\underline{y}^{T} X \underline{w} \big) \ )
\end{align*}
$$

</br>

### Prior ( Zero-Mean Isotropic Gaussian )
We assume a zero-mean isotropic Gaussian for the weights.

$$ \large
\begin{align*}
p(\underline{w}) &= \mathcal{N}(\underline{0}, \sigma_{w}^{2} I) \\
&\propto \exp(-\dfrac{1}{2} \underline{w}^{T} ( \sigma_{w}^{-2} I )
\underline{w})
\end{align*}
$$

### Posterior

$$ \large
\begin{align*}
p(\underline{w} | \underline{y}) &\propto p(\underline{w}) \ p(\underline{y}|\underline{w}) \\
&\propto \exp(-\dfrac{1}{2} \big( \underline{w}^{T} \ \underbrace{( \sigma_{e}^{-2} X^{T} X - \sigma_{w}^{-2} I )}_{C_{po}^{-1}}
\ \underline{w} - 2 \ \underbrace{ \sigma_{e}^{-2} \underline{y}^{T} X }_{\underline{m}_{po}^{T} C_{po}^{-1}} \underline{w} \big) ) \\
&= \mathcal{N}(\underline{w}|\underline{m}_{po}, C_{po}) 
\end{align*}
$$

</br>

## Predictive Distribution

$$ \large
\begin{align*}
p(y^{*}|\underline{x}^{*}, \underline{y}, X) &= \int p(y^{*}|\underline{x}^{*}, \underline{w}) \ p(\underline{w}|\underline{y}, X) \ d\underline{w} \\
&= \int \mathcal{N}(y^{*} - \underline{w}^{T}\underline{x}^{*}| 0, \ \sigma_{e}^{2}) \ \mathcal{N}(\underline{w}|\underline{m}_{po}, \ C_{po}) \ d\underline{w} 
\end{align*}
$$

#### Exact inference is possible if both prior and noise are Gaussian

Instead of directly performing the above computations, we can use the function of a random variable for $ y^{*} $ for a given $ \underline{x}^{*} $:

$$ \Large \color{blue}{
y^{*} = \underbrace{\underline{w}^{T}}_{\underbrace{\mathcal{N}(\underline{w}|\underline{m}_{po}, \ C_{po})}_{\text{Posterior}}} \underline{x}^{*} + \underbrace{\underline{e}}_{ \mathcal{N}(y^{*} - \underline{w}^{T}\underline{x}^{*}| 0, \ \sigma_{e}^{2}) } 
}
$$

Since the **sum of Gaussians is a Gaussian**, the **predictive distribution** is given by:

$$ \Large p(y^{*}|\underline{x}^{*}, \underline{y}, X) = \mathcal{N}(y^{*}| m^{*}, C^{*}) $$

$ \large m^{*} = E(y^{*}) = \underline{m}_{po}^{T} \ \underline{x}^{*} $

$ \large C^{*} = Var(y^{*}) = \underline{x}^{*T} \ C_{po} \ \underline{x}^{*} + \sigma_{e}^{2} $

</br>

#### Confidence bands: $ m^{*} \pm (C^{*})^{1/2} $

