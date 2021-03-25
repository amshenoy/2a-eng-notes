# Digital Controllers


## Encirclement Property

Using the frequency response , we can find some info about the zeros and poles of $F(z)$ (assuming none of the poles lie on the unit circle):

Define the following:
$ \text{NPIC} = \text{Number of Poles in Unit Circle} \\
\text{NZIC} = \text{Number of Zeros in Unit Circle} \\
\text{NPOC} = \text{Number of Poles out of Unit Circle} \\
\text{NZOC} = \text{Number of Zeros out of Unit Circle} $

$$ \text{No. of AC encirclements of the origin for } F(e^{j \theta}) \quad \theta = [0, 2\pi] = \text{NZIC } F(z) - \text{NPIC } F(z) $$

</br>

## Closed Loop Stability

### Open Loop
$ L = KG $

### Closed Loop

For a basic negative feedback loop: &emsp;  $ S = \dfrac{L}{1+L} = \dfrac{KG}{1+KG} $

#### Note: More specifically for a complicated negative feedback loop: &emsp; $ S = \dfrac{L_{\text{Line}}}{1+L_{\text{Circular}}} $

Therefore poles of closed loop are the roots of $ 1+KG = 0 $. Consider $ G(z) = \dfrac{Z(z)}{P(z)} $, therefore the poles of the closed-loop system is as follows:

$$ P(z) + K Z(z) = 0 $$

where $ P(z) $ are the poles and $ Z(z) $ are the zeros of the open loop system $ G $ and $ K $ is the controller.

</br>

## Nyquist Stability Criterion

An alternative expression considering $ 1+KG = 0 $ using the **encirclement property** definition:

$$
\begin{align*}
\text{No. of AC encirclements of } \dfrac{-1}{K} \text{ for } G(z) \\ \text{ from } \theta = [0, 2\pi] &= \text{NZIC } (1+KG) - \text{NPIC } (1+KG) \\ \\
&= \text{NPIC } \dfrac{KG}{1+KG} - \text{NPIC } (KG) \\
&= \text{NPIC Closed-Loop}  - \text{NPIC Open-Loop} \\ \\
& \text{As total number of poles for } KG \text{ and } \dfrac{KG}{1+KG} \text{ are the same: }\\ 
&= (N - \text{NPOC } \dfrac{KG}{1+KG} ) - (N - \text{NPOC } (KG) ) \\
&= - \text{NPOC } \dfrac{KG}{1+KG} + \text{NPOC } (KG) \\
&= - \text{NPOC Closed-Loop} + \text{NPOC Open-Loop} \\
\end{align*}
$$

</br>

Therefore for **stability of the closed-loop** system $ \text{NPOC Closed-Loop} = 0 $ and therefore:

### $$ \text{No. of AC encirclements of } \dfrac{-1}{K} \text{ for } G(z) \text{ must equal } \text{NPOC Open-Loop} $$

ie. must equal the number of unstable open-loop poles.


</br>

## Nyquist Diagram

### $ \theta $ is not the angle on the Nyquist plot!

If $ N $ poles on unit circle, the outer encirclement must rejoin after an angle $ - \dfrac{N \pi}{2} $.

Complete Nyquist plot must have symmetry.
