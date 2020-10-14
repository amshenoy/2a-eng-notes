# Digital Filters

## Stability
Bounded Input gives Bounded Output (BIBO)
</br>

$ G(z) $ is stable means:
* $ |p_{i}| < 1 $ (All poles within unit circle)
* $ \sum_{k=0}^{\infty} |g_{k}| $ is finite (Bounded Impulse Response)

$ \text{Divergence Rate} \propto | p_{i} | \quad \text{Distance of Poles from Origin} $

</br>

## FIR/IIR, Causality

### Finite Impulse Response
Pulse response terminates after a finite number of steps.

$$ g_{k} = \{g_{0}, g_{1}, ..., g_{n}, 0, 0, ..., 0\} $$
$$ G(z) = g_{0}+g_{1}z^{-1}+...+g_{n}z^{-n} $$
This means that **all poles of an FIR filter must be at 0**.
 
### IIR (Infinite Impulse Response)

IIR filters have an infinite pulse response and can have **arbitrary pole locations**.

IIR filters have feedback ( ie. the output is used in the filter).


### Causal System

A system is causal if the system $ G(z) $ is **not top-heavy**.

If a system is causal, $ G(z) $ is finite (equals $ g_{0} $) as $ z \rightarrow \infty $ and is **zero for negative time**.

</br>

## Linear Filter

$$ \textbf{A stable filter "forgets" the initial conditions} $$

Any linear filter can be written as:
$$ A(z) Y(z) = B(z) U(z) + C(z, y_{i}) $$

$ C(z, y_{i}) $ takes into account the initial conditions of the filter. $ U(z) $ is the input and $ Y(z) $ is the output.

</br>

## Ideal Filter

(TBD)

</br>

These cannot be implemented as they have a non-causal impulse response.

### Inverse Fourier Transform

(TBD)



</br>

## Filter Design

### Filter Specs

Passband Ripple - $ 1+\delta p $ - Peak

Peak-to-peak Passband Ripple - $ 1 + 2 \delta p $ - Start to Peak 

Minimum Stopband Attenuation - $ \dfrac{1}{\delta s} $ - Attenuation of stopband level ($ \delta s $)

### Design Methods

(TBD)


</br>

## FIR vs IIR Filters

**FIR**
+ Simple, fast, stable, feedforward implementation (FFT)
+ Linear Design Methods (Easy, efficient)

- Higher filter order than IIR required (for same performance)
- Often greater delay than an equal performance IIR

**IIR**
+ Lower filter order
+ Shorter Delay

- Design Methods: i) Direct optimisation of transfer function, ii) digital implementation of analog filters.
- Can be unstable, use feedback


