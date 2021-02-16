# Quadrature Amplitude Modulation (QAM)

# Introduction

Recall from **PAM**:

$ \large x_{b}(t) = \sum_{k} X_{k} p(t-kT) $

This is a **baseband** signal meaning it is centred at $ 0 Hz $.

To convert this to a **passband** signal we can **upconvert** the PAM signal by using the following:

$$ \large x_{p}(t) = x_{b}(t) \cos(2\pi f_{c} t) = ( \sum_{k} X_{k} p(t-kT) ) \cos(2\pi f_{c} t) $$

$$ X_{p}(f) = \dfrac{1}{2}(X_{b}(f-f_{c}) + X_{b}(f+f_{c})) $$

##### Note: Fourier Transform after using $ \cos(2\pi f_{c} t) = \dfrac{e^{-j 2 \pi f_{c} t} + e^{j 2 \pi f_{c} t} }{2} $

##### However this method uses twice the bandwidth to transmit the same amount of information!

</br>

We can improve on this by using **complex-valued symbols**, giving the **QAM signal**:

$$ \large \color{blue}{
\begin{align*}
x(t) &= Re( \sqrt{2} \ x_{b}(t) \ e^{j 2\pi f_{c} t} ) \\
x(t) &= \sqrt{2} \sum_{k} p(t-kT) \ \Big( Re(X_{k}) \cos(2\pi f_{c} t) - Im(X_{k}) \sin(2\pi f_{c} t) \Big)
\end{align*}
}
$$

</br>

##### The carrier signals $ \cos(2\pi f_{c} t) $ and $ \sin(2\pi f_{c} t) = \cos(2\pi f_{c} t - \dfrac{\pi}{2}) $ are known as "in-phase" and "quadrature" components and hence QAM is also known as I-Q Modulation. 
##### $ \sqrt{2} $ is for making the carrier signals have unit power. 

</br>

# Constellations
$ M $ symbols ($ log_{2}M $ bits)

### M-PSK (Phase Shift Key)

$ M $ points on a circle (Constant Magnitude $ A $, Variable Phase)

$ E_{s} = A^{2} $

### M-QAM

$ M $ points equally spaced $ d $ in a square

$ E_{s} = \dfrac{40d^{2}}{16} = 2.5 d^{2} $


</br>

# Orthonormal Basis for QAM

$$ \large \color{blue}{ x(t) = \sqrt{2} \sum_{k} p(t-kT) \ \Big( Re(X_{k}) \cos(2\pi f_{c} t) - Im(X_{k}) \sin(2\pi f_{c} t) \Big) } $$

Let </br>
$ X_{k}^{r} = Re(X_{k}) $ </br>
$ X_{k}^{i} = Im(X_{k}) $ </br>
$ f_{k}^{r} = \sqrt{2} \ p(t-kT) \cos(2\pi f_{c} t) $ </br>
$ f_{k}^{i} = - \sqrt{2} \ p(t-kT) \sin(2\pi f_{c} t) $ </br>

$$ \large x(t) = \sum_{k} X_{k}^{r} f_{k}^{r}(t) + X_{k}^{i} f_{k}^{i}(t) $$

$ f_{k}^{r}(t) $ and $ f_{k}^{i}(t) $ form an **orthonormal basis** meaning:

Inner product of two of the same components is 1 if indices are the same:

$ \langle f_{k}^{r}(t), f_{l}^{r}(t) \rangle = 1 \qquad k=l $

Inner product of real and imaginary components is always 0:

$ \langle f_{k}^{r}(t), f_{l}^{i}(t) \rangle = 0 $ 


# Detection

$$ \large y(t) = \Big( \sum_{k} X_{k}^{r} f_{k}^{r}(t) + X_{k}^{i} f_{k}^{i}(t) \Big) + n(t) $$

We could perform two separate demodulations however this is not efficient (as inner product is an expensive computation):

$$ Y_{k}^{r} = \langle y(t), f_{k}^{r}(t) \rangle = \color{blue}{ X_{k}^{r} } + N_{k}^{r} $$

$$ Y_{k}^{i} = \langle y(t), f_{k}^{i}(t) \rangle = \color{red}{ X_{k}^{i} }  + N_{k}^{i} $$


## Demodulation

### 1) Multiply by the carrier signal

$ x(t) \cdot \sqrt{2} \cos(2\pi f_{c} t) = \sum_{k} p(t-kT) \ \color{blue}{ X_{k}^{r} } + \color{blue}{ X_{k}^{r} } \cos(4 \pi f_{c} t) - \color{red}{ X_{k}^{i} } \sin(4 \pi f_{c} t) $
$ x(t) \cdot -\sqrt{2} \sin(2\pi f_{c} t) = \sum_{k} p(t-kT) \ \color{red}{ X_{k}^{i} } - \color{red}{ X_{k}^{i} } \cos(4 \pi f_{c} t) - \color{blue}{ X_{k}^{r} } \sin(4 \pi f_{c} t) $


