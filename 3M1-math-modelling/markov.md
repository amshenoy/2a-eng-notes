# Markov Chains

## Discrete (Finite) State-Space



## Continuous State-Space

$$ Q = R - E $$
R is the transition rate matrix.
E is the exit rate for each node and hence a diagonal matrix.
Q is the transition generator matrix where rows sum to 0.

The transition function can be expressed as a matrix exponential function:
$$ P(t) = e^{Q t}$$


### Compartmental Model
$$ X_{i} \text{ is the population of each compartment } i $$
$$ \dfrac{dX_{0}}{dt} = - X_{0} * \text{rate} * \text{probability} $$  
$$ \dfrac{dX_{1}}{dt} = + X_{0} * \text{rate} * \text{probability} - X_{1} * \text{rate} * \text{probability} $$  

## Stochastic Processes



## Sampling
