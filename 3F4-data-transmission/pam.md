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
$ \phi_{k}(t) = p(t-kT) $

$$ \large \color{blue}{ x(t) = \sum_{k} X_{k} \ p(t-kT) } $$

$$ \large \color{blue}{ y(t) = \sum_{k} X_{k} \ p(t-kT) + n(t) }$$

Taking the **inner product with the basis function** $ \phi_{m}(t) $:

$$ \large Y_{m} = \langle y(t), \phi_{m}(t) \rangle = X_{m} + \langle n(t), \phi_{m}(t) \rangle = X_{m} + N_{m} $$

Practically we would need to compute $ N $ inner products (where $ N $ is the number of transmitted symbols ) which is not computationally efficient hence we use a matched (low-pass) filter and sample it to derive the same result as above:

### Matched Filter - $ \large q(t) = p(-t) $

$ \Large \color{blue}{ Y_{m} = r(mT) = y(t) * p(-t) |_{t=mT} = \big( x(t) + n(t) \big) * p(-t) |_{t=mT} = X_{m} + N_{m} } $

**Therefore we can simply sample the output of the matched filter to get the values of $ Y_{m} $ for any value of $ m $.**

</br>

## Optimal Decoding

**MAP (Optimal)**

**MAP = ML (for uniform symbol probability)**

**ML = Minimum Distance between $ Y_{k} $ and $ S \in \mathcal{S} $ (for AWGN)**

#### Note: In general we will only consider solving problems with minimum distance.

</br>

## Signal-Noise Ratio (SNR)

$ \dfrac{N_{0}}{2} $ is the **variance of the noise** $ \sigma^{2} $.

$ E_{bit} $ **Average energy per bit** 

**SNR per bit** $ \large SNR_{b} = \dfrac{E_{bit}}{N_{0}} $ </br>
**SNR per symbol** $ \large SNR_{s}  = \dfrac{E_{s}}{N_{0}} $ </br>

**Average energy per symbol** of the constellation
$$ \large E_{s} = E(\mathcal{S}^{2}) = \dfrac{1}{len(\mathcal{S})} \sum_{i}^{len(\mathcal{S})} S_{i}^{2} $$ 

$ \large E_{s} = b \ E_{bit} = \log_{2}(M) \enspace E_{bit} $


</br>

## Nyquist Pulse Criterion

$ \large p(t) $ &emsp; &emsp; &emsp; &emsp; &emsp; &emsp; **Transmit Filter** </br>
$ \large q(t) = p(-t) $ &emsp; &emsp; &emsp; **Receive Filter** </br>
$ \large \color{blue}{ g(t) = p(t) * q(t) } $ &emsp;  &emsp; **Overall Filter** "Effective" pulse </br>

$$ \Large
\begin{align*}
r(t) &= x(t) * q(t) \\
r(t) &= \Big(\sum_{k} X_{k} p(t-kT)\Big) * q(t) \\
r(t) &= \sum_{k} X_{k} \Big( p(t-kT) * q(t) \Big) \\
r(t) &= \sum_{k} X_{k} \ g(t-kT) \\
\end{align*}
$$

For $ r(mT) = \sum_{k} X_{k} \ g((m-k)T) $ to be equal to $ X_{m} $, we require that:

$$ \large g((m-k)T) = \begin{cases} 1 \quad k=m \\ 0 \quad k \ne m \end{cases} $$

If **NPC** is not obeyed, we get **inter-symbol interference (ISI)** (noise is magnified).

This means that the **effective pulse/overall filter must be a pulse function in discrete-time**.

##### The equivalent statement in frequency domain is known as the Nyquist Pulse Criterion. 

$$ \large \color{blue}{ \sum_{n=-\infty}^{\infty} G(f - \dfrac{n}{T}) = T } $$

### Proof
#### Overall filter $ g(mT) $ must be an impulse function at $ m = 0 $
**Multiply $ g(t) $ by pulse train and set equal to $ \delta(t) $**

$$
\begin{align*}
g(t) \sum_{m=-\infty}^{\infty} \delta(t-mT) &= \delta(t) \\
G(f) * \mathcal{F}\big\{ \sum_{m=-\infty}^{\infty} \delta(t-mT) \big\} &= 1 \\
G(f) * \dfrac{1}{T} \sum_{n=-\infty}^{\infty} \delta(f-\dfrac{n}{T}) &= 1 \\
\sum_{n=-\infty}^{\infty} G(f - \dfrac{n}{T}) &= T \\
\end{align*}
$$

Since the above is true, the **bandwidth** $ [-B,B] $ must be atleast $ \dfrac{1}{2T} $ meaning from $ [-\dfrac{1}{2T},\dfrac{1}{2T}] $ so that the equation above can be at minimum be equal to $ T $.

</br>

### Band-Edge Symmetry
Assuming that the **pulse bandwith lies in $ (\dfrac{1}{2T}, \dfrac{1}{T} ] $** and assuming real and even $ g(t) $ and $G(f)$:

$$ \large G(\dfrac{1}{2T} - \Delta) + G(\dfrac{1}{2T} + \Delta) = T \qquad \Delta \in [0, \dfrac{1}{2T}] $$ 


### Filter Design
Given $ G(f) $:

$ Q(f) = P(-f) $

$$ \large \color{blue}{ G(f) = P(f) Q(f) = |P(f)|^{2} } $$

Therefore we can design $ P(f) $ and $ Q(f) $ or just consider $ P(f) = Q(f) = \sqrt{G(f)} $. 

$ p(t) = \mathcal{F}^{-1}(P(f)) $

#### Note: For $ p(t) $ to be causal we have to truncate and delay the time-domain function. This can lead to non-idealities.




