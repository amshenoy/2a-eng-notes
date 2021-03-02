# Dispersive Channels

A **channel frequency response** $ H(f) $ that is **not flat in the transmission band** is called **frequency-selective** or **dispersive**.

Consider the baseband signal $ \large x(t) = \sum_{k} X_{k} \ p(t-kT) $:

$$ \large y(t) = \Big( \sum_{k} X_{k} \ f(t-kT) \Big) + n(t) $$

where $ \large f(t) = h(t) * p(t) $.


</br>

# Equalisation

At the receiver, we apply the low pass filter $ \large r(t) = y(t) * q(t) $ and sample the output $ \large r(t)|_{t=mT} $:

$ \large r(t) = \Big( \sum_{k} X_{k} \ g(t-kT) \Big) + N(t) $

where $ g(t) = f(t) * q(t) = h(t) * p(t) * q(t) $ and $ N(t) = n(t)*q(t)$

</br>

To make notation easier to parse, consider $ \underline{r} = \{ r_{m} \} = \{ r(mT) \} $ and $ \underline{g} = \{ g_{m} \} = \{ g(mT) \} $ :

$$ \large
\begin{align*}
r_{m} & = \sum_{k} X_{k} \ g_{m-k} + N_{m} \\
& = \sum_{l=0}^{L} X_{m-l} \ g_{l} + N_{k+l} \qquad \small (L \ \text{non-zero components of } g_{l}) \\
\end{align*}
$$ 

We can take the **Z-transform** giving us the following:

$$ \large R(z) = X(z)G(z) + N(z)$$

Then apply the **zero-forcing equaliser** filter &ensp; $ \large H_{E}(z) = \dfrac{1}{G(z)} $ &ensp; (**IIR filter** - Infinite non-zero coeffs). The output of the filter $ O(z) $ is the following:

$$ O(z) = R(z) H_{E}(z) = \underbrace{ \dfrac{R(z)}{G(z)} }_{(1)} = \underbrace{ X(z) + \dfrac{N(z)}{G(z)} }_{(2)} $$

$(1)$ shows us how we can implement the filtering process. We can use an iterative method in the $ k $-domain by writing $ Y(z) G(z) = R(z) $ ie. $ \underline{r} = \underline{y} * \underline{g} = \sum_{l=0}^{L} g_{l} \ y_{n-l} = g_{0} \ y_{n} + ... + g_{L} \ y_{n-L} $. Rearrange for $y_{n}$ and recursively find $ y_{n} $ using previous terms as well as the known $ g_{n} $ filter terms.

$(2)$ shows that in the **absence of noise**, we **can exactly recover the symbols** $ X(z) $ (ie. **inter-symbol interference is removed**).


</br>


# Orthognal Frequency Division Multiplexing (OFDM)

