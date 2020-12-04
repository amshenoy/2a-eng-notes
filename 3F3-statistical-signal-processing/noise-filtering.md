# Noise Filtering

## Correlation Function

### Auto-Correlation
### Similary auto-correlation function as from stochastic processes: $ r_{XX}[k] = r_{XX}[-k] $

### Cross-Correlation
### $$ \color{blue}{ r_{XY}[k] = E(X_{n} Y_{n+k}) = E(Y_{n+k} X_{n}) = r_{YX}[-k] } $$

## Covariance Function

### Auto-Covariance
### $$ \color{blue}{ c_{XX}[k] = E((X_{n}-\mu)(X_{n+k}-\mu)) } \qquad \text{where } \mu = E(X_{n})  $$

### Cross-Covariance

### $$ \color{blue}{ c_{XY}[k] = E((X_{n}-\mu_{X})(Y_{n+k}-\mu_{Y})) }  $$

## White Noise
A process $ X_{n} $ is a **white noise process** if:
### $$ \color{red}{ c_{XX}[k] = \sigma_{X}^{2} \enspace \delta(k) } $$

## Mean Ergodic
A process $ X_{n} $ is mean ergodic if:
### $$ \color{red}{ \lim_{k \rightarrow \infty} c_{XX}[k] = 0 } $$


</br><hr>


# Example System
### For input $ x_{n} $, noise $ v_{n} $ and output $ y_{n} $:
## $$ y_{n} = x_{n} + v_{n} $$

### General Properties
#### If input and noise are uncorrelated &emsp; $ \color{blue}{ r_{vx}[k] = E( V_{n} X_{n+k} ) = 0  \qquad \therefore r_{yx}[k] = r_{xx}[k] \qquad r_{yy}[k] = r_{xx}[k] + r_{vv}[k] } $
#### Noise is WSS &emsp; $ \color{blue}{ r_{vv}[k] = E(V_{n}V_{n+k}) = E(V_{n}^{2}) \delta(k) } \qquad \text{As } E(V_{i}V_{j}) = 0 \text{ for } i \ne j $

</br>

#### Note: In the general case, $ r_{xx}[k] = E(X_{n} X_{n+k}) $ giving $ E(X_{n}^{2}) $ for $ k=0 $ and $ E(X_{n})E(X_{n+k}) $ for $ k \ne 0 $ which can be written as $ \color{green}{ r_{xx}[k] = \mu^{2} + \sigma^{2} \delta(k) } $.

</br><hr>


# Wiener Filter
**Wiener filter** shows how to extract a **random signal from random noise**.

**Wiener filter** is only the **optimal linear estimator** for **stationary signals**. The Kalman filter offers an extension for non-stationary signals via state space models. In cases where a linear filter is still not good enough, non-linear filtering techniques can be adopted.

## Wiener-Hopf Equations

### If we are trying to estimate $ \color{purple}{ \hat{x_{n}} = h_{n} * y_{n} } $ (ie. $ y_{n} = f(x_{n}) $ ), then from the Wiener-Hopf equations, we can derive the filter:


$$ \Large \color{purple}{ r_{yx}[q] =\sum_{p=-\infty}^{\infty} h_{p} r_{yy}[q-p]  
\\ \underline{r_{yx}} = R_{YY} \underline{h} 
}
$$
 
## $$ \color{blue}{ \underbrace{\underline{h}}_{\scriptsize \text{Coefficients of Wiener Filter}} = R_{YY}^{-1} \enspace \underline{r_{yx}} } $$

### $ R_{YY} $ is a symmetric matrix from the vector $ \underline{r_{yy}} $

$ \color{red}{ \text{Note: Always derive the Wiener-Hopf equations using the least MSE criterion unless a convolution is given.} } $

</br>

## Estimation
We can remove the noise from the output signal $ x_{n} $ by applying the filter $ h_{n}$ to get an estimation of the input signal $ \hat{x_{n}} $:
## $$ \color{red}{ \hat{x_{n}} = h_{n} * y_{n} = \sum_{p=0}^{\infty} h_{p} y_{n-p} } $$

</br>

## Mean-Squared Error (MSE)

### $$ \color{green}{ J = E( (\epsilon_{n})^{2} ) = E( (\hat{x_{n}} - x_{n})^{2} ) } $$

### Least MSE Criterion

Use this to **derive the Wiener-Hopf equations** for a given problem:

