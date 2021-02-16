# Frequency Shift Keying (FSK)

## Introduction

For $ i = 1, ..., M $ symbols:

$$ \large \color{blue}{ x(t) = \sqrt{E_{s}} \sqrt{\dfrac{2}{T}} \cos \Big(2\pi \big(f_{c} - \color{red}{(\frac{M+1}{2} - i) \Delta f} \big) t \Big) }
$$

## Orthonormal Basis

$$ \large \color{blue}{ f_{i}(t) = \sqrt{\dfrac{2}{T}} \cos \Big(2\pi \big(f_{c} - (\frac{M+1}{2} - i) \Delta f\big) t \Big) }
$$

$$ \large x(t) = \sum_{k} x_{k} f_{k}(t) $$

where $ \underline{x} = \{0, ..., \sqrt{E_{s}}, ..., 0\} $ where $ x_{i} = \sqrt{E_{s}} $ for $ i $ being the i-th message transmitted.


</br>

## Detection

$$ \large x(t) = \sqrt{E_{s}} f_{i}(t) $$

$$ \Large y(t) = \Big( \sqrt{E_{s}} f_{i}(t) \Big) + n(t) $$

</br>

### Demodulation

$$ \large Y_{k} = \langle y(t), f_{k}(t) \rangle = \langle x(t), f_{k}(t) \rangle + \langle n(t), f_{k}(t) \rangle = X_{k} + N_{k} $$

The transmitted symbol has a non-zero value $ X_{i} = \sqrt{E_{s}} $ :

$ \large X_{k} = \begin{cases}
\sqrt{E_{s}} \qquad k=i \\
0 \qquad \qquad k \ne i
\end{cases}
$.

$$ \large [Y_{1}, ..., Y_{i},..., Y_{N}] = [N_{1}, ..., X_{i} + N_{i},..., N_{N}] $$

</br>

### Optimal Detection

$$ \large
\begin{align*}
\hat{m} &= \arg_{1\le i \le M}\max \ P(\underline{y} | \underline{X} = \underline{x}_{i}) \\
&= \arg_{1\le i \le M}\max \ \prod_{k} P(y_{k} | x_{k}) \\
\hat{m} &= \arg_{1\le i \le M}\max \ y_{i} \\
\end{align*}
$$


### Probability of Error

$$ 
\large 
\begin{align*}
P_{e} &= P(y_{i} \le y_{1} \ \cup ... \cup \ y_{i} \le y_{N} ) \\ \\
P_{e} &\le \sum_{k} P(y_{i} \le y_{k}) \\
&= (M − 1) \ P(x_{i} + n_{i} \le n_{k}) \\
P_{e} &= (M − 1) \ P(n_{k} - n_{i} \ge x_{i} ) \\ 
&= (M − 1) \ P(n_{k} - n_{i} \ge \sqrt{E_{s}} ) \\ \\
n_{k} &\sim \mathcal{N}(0, \dfrac{N_{0}}{2}) \\
\therefore \Delta N = (n_{k} - n_{i}) &\sim \mathcal{N}(0, N_{0}) \\ \\
P_{e} &= (M − 1) \ P( \Delta N \ge \sqrt{E_{s}} ) \\
\end{align*}
$$


## Summary

### Bandwidth

$ B_{QAM} = 2W $

$ B_{FSK} = (M − 1)\ \Delta f = \dfrac{M-1}{2T} $

### Bandwidth Efficiency

$ \eta_{QAM} \approx \log_{2} M $ bits/s/Hz

$ \eta_{FSK} \approx \dfrac{\log_{2} M}{\dfrac{M-1}{2}} $ bits/s/Hz

