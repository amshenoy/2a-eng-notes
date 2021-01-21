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

$$ \Large \text{Energy} \qquad  ||\underline{x}||^{2} = \langle x(t), x(t) \rangle = \int_{-\infty}^{\infty} |x(t)|^{2} dt $$ 

$ \large \langle x(t), y(t) \rangle = \int_{-\infty}^{\infty} x(t) y^{*}(t) dt  $


</br>

## Orthonormal Basis

For a set of **orthonormal basis** functions $ f_{1}(t), ..., f_{k}(t) $, the following must be true:

1) (Must be a **basis**) Any function $ x(t) $ can be represented as a linear combination of the **orthonormal basis** functions $ f_{1}(t), ..., f_{k}(t) $ where $ k $ is the **dimension** of the space and $ x_{i} $ are the **projection coefficients**:

$$ \large x(t) = \sum_{i} x_{i} f_{i}(t) $$

2) (Must be **orthonormal**):

$$ \large \int_{-\infty}^{\infty} f_{i}(t) \ f_{j}^{*}(t) dt = \begin{cases}
1 \quad i = j \\
0 \quad i \ne j \\
\end{cases}
$$


</br>

### Gram-Schmidt Algorithm

Given a set of functions $ x_{1}(t), ..., x_{m}(t) $, we can find an orthonormal basis $ f_{1}(t), ..., f_{k}(t) $ using this algorithm:

$$
\begin{align*}
g_{1}(t) &= x_{1}(t) \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad
f_{1}(t) = \dfrac{g_{1}(t)}{||g_{1}(t)||} \\
g_{2}(t) &= x_{2}(t) - \langle x_{2}(t), f_{1}(t) \rangle f_{1}(t) \qquad \qquad \qquad \qquad \qquad \quad
f_{2}(t) = \dfrac{g_{2}(t)}{||g_{2}(t)||} \\
g_{3}(t) &= x_{3}(t) - \langle x_{3}(t), f_{2}(t) \rangle f_{2}(t) - \langle x_{3}(t), f_{1}(t) \rangle f_{1}(t) \qquad \ f_{3}(t) = \dfrac{g_{3}(t)}{||g_{3}(t)||}
\end{align*}
$$


#### Note: At each step, we try to find the part of $ x_{i}(t) $ which is not orthognal to the previous basis functions $ f_{1}(t), ..., f_{i-1}(t) $ and create a new basis function from the residual.

</br>

### Discrete Representation

Now for any $ x(t) $, we can calculate the **projection coefficients** $ x_{j} $ by considering the projection of $ x(t) $ along $ f_{j}(t) $ (ie. the inner product):

$$ \large 
\begin{align*}
x_{j} &= \langle x(t), f_{j}(t) \rangle \\
&= \int_{-\infty}^{\infty} x(t) f_{j}^{*}(t) dt \\
&= \int_{-\infty}^{\infty} \big( \sum_{i} x_{i} f_{i}(t) \big) \ f_{j}^{*}(t) dt \\
x_{j} &= \sum_{i} x_{i} \int_{-\infty}^{\infty} f_{i}(t) \ f_{j}^{*}(t) dt \quad (= x_{j} ) \\
\end{align*}
$$ 

Therefore we have now converted $ x(t) $ into a vector $ \underline{x} $.


Similarly we can derive the energy formulae in vector form as:

$$ \langle x(t), y(t) \rangle = \int_{-\infty}^{\infty} \big( \sum_{i} x_{i} f_{i}(t) \big) \ \big( \sum_{j} y_{j} f_{j}(t) \big)^{*} dt = \sum_{i} x_{i} y_{i}^{*} = \langle \underline{x}, \underline{y} \rangle $$

$ \langle x(t), x(t) \rangle = \sum_{i} |x_{i}|^{2} = \langle \underline{x}, \underline{x} \rangle$


