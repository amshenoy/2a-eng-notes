# Signal Spaces

## Introduction

### Mapping Bits to Waveforms
Suppose we want to transmit $m$ bits in $T$ seconds using a waveform $x(t)$, meaning that we would have a set of $M = 2^{m}$ different functions for the different possible messages $ \{ S_{1}(t), ..., S_{M}(t)\}$.

Therefore, we need a systematic way to represent finite-energy functions.

By fixing a set of basis functions, signal waveforms can be represented as “vectors”.

### Vector Spaces

A set of linearly independent vectors $ \{ \underline{v}_{1}, ..., \underline{v}_{k} \}$, is a **basis** of the vector space $\mathcal{V}$, if any vector $ \underline{v} \in \mathcal{V} $ can be expressed as a linear combination of the basis vectors.

Dot product $\underline{v} \cdot \underline{v} $ = Inner product $ \langle \underline{v}, \underline{v} \rangle $

**Norm** $ ||\underline{v}|| = \sqrt{\langle \underline{v}, \underline{v} \rangle } $

</br>

## Signal Spaces

$$ \Large \text{Energy} \qquad  ||\underline{x}||^{2} = \langle \underline{x}, \underline{x} \rangle = \int_{-\infty}^{\infty} |x(t)|^{2} dt $$ 

$ \large \langle \underline{x}, \underline{y} \rangle = \int_{-\infty}^{\infty} x(t) y^{*}(t) dt  $


</br>

## Orthonormal Basis

(TBD)

</br>

### Gram-Schmidt Algorithm


(TBD)


</br>

## Discrete Representation

Any function $ x(t) $ can be represented as a linear combination of the **orthonormal basis ** functions $ f_{1}(t), ..., f_{k}(t) $ where $ k $ is the **dimension** of the space and $ x_{i} $ are the **projection coefficients**:

$$ \large x(t) = \sum_{i} x_{i} f_{i}(t) $$

We can now calculate the projection coefficients $ x_{j} $ by considering the projection of $ x(t) $ along $ f_{j}(t) $ (ie. the inner product):

$$ \large 
\begin{align*}
x_{j} &= \langle x(t), f_{j}(t) \rangle \\
&= \\
&= \\
&= \\
\end{align*}
$$ 

(TBD)








