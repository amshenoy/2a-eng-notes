# Noise Filtering

## Correlation Function

### Auto-Correlation
$$ r_{XX}[k] = r_{XX}[-k] $$

### Cross-Correlation
$$ \color{blue}{ r_{XY}[k] = E(X_{n} Y_{n+k}) = E(Y_{n+k} X_{n}) = r_{YX}[-k] } $$

## Covariance Function

### Auto-Covariance
$$ \color{blue}{ c_{XX}[k] = E((X_{n}-\mu)(X_{n+k}-\mu)) } \qquad \text{where } \mu = E(X_{n}) $$

### Cross-Covariance

$$ \color{blue}{ c_{XY}[k] = E((X_{n}-\mu_{X})(Y_{n+k}-\mu_{Y})) }  $$

## White Noise
A process $ X_{n} $ is a **white noise process** if:
$$ \color{red}{ c_{XX}[k] = \sigma_{X}^{2} \enspace \delta(k) } $$

$$ \color{red}{ r_{XX}[k] = E(X^{2}) \enspace \delta(k) } $$

$$ \color{red}{ S_{X}(\omega) = E(X^{2}) = \text{ Constant } } $$

#### Note: This is unrealisable in practice since constant power density means infinite average power. However this is a good approximation for "nearly white" noise processes.

#### Note: &emsp; $ \color{lightgray}{ \text{ White } } S_{X}(\omega) \propto 1 \qquad \color{violet}{ \text{ Pink } } S_{X}(\omega) \propto \dfrac{1}{\omega} \qquad \color{brown}{ \text{ Brown } } S_{X}(\omega) \propto \dfrac{1}{\omega^{2}} $


</br>

## Mean Ergodic
A process $ X_{n} $ is mean ergodic if:
### $$ \color{red}{ \lim_{k \rightarrow \infty} c_{XX}[k] = 0 } $$


</br><hr>


# Example System

### Given some observed output $ \color{teal}{ x_{n} } $, we assume some latent input $ \color{brown}{ d_{n} } $ and noise $ \color{gray}{ v_{n} } $:
$$ \Large \color{teal}{ x_{n} } = \color{brown}{ d_{n} } + \color{gray}{ v_{n} } $$

### General Properties

$$ \Large \color{blue}{ r_{xx}[k] = \underbrace{ r_{xd}[k] }_{r_{dd}[k] + r_{vd}[k]} + \underbrace{ r_{xv}[k] }_{r_{dv}[k] + r_{vv}[k]} } $$

</br>

#### If input and noise are uncorrelated $ \color{blue}{ r_{vd}[k] = E( V_{n} D_{n+k} ) = 0 } $
$ \large \color{green}{ \therefore r_{xd}[k] = r_{dd}[k] \qquad r_{xv}[k] = r_{vv}[k]  } $

$ \large \color{blue}{ r_{xx}[k] = r_{dd}[k] + r_{vv}[k] } $

</br>

### WSS Noise
**Zero Mean** &emsp; $ E(V_{i}V_{j}) = E(V_{i}) E(V_{j}) = 0 \text{ for } i \ne j $

 &emsp; $ \color{blue}{ r_{vv}[k] = E(V_{n}V_{n+k})  = \begin{cases} E(V_{n}^{2}) \qquad k=0 \\ 0 \qquad \qquad k \ne 0 \end{cases} \Bigg\} = E(V_{n}^{2}) \delta(k) = \color{green}{ ( \mu_{v}^{2} + \sigma_{v}^{2} ) \ \delta(k) } }  $

</br>

#### Note: In the general case, $ r_{dd}[k] = E(D_{n} D_{n+k}) = \begin{cases} E(D_{n}^{2}) \qquad \qquad \qquad k=0 \\ E(D_{n}) \ E(D_{n+k}) \qquad k \ne 0 \end{cases} \Bigg\} = \color{green}{ \mu_{d}^{2} + \sigma_{d}^{2} \ \delta(k) } $.

</br><hr>


# Wiener Filter
> **Wiener filter** shows how to extract a **random signal from random noise**.

**Wiener filter** is only the **optimal linear estimator** for **stationary signals**. The Kalman filter offers an extension for non-stationary signals via state space models. In cases where a linear filter is still not good enough, non-linear filtering techniques can be adopted.

## Estimation
We can remove the noise $ \color{gray}{ v_{n} } $ from the output signal $ \color{teal}{ x_{n} } $ by applying the filter $ \color{orange}{ h_{n} } $ to get an estimation of the latent input signal $ \color{brown}{ \hat{d_{n}} } $:
$$ \Large \color{brown}{ \hat{d_{n}} } = \color{orange}{ h_{n} } * \color{teal}{x_{n}} = \sum_{p=0}^{\infty} \color{orange}{h_{p}} \ \color{teal}{x_{n-p}} $$

</br>

## Wiener-Hopf Equations

If we are trying to estimate $ \color{purple}{ \hat{d_{n}} = h_{n} * x_{n} } $ (ie. $ x_{n} = f(d_{n}) $ ), then from the Wiener-Hopf equations, we can derive the filter:


$$ \Large \color{purple}{ r_{xd}[q] =\sum_{p=-\infty}^{\infty} h_{p} r_{xx}[q-p]  
\\ \underline{r_{xd}} = R_{XX} \underline{h} 
}
$$
 
## $$ \color{blue}{ \underbrace{\underline{h}}_{\scriptsize \text{Coefficients of Wiener Filter}} = R_{XX}^{-1} \enspace \underline{r_{xd}} } $$

