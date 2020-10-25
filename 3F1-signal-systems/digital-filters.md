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

</br><hr>

# FIR Filter Design

## Linear Filter

$$ \textbf{A stable filter "forgets" the initial conditions} $$

Any linear filter can be written as:
$$ A(z) Y(z) = B(z) U(z) + C(z, y_{i}) $$

$ C(z, y_{i}) $ takes into account the initial conditions of the filter. $ U(z) $ is the input and $ Y(z) $ is the output.

</br>

## Ideal Filter

$$
\text{ Analog } \cos(\omega t) \qquad  \text{ Digital } \cos(k \theta)
\\
H_{a}(j \omega) = \begin{cases}
               1 \qquad |\omega| \le \omega_{c} \\
               0 \qquad |\omega| \gt \omega_{c}
            \end{cases}
\qquad 
\color{blue}{
H_{d}(e ^ {j \theta}) = \begin{cases}
               1 \qquad |\theta| \le \theta_{c} \\
               0 \qquad |\theta| \gt \theta_{c}
            \end{cases}
}
$$

These cannot be implemented in real life as they have a non-causal impulse response.

### $ \color{red} { \text{Frequency Response of Digital Filter: } G(e^{j \theta}) } $

Write $ G(e^{j \theta}) $ as a delay term and a frequency-dependent gain term (for easier handling):
###  $ \color{blue}{ G(e^{j \theta}) = e^{-j N\theta} f(\theta) }$

### Sketch $ \color{blue}{ | G(e^{j \theta}) |  \quad 0 \le \theta \le \pi } $  for labelling as lowpass, bandpass, highpass or allpass. 


</br>



## Inverse Fourier Transform

To convert the filter from the z-domain to the k-domain, we can use the inverse fourier transform:

### $$ 
\text{ Analog } \qquad h_{a}(t) = \dfrac{1}{2\pi} \int^{\infty}_{-\infty} H_{a}(j \omega) e^{j \omega t} d\omega
\\
\color{blue}{ \text{ Digital } \qquad h_{d}(k) = \dfrac{1}{2\pi} \int^{\pi}_{-\pi} H_{d}(e^{j \theta}) e^{j \theta k} d\theta }
$$

</br>

## Filter Specs

Passband Ripple - $ 1+\delta p $ - Peak

Peak-to-peak Passband Ripple - $ 1 + 2 \delta p $ - Start to Peak 

Minimum Stopband Attenuation - $ \dfrac{1}{\delta s} $ - Attenuation of stopband level ($ \delta s $)

## Window Design Method

### $$ \color{blue}{ \underbrace{g_{k}}_{\text{Filter}} = \underbrace{h_{k}}_{\text{Ideal/Desired} \\ \text{ Impulse Response}} \underbrace{w_{k}}_{\text{Window function}} } $$

$ G = H * W $ 

Using **duality** of multiplication / **convolution**:

### $$ \color{blue}{ G(e^{j \omega}) = \dfrac{1}{2 \pi} \int^{\pi}_{-\pi} H(e^{j \theta}) W(e^{j (\omega - \theta)}) d\theta } $$

### Full Steps:
1) Select window function $ w_{k} $
2) Select ideal frequency response $ H(e^{j \theta}) $
3) Compute coefficients of $ h_{k} $
4) $ g_{k} = h_{k} w_{k} $ 
5) Evaluate and iterate if necessary

Note*: Truncation = Multiplication by Window, Abrupt discontinuities in window filter leads to side-lobe interference

</br>

### Linear Phase
Linear Phase $ G(e^{j \theta}) = |G(e^{j \theta})| e^{-j \theta \dfrac{N}{2}} $ is achieved if $ g_{k} = g_{N-k} $

All window functions satisfy linear phase $ w_{k} = w_{N-k} $.
If the impulse response $ h_{k} $ is also symmetric ie. $ h_{k} = h_{N-k} $, then $ g_{k} = g_{N-k} $.

</br>

## Composite Filters

### Example:
**Ideal Bandpass Filter**
$$
\begin{align*}
H(e^{j \theta}) &= \begin{cases}
               1 \qquad \theta_{1} \le \theta \le \theta_{2}\\
               0 \qquad \text{Otherwise}
            \end{cases}
\\
&= \text{Lowpass}_{[0, \theta_{2}]} - \text{Lowpass}_{[0, \theta_{1}]}
\end{align*}
\\ 
\text{ where } \text{ Lowpass}_{[0, \theta_{c}]}(e^{j \theta}) = \begin{cases}
 1 \qquad 0 \le \theta \le \theta_{c}\\
 0 \qquad \text{Otherwise}
\end{cases} 
$$

### $$
\begin{align*}
h_{k} &= \mathcal{F}^{-1}(H)
\\ &= \mathcal{F}^{-1}(\text{Lowpass}_{[0, \theta_{2}]}) - \mathcal{F}^{-1}(\text{Lowpass}_{[0, \theta_{1}]}) 
\\ &= \dfrac{sin(k\theta_{2})}{\pi k} - \dfrac{sin(k\theta_{1})}{\pi k} 
\end{align*}
$$

**Final Filter $ g_{k} $**

With window function and shift as required.
### $$ g^{*}_{k} = h_{k} w_{k}
\\ g_{k} = g^{*}_{k-N} $$


</br><hr>

## FIR vs IIR Filters

