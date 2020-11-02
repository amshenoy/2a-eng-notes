# Noise Processes

## Auto-Correlation Function

### $$ \color{blue}{ r_{XY}[k] = E(X_{n} Y_{n+k}) = E(Y_{n+k} X_{n}) = r_{YX}[-k] } $$

#### Similary auto-correlation function as from stochastic processes: $ r_{XX}[k] = r_{XX}[-k] $

## Cross-Correlation Function

### $$ \color{blue}{ c_{XX}[k] = E((X_{n}-\mu)(X_{n+k}-\mu)) } \qquad \text{where } \mu = E(X_{n})  $$

### White Noise
A process $ X_{n} $ is a **white noise process** if:
### $$ \color{red}{ c_{XX}[k] = \sigma_{X}^{2} \enspace \delta(k) } $$

### Mean Ergodic
A process $ X_{n} $ is mean ergodic if:
### $$ \color{red}{ \lim_{k \rightarrow \infty} c_{XX}[k] = 0 } $$


# Wiener Filter

**Wiener filter** is only the **optimal linear estimator** for **stationary signals**. The Kalman filter offers an extension for non-stationary signals via state space models. In cases where a linear filter is still not good enough, non-linear filtering techniques can be adopted.

## $$ \color{blue}{ \underbrace{\underline{h}}_{\scriptsize \text{Coefficients of Wiener Filter}} = R_{XX}^{-1} \enspace \underline{r_{yx}} } $$

### $ R_{XX} $ is a symmetric matrix from the vector $ \underline{r_{xx}} $

</br>

### For input $ x_{n} $, noise $ v_{n} $ and output $ y_{n} $:

#### Input and noise are uncorrelated &emsp; $ \color{blue}{ r_{vx}[k] = 0 } $
#### Noise is WSS &emsp; $ \color{blue}{ r_{vv}[k] = E(V_{n}V_{n+k}) = E(V_{n}^{2}) \delta(k) } \qquad \text{As } E(V_{i}V_{j}) = 0 \text{ for } i \ne j $

</br>

## Mean-Squared Error (MSE)

### Minimum Error



