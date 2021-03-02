# Dispersive Channels

> A **channel frequency response** $ H(f) $ that is **not flat in the transmission band** is called **frequency-selective** or **dispersive**.

</br> </br>

# Equalisation


Consider the **baseband signal** $ \large x(t) = \sum_{k} X_{k} \ p(t-kT) $ where $ h(t) $ is the **channel impulse response**:

$$ \large y(t) = \Big( \sum_{k} X_{k} \ f(t-kT) \Big) + n(t) $$

where $ \large f(t) = h(t) * p(t) $.

</br>

At the receiver, we apply the low pass filter $ \large r(t) = y(t) * q(t) $ and sample the output $ \large r(t)|_{t=mT} $:

$$ \large \color{blue}{ r(t) = \Big( \sum_{k} X_{k} \ g(t-kT) \Big) + N(t) } $$

where $ g(t) = f(t) * q(t) = h(t) * p(t) * q(t) $ and $ N(t) = n(t)*q(t)$

</br>

To make notation easier to parse, consider $ \underline{r} = \{ r_{m} \} = \{ r(mT) \} $ and $ \underline{g} = \{ g_{m} \} = \{ g(mT) \} $ :

$$ \large \color{blue}{
\begin{align*}
r_{m} & = \sum_{l=0}^{L} g_{l} \ X_{m-l} + N_{m}  \qquad \small (L \ \text{non-zero components of } g_{l}) \\
\end{align*}
}
$$ 

##### Note: That in the case of no ISI, we would have $ r_{m} = X_{m} g_{0} + n_{m} $ but due to the convolution summation we get interference from the other symbols $ X_{m-l} $. The goal is to remove this by applying a filter.

</br> </br>

## Zero-Forcing Equaliser (IIR)

We can take the **Z-transform** giving us the following:

$$ \large \color{blue}{ R(z) = X(z)G(z) + N(z) } $$

Then apply the **zero-forcing equaliser** filter &ensp; $ \large \color{blue}{ H_{E}(z) = \dfrac{1}{G(z)} } $ &ensp; (**IIR filter** - Infinite non-zero coeffs). The output of the filter $ W(z) $ is the following:

$$ W(z) = R(z) H_{E}(z) = \underbrace{ \dfrac{R(z)}{G(z)} }_{(1)} = \underbrace{ X(z) + \dfrac{N(z)}{G(z)} }_{(2)} $$

$(1)$ shows us how we can implement the filtering process. We can use an iterative method in the $ k $-domain by writing $ Y(z) G(z) = R(z) $ ie. $ \underline{r} = \underline{y} * \underline{g} = \sum_{l=0}^{L} g_{l} \ y_{n-l} = g_{0} \ y_{n} + ... + g_{L} \ y_{n-L} $. Rearrange for $y_{n}$ and recursively find $ y_{n} $ using previous terms as well as the known $ g_{n} $ filter terms.

$(2)$ shows that in the **absence of noise**, we **can exactly recover the symbols** $ X(z) $ (ie. **inter-symbol interference is removed**).


</br> </br>

## Zero-Forcing Equaliser (FIR)

> We want to design a $K+1$-tap equalising (removes ISI) filter $ \underline{h} = \{h_{0}, ..., h_{K}\}$.

Given $ \underline{g} = \{g_{0}, ..., g_{L} \}$, apply the general filter $ \underline{h} = \{h_{0}, ..., h_{K}\}$ to $ \underline{r} $. The output $ \underline{w} $ is given by:

$$
\begin{align*}
\underline{w} &= \underline{h} * \underline{r} = \underline{h} * \Big( \underline{g} * \underline{X} + \underline{n} \Big) \\
&= (\underline{h} * \underline{g}) * \underline{X} + \underline{h}*\underline{n} \\
\text{Let } \underline{f} = \underline{h} * \underline{g} \qquad f_{l} = \sum_{k=0}^{K} \ h_{k} \ g_{l-k} \\ \\

