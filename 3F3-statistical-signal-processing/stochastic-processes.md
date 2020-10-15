# Stochastic Processes

### Discrete Time Random Process
Infinite collection of random variables

**Joint PDF** &emsp; $ f(x_{0}, ..., x_{n}) $

### Discrete Random Variables
**Joint PMF** &emsp; $ p(x_{0}, ..., x_{n}) $

</br>

## Markov Chains
$ \pi $ or $ \lambda $ is the initial distribution

$ Q $ is the transition probability matrix

$ (\pi, Q) $ completely defines a Markov Chain

</br>

### Markov Property
**"Limited Memory"** / Markov property:
#### Only the most recent state $ i_{n-1} $ is needed to determine the probability of the next state $ i_{n} $.

For any positive integer $ n $ and possible states $ i_{0}, ..., i_{n} $ of the random variables,
#### $ P(X_{n} = i_{n}| X_{0} = i_{0}, ..., X_{n-1} = i_{n-1}) = P(X_{n} = i_{n} | X_{n-1} = i_{n-1}) = Q_{i_{n-1} i_{n}} $

More briefly written as:
### $ \color{blue}{ p(i_{n}|i_{0}, ..., i_{n-1}) = p(i_{n}|i_{n-1}) = Q_{i_{n-1} i_{n}} } $

</br>

### Strict Stationarity
A discrete time random process (**Markov** or not) is **strictly stationary** if:
### $ f_{X_{0}, ... X_{k}}(x_{0}, ..., x_{k}) = f_{X_{m}, ... X_{m+k}}(x_{m}, ..., x_{m+k}) $ &emsp; for all k and m > 0

</br>

### Invariant (/Stationary) Distribution



