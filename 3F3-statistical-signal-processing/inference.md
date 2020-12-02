# Inference

## Matrix Calculus

### Linear Differentiation
$ \Large \dfrac{\partial}{\partial \underline{x}} \enspace \Big( \underline{b}^{T} \underline{x} \Big) = \dfrac{\partial}{\partial \underline{x}} \enspace \Big( \underline{x}^{T} \underline{b} \Big) = \underline{b} $

### Quadratic Differentiation
$ \Large \dfrac{\partial}{\partial \underline{x}} \enspace \Big( \underline{x}^{T} B \underline{x} \Big) = (B+B^{T}) \underline{x} $

For a symmetric matrix $ B $, $ \large \dfrac{\partial}{\partial \underline{x}} \enspace \Big( \underline{x}^{T} B \underline{x} \Big) = 2 B \underline{x} $.


</br>

### Completing the Square

### Given $ \large \underline{x}^{T} B \underline{x} + 2 b^{T} x $ and $ B $ is $ \color{green}{\text{symmetric}} $ and $\color{green}{\text{invertible}}$ :

$ \large \underline{x}^{T} B \underline{x} + 2 b^{T} \color{green}{B^{-1} B} \ x $

### Let $ \color{green}{ \underline{u} = B^{-1} \underline{b} } $ and $ \color{green}{ \underline{u}^{T} = \underline{b}^{T} B^{-T} 
 = \underline{b}^{T} B^{-1} 
 } $ 

$ \underline{x}^{T} B \underline{x} + 2 \color{green}{ \underline{u}^{T} } B \ x = \underline{x}^{T} B \underline{x} + \color{green}{ \underline{u}^{T} } B \ x +  \color{green}{ \underline{u}^{T} } B \ x $

$ \large (\underline{x}^{T} + \underline{u}^{T}) B \underline{x} + \color{green}{ \underline{u}^{T} } B \underline{x} $

$ \large (\underline{x}^{T} + \underline{u}^{T}) B (\underline{x} + \color{green}{ \underline{u} }) - \color{green}{ (\underline{x}^{T} + \underline{u}^{T}) B \underline{u} } + \underline{u}^{T} B \underline{x} $


$ (\underline{x}^{T} + \underline{u}^{T}) B (\underline{x} + \underline{u} ) - (\underline{x}^{T} + \underline{u}^{T}) \color{green}{ \underline{b} } + \color{green}{ \underline{b}^{T} } \underline{x} $

$ (\underline{x}^{T} + \underline{u}^{T}) B (\underline{x} + \underline{u} ) - \underbrace{\underline{u}^{T} \underline{b}}_{\underline{b}^{T} \underline{u}} $

</br>

**Extremely important for multivariate gaussian products!**

$ \Large \color{blue}{ \underline{x}^{T} B \underline{x} \color{red}{-} 2 \underline{b}^{T} x \quad \rightarrow \quad (\underline{x} \color{red}{-} B^{-1} \underline{b})^{T} \ B \ (\underline{x} \color{red}{-} B^{-1} \underline{b} ) - \underline{b}^{T} (B^{-1} \underline{b}) } $

**Complete the square for multivariate gaussian**:
* $ B $ is Covariance Matrix
* $ B^{-1} \underline{b} $ is Mean Vector


</br><hr>

# General Linear Model

## Formulation
$$ \Large \mathbf{x} = \mathbf{G} \boldsymbol{\theta} + \mathbf{e} $$

Therefore at a point in time $ n $:
 
$$ \Large x_{n} = \mathbf{g_{n}}^{T} \boldsymbol{\theta} + e_{n} $$

</br>

## Einstein-Wiener-Khinchin Theorem

Consider a signal $ x_{n} $ windowed by the $ 2N+1 $ length window function $ w_{n}^{N} $ where $ −N \le n \le N $ to give an output $ x_{n}^{N} $ of length $ 2N+1 $:

$$ \Large x_{n}^{N} = w_{n}^{N} x_{n} $$


$$ \large
\begin{align*}
|X_{N}(e^{j\theta})|^{2} &= X_{N}(e^{j\theta})  X_{N}^{*}(e^{j\theta}) \\ 
&= \text{DTFT}\{x_{n}^{N} ∗ x_{-n}^{N} \} \\
&= \text{DTFT}\{ \sum_{m=-\infty}^{\infty} x_{m}^{N} \ x_{-(n-m)}^{N} \} \\
&= \text{DTFT}\{ \sum_{m=-\infty}^{\infty} ( w_{m}^{N} x_{m} )( w_{m-n}^{N} x_{m-n} ) \} \\
\end{align*}
$$