\underline{w} &= \underline{f} * \underline{X} + \underline{h}*\underline{n} \\ \\

w_{m} &= \sum_{j=0}^{L+K} X_{m-j} f_{j} + \sum_{i=0}^{K} h_{i} n_{m-i} \\
w_{m} &= X_{m} f_{0} + \underbrace{ \sum_{j=1}^{L+K} X_{m-j} f_{j} }_{ISI} + \sum_{i=0}^{K} h_{i} n_{m-i} \\

\end{align*}
$$

We can try to **eliminate the ISI term** by attempting to get $ f_{j} = \begin{cases} 1 \qquad j=0 \\ 0 \qquad j \ne 0 \end{cases} $ by setting the values of $ h_{i} $.

##### Note: We have to satisy $ L+K+1 $ equations with $ K + 1 $ degrees of freedom (number of filter coefficients). Therefore **perfect zero-forcing is not possible with an FIR filter**. 

</br>

### Given $ \color{green}{ \underline{g} } $ and $ \color{blue}{ f_{l} = \begin{cases} 1 \qquad l=0 \\ 0 \qquad l \ne 0 \end{cases} } $, solve for $ \color{green}{ \underline{h} } $ by solving $ K $ equations $ l = 0, ..., K-1 $:

$$ \Large \color{blue}{ f_{l} = \sum_{k=0}^{K} \ h_{k} \ g_{l-k} } $$

</br>

After solving this we will have eliminated $ K $ ISI terms:

$ \begin{align*}
w_{m} &= X_{m} f_{0} + \underbrace{ \sum_{j=1}^{L+K} X_{m-j} f_{j} }_{ISI} + \sum_{i=0}^{K} h_{i} n_{m-i} \\
\text{becomes} \\
w_{m} &= X_{m} + \underbrace{ \sum_{j=\color{purple}{K+1}}^{L+K} X_{m-j} f_{j} }_{\text{Residual } ISI} + \sum_{i=0}^{K} h_{i} n_{m-i} \\
\end{align*}
$

##### Note: However the filter terms increase the power of the noise:
$ E\Big( (\sum_{i=0}^{K} h_{i} n_{m-i} )^{2} \Big) = \sigma^{2} \sum_{i=0}^{K} h_{i}^{2} $
##### Therefore there is a trade-off between minimising residual interference and noise amplification.


</br> </br>


## MMSE Equalisation

> Instead of applying a filter, here we consider a **direct optimisation method** that minimises $ E \Big( (X_{m}-\hat{X}_{m} )^{2} \Big) $.

The estimate $ \hat{X}_{m} $ is generated as follows:
$$ \large \hat{X}_{m} = c_{0} \ r_{m} + ... + c_{K} \ r_{m+K} $$

where $ r_{m} = \sum_{l=0}^{L} X_{k} \ g_{m-l} + N_{m} $.

Let $ \underline{r} = \{ r_{m}, \ ..., \ r_{m+K} \} $. 


We want to determine the vector $ \underline{c} = \{c_{0}, \ ..., \ c_{K} \} $ such that $ E \Big( (X_{m}-\hat{X}_{m} )^{2} \Big) $ is minimised.

$$ \large \color{blue}{
\begin{align*}
\underline{c}^{*} &= \arg_{\underline{c}} \min E \Big( (X_{m}-\hat{X}_{m} )^{2} \Big) \\
&= \arg_{\underline{c}} \min E \Big( (X_{m}-\underline{r}^{T} \ \underline{c}  )^{2} \Big) 
\end{align*}
}
$$

</br>

