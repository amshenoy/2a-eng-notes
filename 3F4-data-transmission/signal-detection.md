# Signal Detection

## General LTI Noise Model 
$$ \large y(t) = h(t) * x(t) + n(t) $$
$$ \large Y(f) = H(f) X(f) + N(f) $$

## AWGN Model
$$ \large y(t) = x(t) + n(t) $$

simplified from general model when $ h(t) = c \delta(t-\tau) $ or $ H(f) = c e^{-j 2\pi f \tau}$

We can use the AWGN model as a simplification when delay is constant and power spectrum is constant in magnitude since we can compensate for the delay and attentuation.

### White Noise

$ \large E(n(t) n(t+\tau)) = R_{nn}(\tau) = \dfrac{N_{0}}{2} \delta(\tau) $

$ \text{Constant PSD} \qquad \large S_{nn}(f) = \dfrac{N_{0}}{2} $

</br>

## Applications

### Baseband
**Telephone** - AWGN

**DSL** - General

### Passband
**Geostationary** - AWGN

**Mobile Wireless** - General ($ L $ signal paths with different delays and attenuations. $ h(t) = \sum_{i}^{L} c_{i} \delta(t-\tau_{i})$ )

</br><hr></br>

# Signal Detection

## Setup
Consider a set of M possible messages $ \{s_{1}(t), ..., s_{M}(t) \} $ that can be transmitted.

One of the messages $ i $ is transmitted $ x(t) = s_{i}(t) $.

The channel has the output $ y(t) = x(t) + n(t) $. We want to detect the original signal $ x(t) $ from $ y(t) $.

</br>

If $ \{ \phi_{1}(t), ..., \phi_{k}(t) \} $ is an orthonormal basis for the signal set, then each input $ x(t) $ can be defined as a vector $ \underline{x} = \{x_{j}\} = \{\int x(t) \phi_{j}^{*}(t) dt\} $.

The noise waveform $ n(t) $ in general will not lie in the signal space (ie. it extends out of the signal space). Therefore $ y(t) $ does not lie in the signal space.

</br>

## Output Projection Vector

By projecting $ y(t) $ into the signal space, we can find the vector representation $ \underline{y} $:

$$ \large 
\begin{align*}
\underline{y} &= \{y_{j}\} = \Big\{\int y(t) \ \phi_{j}^{*}(t) \ dt \Big\} \\
&= \Big\{\int \big( x(t) + n(t) \big) \ \phi_{j}^{*}(t) \ dt \Big\} = \Big\{\int x(t) \ \phi_{j}^{*}(t) \ dt \Big\} + \Big\{\int n(t) \ \phi_{j}^{*}(t) \ dt \Big\}\\
\underline{y} &= \Big\{x_{j}\Big\} + \Big\{n_{j}\Big\} = \underline{x} + \underline{n}
\end{align*}
$$

$$ \Large \color{blue}{ \underline{y} = \underline{x} + \underline{n} } $$

</br>

## Noise Vector Characteristic

For optimal detection, we first need to understand the distribution of the (random) noise vector $ \underline{n} $.

$ E(n_{j}) = E\Big( \int n(t) \ \phi_{j}^{*}(t) \ dt \Big) = \int E(n(t)) \ \phi_{j}^{*}(t) \ dt = 0 $

$$ \large \color{blue}{ E(n_{j}) = 0 } $$

$
\begin{align*}
E(n_{l}n_{m}) &= E\Big( \int n(t) \ \phi_{l}^{*}(t) \ dt \int n(s) \ \phi_{m}^{*}(s) \ ds \Big) \\
&= \int \int E(n(t)n(s)) \ \phi_{l}^{*}(t) \ dt \ \phi_{m}^{*}(s) \ ds \\
&= \int \int \dfrac{N_{0}}{2} \delta(s-t) \ \phi_{l}^{*}(t) \ dt \ \phi_{m}^{*}(s) \ ds  \\
&= \dfrac{N_{0}}{2} \int \phi_{l}^{*}(s) \ \phi_{m}^{*}(s) \ ds \\
&= \dfrac{N_{0}}{2} \delta(m-l)
\end{align*}
$

$$ \large \color{blue}{ E(n_{l}n_{m}) = \dfrac{N_{0}}{2} \delta(m-l) } $$

These results for the discrete version are exactly the same as the continuous version.

</br>

## Optimal Detection

### Maximum a Posteriori (MAP) [Optimal]

$$ \Large \color{green}{
\begin{align*}
\hat{\underline{x}}_{MAP} &= \arg_{\underline{s}_{i} \in \mathcal{S}} \max P(\underline{x} = \underline{s}_{i} | \underline{y}) \\
\hat{\underline{x}}_{MAP} &= \arg_{\underline{s}_{i} \in \mathcal{S}} \max P(\underline{x} = \underline{s}_{i}) p(\underline{y} | \underline{x} = \underline{s}_{i}) \\
\end{align*}
}
$$

### Maximum Likelihood

**ML is equivalent to MAP and hence optimal only when $ P(\underline{x} = \underline{s}_{i}) = \text{Constant} $ (ie. uniform prior):**
 
$$ \Large \color{blue}{
\begin{align*}
\hat{\underline{x}}_{ML} &= \arg_{\underline{s}_{i} \in \mathcal{S}} \max  p(\underline{y} | \underline{x} = \underline{s}_{i}) \\
\end{align*}
}
$$

#### ML Detection in AWGN

Consider the **likelihood PDF** $ \color{red}{ p(\underline{y} | \underline{x} = \underline{s}_{i}) = p_{n}(\underline{y} - \underline{s}_{i}) = \prod_{i} p_{n}(y_{i} - s_{i}) } $.

Minimising the **log likelihood** for the iid Gaussian PDF $ \mathcal{N}(0, \dfrac{N_{0}}{2})$ :

$$ \Large \color{purple}{ \hat{\underline{x}}_{ML} = \arg_{\underline{s}_{i} \in \mathcal{S}} \min |\underline{y} - \underline{s}_{i}|^{2} } $$


### Probability of Detection Error

$$ \color{blue}{  P_{e} = \sum_{i} P(\underline{x} = \underline{s}_{i}) P(\hat{\underline{x}}^{ML} \ne \underline{s}_{i} | \underline{x} = \underline{s}_{i}) } $$

For **constant/uniform prior**:

$$ \color{purple}{  
\begin{align*}
P_{e} &= P(\hat{\underline{x}}^{ML} \ne \underline{s}_{i} | \underline{x} = \underline{s}_{i}) \\
&= 1 - P(\hat{\underline{x}}^{ML} = \underline{s}_{i} | \underline{x} = \underline{s}_{i}) \\
\end{align*}
}
$$