### 2) Apply lowpass filter

Remove high-frequency components ie. $ \sin(4 \pi f_{c} t) $ and $ \cos(4 \pi f_{c} t) $ terms.

</br>

Now we essentially have **2 PAM signals**:
 
$$ Lowpass( y(t) \cdot \sqrt{2} \cos(2\pi f_{c} t) ) \qquad = \qquad y^{r}(t) = \sum_{k} \color{blue}{ X_{k}^{r} } \ p(t-kT) + n^{r}(t) $$
$$ Lowpass( y(t) \cdot - \sqrt{2} \sin(2\pi f_{c} t) ) \qquad = \qquad y^{i}(t) = \sum_{k} \color{red}{ X_{k}^{i} } \ p(t-kT) + n^{i}(t) $$


### 3) Apply matched filter $ p(-t) $ and sample $ t = mT $
$$ y^{r}(t) * p(-t) |_{t=mT} = \big( x^{r}(t) + n^{r}(t) \big) * p(-t) |_{t=mT} \qquad = \qquad Y_{m}^{r} = X_{m}^{r} + N_{m}^{r} $$ 

$$ y^{i}(t) * p(-t) |_{t=mT} = \big( x^{i}(t) + n^{i}(t) \big) * p(-t) |_{t=mT} \qquad = \qquad Y_{m}^{i} = X_{m}^{i} + N_{m}^{i} $$

</br>

## Optimal Detection
The process is the same as for PAM, but now we are essentially considering a **2D gaussian** or equivalently **symbol vectors**:

$ \underline{Y} = \begin{pmatrix} Y^{r} \\ Y^{i} \end{pmatrix} $, 
$ \underline{X} = \begin{pmatrix} X^{r} \\ X^{i} \end{pmatrix} $

$ \large N^{r}, N^{i} \sim \mathcal{N}(0, \dfrac{N_{0}}{2}) $

### MAP (Optimal)

$$ \hat{X} = \arg_{\underline{x} \in \mathcal{C}} \max P(X = \underline{x}) f(Y=\underline{y} | X=\underline{x}) $$

### ML (Optimal when Uniform symbol probability)

$$ \begin{align*} 
\underline{\hat{X}} &= \arg_{\underline{x} \in \mathcal{C}} \max f(Y=\underline{y} | X=\underline{x}) \\
&= \arg_{\underline{x} \in \mathcal{C}} \mathcal{N}\big(y^{r}-x^{r}| 0, \dfrac{N_{0}}{2}\big) \mathcal{N}\big(y^{i}-x^{i}| 0, \dfrac{N_{0}}{2}\big)
\end{align*}
$$

### Min Dist (ML when Gaussian)

$$ \begin{align*}
\underline{\hat{X}} &= \arg_{\underline{x} \in \mathcal{C}}\min || \underline{y} - \underline{x} ||^{2} \\ 
&= \arg_{\underline{x} \in \mathcal{C}}\min \ (\underline{y} - \underline{x})^{T} (\underline{y} - \underline{x}) \\
&= \arg_{\underline{x} \in \mathcal{C}}\min || \underline{y} ||^{2} + || \underline{x} ||^{2} - 2 \underline{x}^{T} \underline{y}  \\\\
\text{(1) QAM Simplifies to } \\
&= \arg_{\underline{x} \in \mathcal{C}}\min || \underline{x} ||^{2} - 2 \underline{x}^{T} \underline{y}  \\\\
\text{(2) PSK Further simplifies to} \\
&= \arg_{\underline{x} \in \mathcal{C}}\min || \underline{x} ||^{2} - 2 ||\underline{x}|| \ ||\underline{y}|| \cos(\theta(\underline{x}, \underline{y}))  \\
&= \arg_{\underline{x} \in \mathcal{C}}\min \theta(\underline{x}, \underline{y})
\end{align*}
$$

**(1)** - Simplifies since $ ||\underline{y}||^{2} $ does not affect $ \arg \min $.

**(2)** - Simplifies since $ || \underline{x} ||^{2} - 2 ||\underline{x}|| \ ||\underline{y}|| \cos(\theta(\underline{x}, \underline{y})) $ is minimised when $ \theta(\underline{x}, \underline{y}) $ is minimised.


## Summary

#### Rate $ \dfrac{1}{T} $ symbols/s $ \dfrac{log_{2}M}{T} $ bits/s

#### Passband Bandwidth of QAM = $ 2 W $ if baseband bandwidth of pulse p(t) = $ W $