$$ \color{blue}{
\Large \dfrac{\partial}{\partial h_{i}} E(\epsilon_{n}^{2}) = E(2 \epsilon_{n} \dfrac{\partial \epsilon_{n}}{\partial h_{i}} ) = 0
}
$$

#### Orthognality Principle
$ \therefore \Large E(\epsilon_{n} y_{n-p}) = 0 $

$
E((x_{n} - \hat{x}_{n}) y_{n-q}) = E((x_{n} - \sum_{p=0}^{\infty} h_{p} y_{n-p} ) y_{n-q}) = 0 \\ E(x_{n}y_{n-q}) - \sum_{p=0}^{\infty} h_{p} E( y_{n-p} y_{n-q} ) = 0 \\
$ 

Wiener-Hopf Equations Derived:

$ \large
\therefore E(x_{n}y_{n-q}) = \sum_{p=0}^{\infty} h_{p} E( y_{n-p} y_{n-q} )
$

</br>

### Minimum Error
### $ 
\begin{align*}
J_{min} &= E(\epsilon_{n}^{2}) = E(\epsilon_{n} x_{n}) \qquad \small \text{Simplifies to this using the orthognality principle} \\ \\ 
&= E((x_{n} - \hat{x_{n}}) x_{n} ) = E(x_{n}^{2}) - E(\hat{x_{n}}x_{n}) \\ \\
&= E(x_{n}^{2}) - E(x_{n} (\sum_{p=0}^{\infty} h_{p} y_{n-p})) = E(x_{n}^{2}) - \sum_{p=0}^{\infty} h_{p} E(y_{n-p} x_{n}) \\
J_{min} &= r_{xx}(0) - \sum_{p=0}^{\infty} h_{p} r_{yx}(p) \\
J_{min} &= r_{xx}(0) - \underline{h} \cdot \underline{r_{yx}}
\end{align*}
$

## $$ \color{blue}{ J_{min} = r_{xx}(0) - \underline{h} \cdot \underline{r_{yx}} } $$

Power of the error signal can be found by performing the inverse fourier transform on $ J_{min} $.

## Wiener Gain

Taking the **DTFT of the Wiener-Hopf** equations:

$$ \Large \color{purple}{ H(e^{j \theta}) = \dfrac{S_{yx}(e^{j \theta})}{S_{y}(e^{j \theta})} } $$

If noise and input are uncorrelated then $ S_{yx} = S_{xx} $ and $ S_{yy} = S_{xx} + S_{vv} $:

$ H(e^{j \theta}) = \dfrac{S_{xx}}{S_{xx} + S_{vv}} = \dfrac{1}{1+ \dfrac{1}{\text{SNR}} }$

</br><hr>

# Matched Filter
**Matched filter** shows how to extract a **known deterministic signal from random noise**.

## $$ \color{blue}{ \underbrace{\underline{h_{\text{opt}}}}_{\scriptsize \text{Coefficients of Matched Filter}} = \dfrac{\underline{\tilde{x}}}{|\underline{\tilde{x}}|} } \qquad \small ( \text{where }\underline{\tilde{x}}\text{ is } \underline{x} \text{ time-reversed })$$

$$ \text{SNR} = \dfrac{E(|\mathbf{h} \mathbf{\tilde{s}}|^{2})}{E(|\mathbf{h} \mathbf{\tilde{v}}|^{2})} = \dfrac{|\mathbf{h} \mathbf{\tilde{s}}|^{2}}{\sigma_{v}^{2} \mathbf{h}_{T} \mathbf{h} } $$

#### Instead of minimising the MSE like for Wiener, here we try to maximise the SNR:

## $$ \color{blue}{
\text{SNR}_{\text{opt}} = \dfrac{ \underline{\tilde{x}} \cdot \underline{\tilde{x}} } {\sigma_{v}^{2}} = \dfrac{ |\underline{\tilde{x}}|^{2} } {\sigma_{v}^{2}} 
} $$

</br><hr>


# Orthognal Signals

Consider $ \large y_{n} = s_{1,n} + s_{2, n} + v_{n} $ where $ s_{1, n} $ and $ s_{2, n} $ are orthognal to each other:

Since the two signals are orthognal, both signals can be extracted by applying their respective filters $ h_{1} $ and $ h_{2} $.

$ \large \hat{s_{1,n}} = h_{1} * y_{n} $

$ \large \hat{s_{2,n}} = h_{2} * y_{n} $




 
