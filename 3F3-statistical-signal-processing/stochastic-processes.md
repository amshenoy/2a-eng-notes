# Stochastic Processes

### Discrete Time Random Process
Infinite collection of random variables

**Joint PDF** &emsp; $ f(x_{0}, ..., x_{n}) $

### Discrete Random Variables
**Joint PMF** &emsp; $ p(x_{0}, ..., x_{n}) $

</br><hr>

# Markov Chains
$ \pi $ or $ \lambda $ is the initial distribution

$ Q $ is the transition probability matrix

$ (\pi, Q) $ completely defines a Markov Chain

### $$ \color{blue}{ P_{X_{n}}(x_{n}) = (\pi Q^{n})_{x_{n}} } $$

### $$ \color{blue}{ P(x_{n}, ..., x_{n+k}) \overbrace{=}^{\text{Chain Rule}} \prod_{i=m}^{m+k} P(x_{i}|x_{i-1}, ..., x_{1}) \overbrace{=}^{\text{Markov Property}} \pi_{i_{m}} \prod_{i=m}^{m+k-1} Q_{i, i+1} \overbrace{=}^{\text{Invariant Dist.}} \prod_{i=m}^{m+k} \pi_{i} } $$

**Irreducible** - All states communicate with each other (No sink cycles/nodes)

**Ergodic** - All **irreducible** and **aperiodic** Markov chains have a unique **stationary (/invariant) distribution** $ \pi $.

</br>

## Markov Property
**"Limited Memory"** / Markov property:
#### The next state $ x_{n} $ depends only on the previous state $ x_{n-1} $.

#### $ P(X_{n} = x_{n}| X_{n-1} = x_{n-1}, ..., X_{0} = x_{0}) = P(X_{n} = x_{n} | X_{n-1} = x_{n-1}) = Q_{x_{n-1} x_{n}} $

More briefly written as:
### $ \color{blue}{ p(x_{n}| x_{n-1}, ..., x_{0}) = p(x_{n}|x_{n-1}) = Q_{x_{n-1} x_{n}} } $

</br>

## Strict Stationarity
A discrete time random process (**Markov** or not) is **strictly stationary** if:
### $ \color{blue}{ f_{X_{0}, ... X_{k}}(x_{0}, ..., x_{k}) = f_{X_{m}, ... X_{m+k}}(x_{m}, ..., x_{m+k}) } $ &emsp; for all k and m > 0

#### Note*: Markov Chains are strictly stationary

</br>

## Stationary (/Invariant) Distribution
The p.m.f $ \pi = (\pi_{i}: i \in S) $ is invariant for $Q$ if for all $ j \in S $:

$$ \sum_{i \in S } \pi_{i} Q_{ij} = \pi_{j} $$  
## $$ \color{blue}{ \pi Q = \pi } \quad (\pi \text{ is regarded as a row vector}) $$

</br><hr></br>

# WSS Processes

## Wide Sense Stationary (WSS)

### 1) Constant Mean: $ E\{ X_{n} \} = \mu \quad \text{ for all n } $
### 2) Finite Variance: $ E\{ X_{n}^{2} \} < \infty \quad \text{ for all n } $
### 3) Stationarity Property: $ \color{green}{ E \{ X_{m} X_{n}  \} = E \{ X_{m+k} X_{n+k}  \} = R_{X}(n-m) } $
</br>

**Note: WSS is a weaker restriction of strict stationarity as strict stationarity is an inappropriate model for real-world processes.**

## Correlation Function
## $$ \color{blue}{ 
\begin{align*}
R_{X}(k) &= E \{ X_{0} X_{k} \} \\ (&= E \{ X_{n} X_{n+k} \}) \quad (\small\text{By stationarity})
\end{align*}
}
$$

### For a WSS process, $ R_{X}(k) $ is only dependent on $ k $ (ie. the difference of the indices).

### $ R_{X}(k) $ is an even function (ie. $ R_{X}(k) = R_{X}(-k) $ )

## LTI System

### For any LTI system with WSS input $ W_{n} $ and impulse response $ h_{n} $, then the output $ X_{n} $ is WSS where:
### $$ X_{n} = \sum_{k=-\infty}^{\infty} W_{n-k} h_{k} = W_{n} * h_{n} $$

</br></br>

## Autoregressive (AR) Process

### $$ \color{purple}{AR}(p): \qquad \color{blue}{  X_{n} = \Big( \sum_{i=1}^{p} a_{i} \color{purple}{X_{n-i}} \Big) + W_{n} } $$