### $ R_{XX} $ is a symmetric matrix from the vector $ \underline{r_{xx}} $

$ \color{red}{ \text{Note: Always derive the Wiener-Hopf equations using the least MSE criterion unless a convolution is given.} } $

</br>

## Mean-Squared Error (MSE)

### $$ \color{green}{ J = E( (\epsilon_{n})^{2} ) = E( (d_{n} - \hat{d}_{n})^{2} ) } $$

### Least MSE Criterion

Use this to **derive the Wiener-Hopf equations** for a given problem:

$$ \color{blue}{
\Large \dfrac{\partial}{\partial h_{i}} E(\epsilon_{n}^{2}) = E(2 \epsilon_{n} \dfrac{\partial \epsilon_{n}}{\partial h_{i}} ) = 0
}
$$

#### 
$$ \large
\begin{align*}
E(\epsilon_{n} x_{n-p}) &= 0 \quad \small (\text{ "Orthognality Principle" }) \\
E((d_{n} - \hat{d}_{n}) x_{n-q}) = E((d_{n} - \sum_{p=0}^{\infty} h_{p} x_{n-p} ) x_{n-q}) &= 0 \\
E(d_{n}x_{n-q}) - \sum_{p=0}^{\infty} h_{p} E( x_{n-p} x_{n-q} ) &= 0 \\
\end{align*}
$$ 

Wiener-Hopf Equations Derived:

$ \large
\therefore E(d_{n}x_{n-q}) = \sum_{p=0}^{\infty} h_{p} E( x_{n-p} x_{n-q} )
$

</br>

### Minimum Error
### $ 
\begin{align*}
J_{min} &= E(\epsilon_{n}^{2}) = E(\epsilon_{n} \big( d_{n} - \sum_{p} h_{p} x_{n-p} \big) ) \\ 
&= E(\epsilon_{n} d_{n}) - \sum_{p=0}^{\infty} h_{p} \underbrace{ E(\epsilon_{n} x_{n-p}) }_{0 \text{ by orthognality principle} } \\
&= E(\epsilon_{n} d_{n}) \\ \\ 
&= E((d_{n} - \hat{d}_{n}) d_{n} ) = E(d_{n}^{2}) - E(\hat{d}_{n} d_{n}) \\ \\
&= E(d_{n}^{2}) - E(d_{n} (\sum_{p=0}^{\infty} h_{p} x_{n-p})) = E(d_{n}^{2}) - \sum_{p=0}^{\infty} h_{p} E(x_{n-p} d_{n}) \\
J_{min} &= r_{dd}(0) - \sum_{p=0}^{\infty} h_{p} r_{xd}(p) \\
J_{min} &= r_{dd}(0) - \underline{h} \cdot \underline{r_{xd}}
\end{align*}
$

## $$ \color{blue}{ J_{min} = r_{dd}(0) - \underline{h} \cdot \underline{r_{xd}} } $$

#### Power of the error signal can be found by performing the DTFT of $ J_{min} $ then integrating across the frequency $ [\pi, -\pi] $ multiplied by $ \dfrac{1}{2\pi} $. (See Stochastic Processes)

</br>

## Wiener Gain

Taking the **DTFT of the Wiener-Hopf** equations:

$$ \Large \color{purple}{ H(e^{j \theta}) = \dfrac{S_{xd}(e^{j \theta})}{S_{xx}(e^{j \theta})} } $$

If noise and input are uncorrelated then $ S_{xd} = S_{dd} $ and $ S_{xx} = S_{dd} + S_{vv} $:

$ H(e^{j \theta}) = \dfrac{S_{dd}}{S_{dd} + S_{vv}} = \dfrac{1}{1+ \dfrac{1}{\text{SNR}} }$

</br><hr>

# Matched Filter
**Matched filter** shows how to extract a **known deterministic signal $ \mathbf{\tilde{s}} $ from random noise**.

## $$ \color{blue}{ \underbrace{\underline{h_{\text{opt}}}}_{\scriptsize \text{Coefficients of Matched Filter}} = \dfrac{\underline{\tilde{x}}}{|\underline{\tilde{x}}|} } \qquad \small ( \text{where }\underline{\tilde{x}}\text{ is } \underline{x} \text{ time-reversed })$$

$$ \text{SNR} = \dfrac{E(|\mathbf{h} \mathbf{\tilde{s}}|^{2})}{E(|\mathbf{h} \mathbf{\tilde{v}}|^{2})} = \dfrac{|\mathbf{h} \mathbf{\tilde{s}}|^{2}}{\sigma_{v}^{2} \mathbf{h}_{T} \mathbf{h} } $$

#### Instead of minimising the MSE like for Wiener, here we try to maximise the SNR:

## $$ \color{blue}{
\text{SNR}_{\text{opt}} = \dfrac{ \underline{\tilde{x}} \cdot \underline{\tilde{x}} } {\sigma_{v}^{2}} = \dfrac{ |\underline{\tilde{x}}|^{2} } {\sigma_{v}^{2}} 
} $$

</br><hr>


# Orthognal Signals

Consider $ \large x_{n} = s_{1,n} + s_{2, n} + v_{n} $ where $ s_{1, n} $ and $ s_{2, n} $ are orthognal to each other:

Since the two signals are orthognal, both signals can be extracted by applying their respective filters $ h_{1} $ and $ h_{2} $.

$ \large \hat{s_{1,n}} = h_{1} * x_{n} $

$ \large \hat{s_{2,n}} = h_{2} * x_{n} $




 
