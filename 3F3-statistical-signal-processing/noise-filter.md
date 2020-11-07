# Noise Filter

## Correlation Function

### Auto-Correlation
### Similary auto-correlation function as from stochastic processes: $ r_{XX}[k] = r_{XX}[-k] $

### Cross-Correlation
### $$ \color{blue}{ r_{XY}[k] = E(X_{n} Y_{n+k}) = E(Y_{n+k} X_{n}) = r_{YX}[-k] } $$

## Covariance Function

### Auto-Covariance
### $$ \color{blue}{ c_{XX}[k] = E((X_{n}-\mu)(X_{n+k}-\mu)) } \qquad \text{where } \mu = E(X_{n})  $$

### Cross-Covariance

## White Noise
A process $ X_{n} $ is a **white noise process** if:
### $$ \color{red}{ c_{XX}[k] = \sigma_{X}^{2} \enspace \delta(k) } $$

## Mean Ergodic
A process $ X_{n} $ is mean ergodic if:
### $$ \color{red}{ \lim_{k \rightarrow \infty} c_{XX}[k] = 0 } $$


# Example System
### For input $ x_{n} $, noise $ v_{n} $ and output $ y_{n} $:
## $$ y_{n} = x_{n} + v_{n} $$

### General Properties
#### Input and noise are uncorrelated &emsp; $ \color{blue}{ r_{vx}[k] = E( V_{n} X_{n+k} ) = 0 } $
#### Noise is WSS &emsp; $ \color{blue}{ r_{vv}[k] = E(V_{n}V_{n+k}) = E(V_{n}^{2}) \delta(k) } \qquad \text{As } E(V_{i}V_{j}) = 0 \text{ for } i \ne j $

</br>

# Wiener Filter
**Wiener filter** shows how to extract a random signal from random noise.

**Wiener filter** is only the **optimal linear estimator** for **stationary signals**. The Kalman filter offers an extension for non-stationary signals via state space models. In cases where a linear filter is still not good enough, non-linear filtering techniques can be adopted.

## $$ \color{blue}{ \underbrace{\underline{h}}_{\scriptsize \text{Coefficients of Wiener Filter}} = R_{XX}^{-1} \enspace \underline{r_{xy}} } $$

### $ R_{XX} $ is a symmetric matrix from the vector $ \underline{r_{xx}} $

</br>

## Estimation
We can remove the noise from the output signal $ x_{n} $ by applying the filter $ h_{n}$ to get an estimation of the input signal $ \hat{x_{n}} $:
## $$ \color{red}{ \hat{x_{n}} = h_{n} * y_{n} = \sum_{p=0}^{\infty} h_{p} y_{n-p} } $$

</br>

### Mean-Squared Error (MSE)

### $$ \color{green}{ J = E( (\epsilon_{n})^{2} ) = E( (\hat{x_{n}} - x_{n})^{2} ) } $$
 
### Minimum Error

### $$ 
\begin{align*}
J_{min} &= E(\epsilon_{n}^{2}) = E(\epsilon_{n} x_{n}) = E((x_{n} - \hat{x_{n}}) x_{n} ) \\ 
&= E(x_{n}^{2}) - E(\hat{x_{n}}x_{n}) \\
&= E(x_{n}^{2}) - E(x_{n} (\sum_{p=0}^{\infty} h_{p} y_{n-p})) = E(x_{n}^{2}) - \sum_{p=0}^{\infty} h_{p} E(y_{n-p} x_{n}) \\
J_{min} &= r_{xx}(0) - \sum_{p=0}^{\infty} h_{p} r_{yx}(p) \\
J_{min} &= r_{xx}(0) - \underline{h} \cdot \underline{r_{yx}}
\end{align*}
$$ 

## $$ \color{blue}{ J_{min} = r_{xx}(0) - \underline{h} \cdot \underline{r_{yx}} } $$


# Matched Filter
**Matched filter** shows how to extract a known deterministic signal from random noise.

## $$ \color{blue}{ \underbrace{\underline{h_{\text{opt}}}}_{\scriptsize \text{Coefficients of Matched Filter}} = \dfrac{\underline{\tilde{x}}}{|\underline{\tilde{x}}|} } \qquad \small ( \text{where }\underline{\tilde{x}}\text{ is } \underline{x} \text{ time-reversed })$$

#### Instead of minimising the MSE like for Wiener, here we try to maximise the SNR:

## $$ \color{blue}{
\text{SNR}_{\text{opt}} = \dfrac{ \underline{\tilde{x}} \cdot \underline{\tilde{x}} } {\sigma_{v}^{2}} = \dfrac{ |\underline{\tilde{x}}|^{2} } {\sigma_{v}^{2}} 
} $$