### where $ \quad \color{green}{ E\{W_{i}\} = 0 \quad E\{ W_{i} W_{j} \} = \begin{cases}
\sigma^{2} \qquad i = j \\
0 \quad i \ne j
\end{cases}
\quad \text{(Required for WSS)} }
$

## $$ 
\begin{align*}
AR(1): \qquad
\color{blue}{ X_{n} } &= \color{blue}{ a X_{n-1} + W_{n} } \\
&= a (a X_{n-2} + W_{n-1}) + W_{n} \quad (\small\text{By resubstitution})  \\
&= \quad ... \\
\color{blue}{ X_{n} } &= \color{blue}{ \sum_{k=0}^{\infty} W_{n-k} a^{k} } \\
&= W_{k} * \underbrace{a^{k}}_{h_{k}} \quad (\small\text{ where the impulse response is } h_{k} = a^{k}  ) \\
\end{align*}
$$


### $ R_{X}(k) = a^{2} \sigma_{x}^{2} = a^{2} \dfrac{\sigma^{2}}{1-a^{2}} $

</br>

## Moving Average (MA) Process

 
### $$ \color{purple}{MA}(q): \qquad \color{blue}{  X_{n} = \Big( \sum_{i=1}^{q} b_{i} \color{purple}{W_{n-i}} \Big) + W_{n} } $$

### where $ \quad \color{green}{ E\{W_{i}\} = 0 \quad E\{ W_{i} W_{j} \} = \begin{cases}
\sigma^{2} \qquad i = j \\
0 \quad i \ne j
\end{cases}
\quad \text{(Required for WSS)} }
$

</br>

## Autoregressive Moving Average (ARMA) Process

 
### $$ \color{purple}{ARMA}(p, q): \qquad \color{blue}{  X_{n} = \Big( \sum_{i=1}^{p} a_{i} \color{purple}{X_{n-i}} \Big) + \Big( \sum_{i=1}^{q} b_{i} \color{purple}{W_{n-i}} \Big) + W_{n} } $$

### where $ \quad \color{green}{ E\{W_{i}\} = 0 \quad E\{ W_{i} W_{j} \} = \begin{cases}
\sigma^{2} \qquad i = j \\
0 \quad i \ne j
\end{cases}
\quad \text{(Required for WSS)} }
$

</br><hr>

# Power Spectrum Density (PSD)

Power Spectrum Density = Fourier transform of the correlation function

### $ S_{X}(f) $ is even, real and non-negative &emsp; $ S_{X}(f) = S_{X}(-f) = S^{*}_{X}(f) \enspace \ge 0 $

### $ S_{X}(f) $ is continuous if $ \sum_{-\infty}^{\infty} |R_{X}(k)| < \infty $
 
### $ S_{X}(f) = S_{X}(f+k) \quad S_{X}$ has period 1.

</br>

#### Note: Split $ \sum_{k=-\infty}^{\infty} $ into $ \sum_{k=0}^{\infty} $ and $ \sum_{k=-\infty}^{0} $

#### Note: $ R_{X}(k) = R_{X}(-k) $ (even function)

#### Note: For proving conjugates, use change of variable $ k = - k^{'} $ in sum before doing anything else!

</br>

## Fourier Transform

### $$ 
\begin{align*}
S_{X}(f) &= \mathcal{F}\{ R_{X}(k) \} = \sum_{k=-\infty}^{\infty} R_{X}(k) e^{-j 2\pi f k} = \sum_{k=-\infty}^{\infty} R_{X}(k) \cos(2 \pi f k) \\ & (\text{As } R_{x}(k) \text{ is even, sines are removed}) \\ \\ &= \Bigg( \sum_{k=0}^{\infty} R_{X}(k) e^{-j 2\pi f k} + R_{X}(-k) e^{j 2\pi f k} \Bigg) \enspace - R_{X}(0) \\
&= 2 \sum_{k=0}^{\infty} R_{X}(k) \cos(2 \pi f k) \enspace - R_{X}(0) \\
\end{align*}
$$

Alternatively can be written in the z-domain as:
### $$ S_{X}(e^{j \omega}) = \mathcal{Z}\{ R_{X}(k) \}|_{z=e^{j \omega}}  $$


</br>

## Inverse Fourier Transform

### $$ R_{X}(k) = \int_{-\frac{1}{2}}^{\frac{1}{2}} \enspace S_{X}(f) \enspace e^{j 2\pi f k } \enspace df $$

</br>

## LTI System
### $$ X_{n} = W_{k} * h_{k} $$

### $$ S_{X}(f) = S_{W}(f) \enspace |H(f)|^{2} = S_{W}(f) \enspace H(f) H^{*}(f) $$