$$
\Large
\begin{align*}
\dfrac{1}{2N+1} E(|X_{N}(e^{j\theta})|^{2}) &= \dfrac{1}{2N+1} \text{DTFT}\{ \sum_{m=-\infty}^{\infty} w_{m}^{N} w_{m-n}^{N} E(x_{m} x_{m-n}) \} \\
&= \text{DTFT}\{ r_{xx}[n] \enspace \dfrac{1}{2N+1} \sum_{m=-\infty}^{\infty} w_{m}^{N} w_{m-n}^{N} \} \\
&= \text{DTFT}\{ r_{xx}[n] \enspace \dfrac{1}{2N+1} \sum_{m=-N}^{N} w_{m}^{N} w_{m-n}^{N} \} \\
&= \text{DTFT}\{ r_{xx}[n] E(w_{m}^{N} w_{m-n}^{N}) \} \\
&= \text{DTFT}\{ r_{xx}[n] \enspace r_{ww}[n] \} \\
\dfrac{1}{2N+1} E(|X_{N}(e^{j\theta})|^{2}) &= S_{xx}(e^{j\theta}) * S_{ww}(e^{j\theta})
\end{align*}
$$

</br>

#### Since $ S_{ww}(e^{j\theta}) \rightarrow \delta $ (delta function) as $ N \rightarrow \infty $:

$$ \Large \lim_{n \rightarrow \infty} \dfrac{1}{2N+1} E(|X_{N}(e^{j\theta})|^{2}) = S_{xx}(e^{j \theta})$$


</br>

## Estimation Theory

### Unbiased if $ E(\hat{\underline{\theta}}) = \underline{\theta} $

### Consistent if $ \text{Var}(\hat{\underline{\theta}}) \rightarrow 0 \text{ as } N \rightarrow \infty $ and unbiased


</br>

# Estimators


## Ordinary Least-Squares (OLS)

$$ \Large \dfrac{d}{d \underline{\theta}} \underline{e}^{T} \underline{e} = \dfrac{d}{d \underline{\theta}} \Big( \underline{x} - \mathbf{G} \underline{\theta}^{T} \Big) \Big( \underline{x} - \mathbf{G} \underline{\theta} \Big) = 0 $$

$$ \Large \color{blue}{ \hat{\underline{\theta}}_{\text{OLS}} = (G^{T} G)^{-1} \ G^{T} \underline{x} }$$ 

</br></br>

## Maximum Likelihood (ML)

$$ \Large \hat{\underline{\theta}}_{\text{ML}} = \arg \max_{\underline{\theta}} \{ P(\underline{x} | \underline{\theta}) \} $$ 

To solve for $ \hat{\underline{\theta}}_{\text{ML}} $:

$$ \Large \color{blue}{ \dfrac{d}{d \underline{\theta}} P(\underline{x} | \underline{\theta}) = 0 } $$

#### Consider $ \color{purple}{ \text{ log-likelihood } } $ where suitable.

</br>

Given $ x_{n} = \mathbf{g_{n}}^{T} \boldsymbol{\theta} + e_{n} $ (For iid RVs):

$$ P(x_{n} | \theta_{n}) = P_{e}(e_{n}) $$

$$ P(\underline{x} | \underline{\theta}) = \prod_{n} P_{e}(e_{n}) = \prod_{n} P_{e}(x_{n} - \mathbf{g_{n}}^{T} \boldsymbol{\theta}) $$

</br>

Given $ \underline{x} = \mathbf{G} \underline{\theta} + \underline{e} $ (Usually for multivariate gaussian):

$$ P(\underline{x} | \underline{\theta}) = P_{e}(\underline{x} - \mathbf{G} \underline{\theta}) $$


#### Note: When the error process $ e_{n} $ is independent and gaussian with mean zero and constant variance, the ML estimator is equal to the OLS estimator. 

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

</br>

$$ \large P(\underline{\theta} | \underline{x}) \propto  P(\underline{\theta}) P(\underline{x} | \underline{\theta}) $$

#### Note: By marginalisation, we can find the normalising constant (area of $ P(\underline{\theta} | \underline{x}) $ must equal 1) $ P(\underline{x}) = \int P(\underline{\theta}) P(\underline{x} | \underline{\theta}) \ d\underline{\theta} $ 


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

</br></br>

## Practical Solving

A gaussian in the form $ \propto e^{-\frac{1}{2} (ax^{2} + bx + c)} $ has variance $ \dfrac{1}{\hat{\sigma}^{2}} = a $ and $ \dfrac{-2\hat{\mu}}{\hat{\sigma}^{2}} = b $.

Essentially derive the constants from $ -\dfrac{1}{2} \dfrac{(x-\mu)^{2}}{\sigma^{2}} $.

In the multivariate case, $ \mu = \underline{m_{\theta}} $ and $ \sigma^{2} = \underline{C_{\theta}} $.

Always use log-posterior and likelihood where possible.

