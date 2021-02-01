# Pulse Amplitude Modulation (PAM)

**PAM Modulator** - Converts bits into a time waveform $ x(t) $ </br>
**Transmission** - Assume some noise input $ y(t) = x(t) + n(t) $ </br>
**PAM Demodulator** - Converts time waveform $ y(t) $ into bits </br>

To transmit $ M $ symbols (ie. $ M $ amplitudes), each symbol is represented by $ b=\log_{2}{M} $ bits.

We can **transmit a series of bits** by converting them to symbols $ X_{k} $ at time $ k $ and applying **PAM**:

$$ \large \underline{01} \ \underline{00} \ ... \underline{01} \qquad \rightarrow \qquad X_{1}, X_{2}, ..., X_{N} \qquad \rightarrow \qquad \sum_{k} X_{k} \ p(t-kT) $$

## Choice of pulse function $ p(t) $

- $ p(t) $ should decay quickly in time (ideal would be $ \delta(t) $) such as to not affect the next symbol.
- $ p(t) $ should be bandlimited to $ [-W, W] $.
- Good recovery after the addition of noise $ n(t) $, therefore **shifted pulses must form an orthonormal basis** $ \phi_{k}(t)$.

</br>

### Time-Decay vs Bandwidth Tradeoff

**Sinc function** - $ p(t) = \dfrac{1}{\sqrt{T}} sinc(\dfrac{\pi t}{T}) $ (Perfectly **band-limited** but **decays slowly in time**)

**Rect function** - $ p(t) = \dfrac{1}{\sqrt{T}} \quad [-\dfrac{T}{2}, \dfrac{T}{2}] $ (Perfectly **time-limited** but **decays slowly in frequency**)

We need the best of both!

</br>

## Signal Space Projection

$$ \large x(t) = \sum_{k} X_{k} p(t-kT) = \sum_{k} X_{k} \phi_{k}(t) $$

$$ \large y(t) = \sum_{k} X_{k} p(t-kT) + n(t) = \sum_{k} X_{k} \phi_{k}(t) + n(t) $$

Taking the **inner product with the basis function** $ \phi_{k}(t) $:

$$ \large Y_{m} = \langle y(t), \phi_{m}(t) \rangle = X_{m} + \langle n(t), \phi_{m}(t) \rangle = X_{m} + N_{m} $$

Practically we would need to compute $ N $ inner products (where $ N $ is the number of transmitted symbols ) which is not computationally efficient hence we use a matched (low-pass) filter and sample it to derive the same result as above:

### Matched Filter - $ \large q(t) = p(-t) $

$ \Large \color{blue}{ Y_{k} = r(kT) = y(t) * p(-t) |_{t=kT} = X_{k} + N_{k} } $

$$ \Large 
\begin{align*}
r(kT) &= r(t) |_{t=kT} \\
&= y(t) * q(t) |_{t=kT} \\
&= x(t) * q(t) + n(t) * q(t) \ |_{t=kT} \\
r(kT) &= X_{k} + N_{k}
\end{align*}
$$

**Therefore we can simply sample the output of the matched filter to get the values of $ Y_{k} $ for any value of $ k $.**

</br>

## Optimal Decoding

**MAP (Optimal)**

**MAP = ML = Minimum Distance between $ Y_{k} $ and $ S \in \mathcal{S} $ (for AWGN)**

</br>

## Signal-Noise Ratio (SNR)

$ \dfrac{N_{0}}{2} $ is the **variance of the noise** $ \sigma^{2} $.
*Average energy per bit* $ E_{bit} $

**SNR per bit** $ \large SNR_{b} = \dfrac{E_{bit}}{N_{0}} $ </br>
**SNR per symbol** $ \large SNR_{s}  = \dfrac{E_{s}}{N_{0}} $ </br>

**Average energy per symbol** of the constellation
$$ \large E_{s} = E(\mathcal{S}^{2}) = \dfrac{1}{len(\mathcal{S})} \sum_{i}^{len(\mathcal{S})} S_{i}^{2} $$ 

$ \large E_{s} = b \ E_{bit} = \log_{2}(M) \enspace E_{bit} $


