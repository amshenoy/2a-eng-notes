# Inference

## Matrix Calculus

$ \Large \dfrac{\partial}{\partial \underline{x}} \enspace \Big( \underline{b}^{T} \underline{x} \Big) = \underline{b} $

$ \Large \dfrac{\partial}{\partial \underline{x}} \enspace \Big( \underline{x}^{T} B \underline{x} \Big) = (B+B^{T}) \underline{x} $


</br>

### Completing the Square

### Given $ \large \underline{x}^{T} B \underline{x} + 2 b^{T} x $ and $ B $ is $ \color{green}{\text{symmetric}} $ and $\color{green}{\text{invertible}}$ :

$ \large \underline{x}^{T} B \underline{x} + 2 b^{T} \color{green}{B^{-1} B} \ x $

### Let $ \color{green}{ \underline{u} = B^{-1} \underline{b} } $ and $ \color{green}{ \underline{u}^{T} = \underline{b}^{T} B^{-T} 
 = \underline{b}^{T} B^{-1} 
 } $ 

$ \large \underline{x}^{T} B \underline{x} + 2 \color{green}{ \underline{u}^{T} } B \ x = \underline{x}^{T} B \underline{x} + \color{green}{ \underline{u}^{T} } B \ x +  \color{green}{ \underline{u}^{T} } B \ x $

</br>

$ \large (\underline{x}^{T} + \underline{u}^{T}) B \underline{x} + \color{green}{ \underline{u}^{T} } B \underline{x} $

$ \large (\underline{x}^{T} + \underline{u}^{T}) B (\underline{x} + \color{green}{ \underline{u} }) - \color{green}{ (\underline{x}^{T} + \underline{u}^{T}) B \underline{u} } + \underline{u}^{T} B \underline{x} $


$ \large (\underline{x}^{T} + \underline{u}^{T}) B (\underline{x} + \underline{u} ) - (\underline{x}^{T} + \underline{u}^{T}) \color{green}{ \underline{b} } + \color{green}{ \underline{b}^{T} } \underline{x} $

$ \large (\underline{x}^{T} + \underline{u}^{T}) B (\underline{x} + \underline{u} ) - \underbrace{\underline{u}^{T} \underline{b}}_{\underline{b}^{T} \underline{u}} $


</br><hr>

# General Linear Model

## Formulation
$$ \Large \mathbf{x} = \mathbf{G} \boldsymbol{\theta} + \mathbf{e} $$

Therefore at a point in time $ n $:
 
$$ \Large x_{n} = \mathbf{g_{n}}^{T} \boldsymbol{\theta} + e_{n} $$

</br>

## Bayesian Theory







</br>

## Estimation Theory

### Unbiased if $ E(\hat{\underline{\theta}}) = \underline{\theta} $

### Consistent if $ \text{Var}(\hat{\underline{\theta}}) \rightarrow 0 \text{ as } N \rightarrow \infty $ and unbiased


</br>

# Estimators


## Ordinary Least-Squares (OLS)

$$ \Large \dfrac{d}{d \underline{\theta}} \underline{e}^{T} \underline{e} = 0 $$

$$ \Large \color{blue}{ \hat{\underline{\theta}}_{\text{OLS}} = (G^{T} G)^{-1} \ G^{T} \underline{x} }$$ 

</br></br>

## Maximum Likelihood (ML)

$$ \Large \hat{\underline{\theta}}_{\text{ML}} = \arg \max_{\underline{\theta}} \{ P(\underline{x} | \underline{\theta}) \} $$ 

To solve for $ \hat{\underline{\theta}}_{\text{ML}} $:

$$ \Large \color{blue}{ \dfrac{d}{d \underline{\theta}} P(\underline{x} | \underline{\theta}) = 0 } $$

#### Consider $ \color{purple}{ \text{ log-likelihood } } $ where suitable.

</br>

$$ x_{n} = \mathbf{g_{n}}^{T} \boldsymbol{\theta} + e_{n} $$

$$ P(x_{n} | \theta_{n}) = P_{e}(e_{n}) $$

$$ P(\underline{x} | \underline{\theta}) = \prod_{n} P_{e}(e_{n}) = \prod_{n} P_{e}(x_{n} - \mathbf{g_{n}}^{T} \boldsymbol{\theta}) $$


</br></br>

## Minimum Mean-Squared Error (MMSE)

$$ \Large \dfrac{d}{d \underline{\theta}} E( (\underline{\hat{\theta}} - \underline{\theta})^{2} ) = 0 $$

Simplifies to (for solving for $ \hat{\underline{\theta}}_{\text{MMSE}} $) using the **posterior**:

$$ \Large \color{blue}{ \hat{\underline{\theta}}_{\text{MMSE}} = E (\underline{\theta}|\underline{x}) = \int \underline{\theta}  P(\underline{\theta}|\underline{x}) d \underline{\theta} } $$

</br></br>

## Maximum A Posteriori (MAP)

$$ \Large \hat{\underline{\theta}}_{\text{MAP}} = \arg \max_{\underline{\theta}} \{ P(\underline{\theta} | \underline{x}) \} $$ 

To solve for $ \hat{\underline{\theta}}_{\text{MAP}} $:

$$ \Large \color{blue}{ \dfrac{d}{d \underline{\theta}} P(\underline{\theta} | \underline{x}) = 0 } $$

#### Consider $ \color{purple}{ \text{ log-posterior } } $ where suitable.

</br></br>


# Comparison


### Least Squares (LS)
* (+) Requires no knowledge of probability distributions 
* (+) Simplest to implement  
* (+) Guarantee of performance as BLUE (**Best Linear Unbiased Estimator**) estimator 
* (-) Cannot incorporate prior knowledge about parameter probability distributions 
* No guarantees of performance compared to nonlinear estimators

### Maximum Likelihood (ML)
* (+) Performance guaranteed to be optimal when the amount of data is large
* (-) Requires knowledge of noise (model) probability distribution 
* (-) Cannot incorporate prior knowledge about parameter probability distributions 
* (-) Can be more complicated to implement than LS in the non-Gaussian case



### Bayesian (MAP and MMSE)
* (+) Incorporates prior knowledge
* (+/-) Performance guaranteed to be optimal for any amount of data (provided prior distribution is correct) 
* (-) Requires knowledge of noise (model) probability distribution 
* (-) Requires knowledge of parameter prior probability distribution
* (-) Can be more complicated to implement than LS or ML, depending on form of likelihood and prior