**FIR**
+ Simple, fast, stable, feedforward implementation (FFT)
+ Linear Design Methods (Easy, efficient)
+ Can have exactly linear phase ie. $ G(e^{j \theta}) = |G(e^{j \theta})| e^{-j \theta} $

- Higher filter order than IIR required (for same performance)
- Often greater delay than an equal performance IIR

**IIR**
+ Lower filter order
+ Shorter Delay

- Design Methods: i) Direct optimisation of transfer function, ii) digital implementation of analog filters.
- Can be unstable, use feedback

</br><hr>

# IIR Filter Design

## Discretisation
Given an analogue filter $ G_{A}(s) $ (s-domain), we can convert it to a digital filter $ G_{D}(z) $ (z-domain) by discretisation.

There are two methods of discretisation:
**1) Algebraic Transformation**
**2) Response Matching**

</br>

### 1) Algebraic Transformation

### $$ s = \Psi(z) $$

### $$ \color{blue}{ G_{D}(z) = G_{A}(\Psi(z)) } $$

#### Frequency Warping
Therefore the **frequency response** of the **digital filter** $ G_{D}(e^{j \theta}) $ is:
### $$ G_{D}(e^{j \theta}) = G_{A}(\Psi(e^{j \theta})) = G_{A}(j \omega) $$
### $$ \color{blue}{ \therefore j\omega = \Psi(e^{j \theta}) } $$

Note that **$\omega$ is the analogue frequency** and **$\theta$ is the digital frequency**. Therefore we can now convert between analogue and digital frequencies depending on the transformation.


</br>

**Notable Transforms**

**Forward Difference**: $\Psi(z) = \dfrac{z-1}{T}$ &emsp; LHS ($ s < 0 $) of s-plane maps to $ z < 1 $ &emsp; (**Possibly Unstable**)

**Backward Difference**: $\Psi(z) = \dfrac{z-1}{zT}$ &emsp; LHS ($ s < 0 $) of s-plane maps to circle $ r=1/2 $ at $ (1/2, 0) $ &emsp; (**Stable**)

**Tustin / Bilinear Transform**: $\Psi(z) = \dfrac{2}{T} \dfrac{z-1}{z+1}$ (or simply $\dfrac{z-1}{z+1}$ ) &emsp; LHS ($ s < 0 $) of s-plane maps to **unit circle** &emsp; (**Stable**)

For the **bilinear transform**, $ j \omega = \dfrac{2}{T} tan \dfrac{\theta}{2} $ or simply $ \color{blue}{ j \omega = tan \dfrac{\theta}{2} } $

</br>

### 2) Response Matching

Given an analogue filter $ G_{a}(s) $, we need to find the digital filter $ G(z) $ for which the response is invariant for some function $ U(s) $ and for some function $ U(z) $ (ie. the discrete time response is the same):

### $$ \color{blue}{\mathcal{Z}^{-1} \{ G(z) U(z) \} = \mathcal{L}^{-1} \{ G(s) U(s) \}|_{t=kT}} $$

### $ \color{blue}{ \text{Rearrange to solve for } G(z)  \text{ given a } G(s) }$


</br>


## Band Transformations

Assuming a **lowpass prototype with a cutoff of $\omega=1$**:

### Lowpass to Lowpass:
### $ F(s) = \dfrac{s}{\omega_{c}} $

### Lowpass to Highpass:
### $ F(s) = \dfrac{\omega_{c}}{s} $

### Lowpass to Bandpass:
### $ F(s) = \dfrac{s^{2}+\omega_{1}\omega_{2}}{s(\omega_{2} - \omega_{1})} $

### Lowpass to Bandstop:
### $ F(s) = \dfrac{s(\omega_{2} - \omega_{1})}{s^{2}+\omega_{1}\omega_{2}}$
 
**Note: $ \color{blue}{ \text{Highpass is the reciprocal of lowpass. Bandstop is the reciprocal of bandpass.} } $**
 
</br>

## Design Method

#### Given the sampling frequency $\color{orange}{f_{s}} $, the type of filter $\color{orange}{F}$ to be designed with the corresponding 3dB (ie. cutoff) frequency/frequencies $\color{orange}{ f_{i} }$, the prototype analogue low pass filter $\color{orange}{ H(s) }$ with 3dB (ie. cutoff) frequency $ \color{orange}{ \omega_{H} = 1 rad s^{-1}} $ and the discretisation transformation $ \color{orange}{ \Psi(z) } $:

1) Find **digital frequencies** $ \theta_{i} $ by converting required frequencies $ f_{i} $:
### $$ \color{blue}{ \theta_{i} }= \dfrac{f_{i}}{f_{s}} \cdot 2 \pi $$

2) Find **analogue frequencies** $ \omega_{i} $ by normalising digital frequencies $ \theta_{i} $ depending on the discretisation transformation $ \Psi(z) $:
### $$ j \color{blue}{ \omega_{i} } = \Psi(e^{j \theta_{i}}) $$

3) Apply required **band transformation** $ F(s) $ to analogue prototype using calculated analogue frequencies $ \omega_{i} $:
### $$ \color{blue}{ G_{A}(s) = H(F(s)|_{w_{i}}) } $$

4) Apply the **discretisation filter** from before:
 ### $$ \color{blue}{ G_{D}(z) = G_{A}(\Psi(z)) } \quad \Big( = H(F(\Psi(z))|_{w_{i}}) \Big) $$



