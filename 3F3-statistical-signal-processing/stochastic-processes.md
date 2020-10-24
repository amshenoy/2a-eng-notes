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

</br>

## Markov Property
**"Limited Memory"** / Markov property:
#### Only the most recent state $ i_{n-1} $ is needed to determine the probability of the next state $ i_{n} $.

#### $ P(X_{n} = x_{n}| X_{n-1} = x_{n-1}, ..., X_{0} = x_{0}) = P(X_{n} = x_{n} | X_{n-1} = x_{n-1}) = Q_{x_{n-1} x_{n}} $

More briefly written as:
### $ \color{blue}{ p(x_{n}| x_{n-1}, ..., x_{0}) = p(x_{n}|x_{n-1}) = Q_{x_{n-1} x_{n}} } $

</br>

## Strict Stationarity
A discrete time random process (**Markov** or not) is **strictly stationary** if:
### $ f_{X_{0}, ... X_{k}}(x_{0}, ..., x_{k}) = f_{X_{m}, ... X_{m+k}}(x_{m}, ..., x_{m+k}) $ &emsp; for all k and m > 0

#### Note*: Markov Chains are strictly stationary

</br>

## Invariant (/Stationary) Distribution
The p.m.f $ \pi = (\pi_{i}: i \in S) $ is invariant for $Q$ if for all $ j \in S $:

$$ \sum_{i \in S } \pi_{i} Q_{ij} = \pi_{j} $$  
## $$ \color{blue}{ \pi Q = \pi } \quad (\pi \text{ is regarded as a row vector}) $$

</br><hr>

# Autoregressive (AR) Process

</br>

## Wide Sense Stationary (WSS)

#### 1) Constant Mean: $ E\{ X_{n} \} = \mu \quad \text{ for all n } $
#### 2) Finite Variance: $ E\{ X_{n}^{2} \} < \infty \quad \text{ for all n } $
#### 3) Stationarity Property: $ \color{green}{ E \{ X_{m} X_{n}  \} = E \{ X_{m+k} X_{n+k}  \} } $ 
</br>

**Note: WSS is a weaker restriction of strict stationarity as strict stationarity is an inappropriate model for real-world processes.**

## Correlation Function
### $$ \color{blue}{ R_{X}(k) = E \{ X_{0} X_{k} \} } $$

$ E \{ X_{m} X_{n}  \} = E \{ X_{0} X_{n-m}  \} = R_{X}(n-m) $ 
 
</br><hr>

# Moving Average (MA) Process


</br><hr>

## Power Spectrum