$$
\begin{align*}
\dfrac{d}{d\underline{c}} & E \Big( (X_{m}-\underline{r}^{T} \ \underline{c}  )^{2} \Big) = 0 \\
& E \Big( \dfrac{d}{d\underline{c}} (X_{m}-\underline{r}^{T} \ \underline{c}  )^{2} \Big) = 0 \\
& E \Big( -2 \underline{r} \ (X_{m}-\underline{r}^{T} \ \underline{c}  ) \ \Big) = 0 \\
& E \Big( \underline{r} \ (X_{m}-\underline{r}^{T} \ \underline{c}  ) \ \Big) = 0 \\
& E \Big( \underline{r} X_{m} \Big) = E \Big( \underline{r} \underline{r}^{T} \Big) \ \underline{c} \\ \\
\therefore \underline{c}^{*} &= \Big( \underbrace{ E \big( \underline{r} \underline{r}^{T} \big) }_{ R = (K+1) \times (K+1)} \Big)^{-1}  \ \underbrace{ E \big( \underline{r} X_{m} \big) }_{\underline{p}} \\ \\
\underline{c}^{*} &= R^{-1} \underline{p}
\end{align*}
$$

</br>

## Summary

- Both the **MMSE and the zero forcing equalisers are linear equalisers**: The estimate of each symbol is a **linear combination of the observed sequence** $ \{r{m}\} $.

- There are also **non-linear equalisation** techniques such as “decision feedback equalisers”.

- We **assume a constant** $ \underline{g} $ which in practice may not be true since the **channel frequency response may be time-varying**. Hence we would need to use **adaptive equalisation** (used widely in practice such as telephone networks).
 

</br> <hr> </br>

# Orthognal Frequency Division Multiplexing (OFDM)

</br>

Consider the **passband signal**:
$$ \large
\begin{align*}
x(t) &= Re(x_{b}(t) e^{j 2\pi f_{c} t}) = x_{b}(t) \cos(2\pi f_{c} t) \\
&= \Big( \sum_{k} \ x_{k} \ p(t-kT) \Big) \ \cos(2\pi f_{c} t) \\
&= \sum_{k} p(t-kT) \ \Big( Re(x_{k}) \cos(2\pi f_{c} t) - Im(x_{k}) \sin(2\pi f_{c} t) \Big) 
\end{align*}
$$

##### Note: Although we consider the signal to be the same as that used in QAM, the symbols are not distributed according to the QAM constellation.

</br>

Consider $ \large h(t) = Re( \ h_{b}(t) \ e^{j 2\pi f_{c} t} \ ) = h_{b}(t) \cos(2\pi f_{c} t) $ where $ \large h_{b}(t) $ is the **baseband equivalent impulse response**:

$$ \large 
\begin{align*}
y(t) &= x(t)*h(t) + n(t) \\
y(t) &= \sum_{k} f(t-kT) \ \Big( Re(x_{k}) \cos(2\pi f_{c} t) - Im(x_{k}) \sin(2\pi f_{c} t) \Big) + n(t)
\end{align*}
$$

where $ \large f(t) = h_{b}(t) * p(t) $.

</br>

### Multiply, Lowpass, Matched, Sample (as in QAM)

$$ y_{r}(t) = Lowpass( y(t) \cdot \cos(2\pi f_{c} t) )\qquad = \qquad \sum_{k} \color{blue}{ x_{k}^{r} } \ f(t-kT) + n^{r}(t)  $$
$$ y_{i}(t) =  Lowpass( y(t) \cdot - \sin(2\pi f_{c} t) ) \qquad = \qquad \sum_{k} \color{red}{ x_{k}^{i} } \ f(t-kT) + n^{i}(t) $$

$$ \large 
\begin{align*}
r(t) &= ( \ y_{r}(t) + j \ y_{i}(t) \ ) * p(-t) \\ \\
r(t) &= \sum_{k} x_{k} \ g(t-kT) \ + n(t) \\
r_{m} &= \sum_{k} x_{k} \ g_{m-k}  \ + n_{m} \\
\end{align*}
$$


$$ \Large \color{blue}{ r_{m} = \sum_{l=0}^{L} g_{l} \ x_{m-l}  \ + n_{m} } $$

</br>

where $ \large g(t) = f(t) * p(-t) = p(t) * h_{b}(t) * p(-t) $, $ \large r_{m} = r(mT) $ and $ \large g_{m} = g(mT) $.

</br>










