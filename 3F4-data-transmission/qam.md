# Quadrature Amplitude Modulation (QAM)

## Introduction

Recall from **PAM**:

$ \large x_{b}(t) = \sum_{k} X_{k} p(t-kT) $

This is a **baseband** signal meaning it is centred at $ 0 Hz $.

To convert this to a **passband** signal we can **upconvert** the PAM signal by using the following:

$$ \large x_{p}(t) = x_{b}(t) \cos(2\pi f_{c} t) = ( \sum_{k} X_{k} p(t-kT) ) \cos(2\pi f_{c} t) $$

$$ X_{p}(f) = \dfrac{1}{2}(X_{b}(f-f_{c}) + X_{b}(f+f_{c})) $$

##### Note: Fourier Transform after using $ \cos(2\pi f_{c} t) = \dfrac{e^{-j 2 \pi f_{c} t} + e^{j 2 \pi f_{c} t} }{2} $

##### However this method uses twice the bandwidth to transmit the same amount of information!

</br>

We can improve on this by using **complex-valued symbols** giving the **QAM signal**:

$$ \large
\begin{align*}
x(t) &= Re( \sqrt{2} \ x_{b}(t) \ e^{j 2\pi f_{c} t} ) \\
x(t) &= \sqrt{2} \sum_{k} p(t-kT) \ \Big( Re(X_{k}) \cos(2\pi f_{c} t) + Im(X_{k}) \sin(2\pi f_{c} t) \Big)
\end{align*}
$$

</br>

##### The carrier signals $ \cos(2\pi f_{c} t) $ and $ \sin(2\pi f_{c} t) = \cos(2\pi f_{c} t - \dfrac{\pi}{2}) $ are known as "in-phase" and "quadrature" components and hence QAM is also known as I-Q Modulation. 
##### $ \sqrt{2} $ is for making the carrier signals have unit power. 

</br>

## Constellations
$ M $ symbols ($ log_{2}M $ bits)

### M-PSK (Phase Shift Key)

$ M $ points on a circle (Constant Magnitude $ A $, Variable Phase)

$ E_{s} = A^{2} $

### M-QAM

$ M $ points equally spaced $ d $ in a square

$ E_{s} = \dfrac{40d^{2}}{16} = 2.5 d^{2} $







