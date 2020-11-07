# Digital Controllers


## Encirclement Property

Using the frequency response $ F(e^{j \theta}) $, we can find some info about the zeros and poles of $F(z)$ (assuming none of the poles lie on the unit circle):

$$ \text{Number of encirclements of the origin from } \theta = [0, 2\pi] = \text{Number of Zeros in unit circle} - \text{Number of Poles in unit circle} $$


## Closed Loop Stability

### Open Loop
$ L = KG $

### Closed Loop

For a basic negative feedback loop: &emsp;  $ S = \dfrac{L}{1+L} = \dfrac{KG}{1+KG} $

#### Note: More specifically for a complicated negative feedback loop: &emsp; $ S = \dfrac{L_{\text{Line}}}{1+L_{\text{Circular}}} $

Therefore poles of closed loop are the roots of $ 1+KG = 0 $. Consider $ G(z) = \dfrac{Z(z)}{P(z)} $, therefore the poles of the closed-loop system is as follows:

$$ P(z) + K Z(z) = 0 $$

where $ P(z) $ are the poles and $ Z(z) $ are the zeros of the open loop system $ G $ and $ K $ is the controller.


## Nyquist Stability Criterion



