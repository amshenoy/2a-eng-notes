# Discrete Transforms 

## Discrete Fourier Transform (DFT) 
**Single DFT sample** generated from **two vectors**:

$$ \Large X_{n} = \sum_{k=0}^{N-1} x_{k} e^{-j \frac{2\pi}{N} n k} $$

$$ \Large X_{n}  = \underline{b_{N}(n)} \cdot \underline{x} $$

where $ \large  \underline{b_{N}(n)} = \begin{pmatrix}
           e^{-j\frac{2\pi}{N} \ (0) \ n} \\
           e^{-j\frac{2\pi}{N} \ (1) \ n} \\
           \vdots \\
           e^{-j\frac{2\pi}{N} \ (N-1) \ n}
         \end{pmatrix} = \begin{pmatrix}
           e^{-j\frac{2\pi}{N} \ (0)} \\
           e^{-j\frac{2\pi}{N} \ (1)} \\
           \vdots \\
           e^{-j\frac{2\pi}{N} \ (N-1)}
         \end{pmatrix}^{ \Large \circ n } = \underline{b_{N}}^{ \Large \circ n } $ using the Hadamdard power notation.

</br>

**DFT vector** of **N samples** generated from **matrix multiplication**:
$$ \Large \underline{X}  = B_{N} \ \underline{x} $$

$$ \large
\begin{align*}
\underline{X} = \begin{bmatrix}
           \underline{b_{N}^{T}(0)} \\
           \underline{b_{N}^{T}(1)}\\
           \vdots \\
           \underline{b_{N}^{T}(N-1)}
         \end{bmatrix} \underline{x}
\end{align*}
$$


## Inverse DFT
$$ \Large x_{k} = \dfrac{1}{N} \sum_{n=0}^{N-1} X_{n} e^{j \frac{2\pi}{N} k n} $$


$$ \Large \underline{x}  = \underbrace{B_{N}^{-1}}_{\frac{1}{N} B_{N}^{*}} \ \underline{X} $$

$$
\begin{align*}
\large x_{k} &= \frac{1}{N} \ \underline{b_{N}(n)}^{*} \cdot \underline{X}\\
&= \frac{1}{N} \ \underline{b_{N}(-n)} \cdot \underline{X}
\end{align*}
$$

</br>

## Properties

#### Linearity &emsp; If $ z_{k} = x_{k} + y_{k} $, then $ Z_{n} = X_{n} + Y_{n} $

#### Periodicity &emsp; $ X_{n} = X_{n+N} $

#### Symmetry &emsp; $ X_{n} = X_{n}^{*} = X_{N-n} $


#### Finite Sampling $ \omega = \dfrac{2 \pi}{NT}$  (Not a problem, any $ T $ can be selected)

#### Finite Horizon (Frequency distortion) Improvement as $ N \rightarrow \infty $


</br><hr>

## Circular Convolution

$$ \Large y_{m} = \text{IDFT}( \text{DFT}(g_{k}) \text{DFT}(x_{k}) ) = \text{IDFT}(G_{n} X_{n}) = \sum_{k=0}^{N-1} g_{k} \ x_{mod(m-k, N)} $$

</br>

If $ M \le m \le N $ for a given $ m $ where $ M = len(g_{k}) $ and $ N = len(x_{k})$, then **circular convolution equals standard convolution**:

$$ \Large y_{m} = \underbrace{\sum_{k=0}^{N-1} g_{k} \ x_{mod(m-k, N)}}_{\text{Circular Convolution}} = \underbrace{\sum_{k=0}^{M} g_{k} x_{m-k}}_{\text{Standard Convolution}}  $$



</br><hr>

## Fast Fourier Transform (FFT)

$$ \underline{X} = \text{FFT}(\underline{x}) $$

### Radix-2 Method

$$ X_{n} = \underline{b_{N}^{T}(n)} \underline{x} = \underline{b_{N/2}^{T}(n)} \Big( \underline{x_{A}} \color{red}{+} 
 (e^{-j \frac{2 \pi}{N}})^{n} \ \underline{x_{B}} \Big) $$

$$ X_{n+N/2} = \underline{b_{N}^{T}(n + N/2)} \underline{x} = \underline{b_{N/2}^{T}(n)} \Big( \underline{x_{A}} \color{red}{-} (e^{-j \frac{2 \pi}{N}})^{n} \ \underline{x_{B}} \Big) $$

where $ \underline{x_{A}} = [x_{i\%2 \ == \ 0}]^{T} $ and $ \underline{x_{B}} = [x_{i\%2 \ != \ 0}]^{T} $

In simple notation from above:
$$ X_{n} = \underline{b_{N}^{T}(n)} \underline{x} = A_{n} + W^{n} B_{n} $$

$$ X_{n+N/2} = \underline{b_{N}^{T}(n + N/2)} \underline{x} = A_{n} - W^{n} B_{n} $$



## Inverse FFT

$$ \underline{x} = \dfrac{1}{N} \text{FFT}(\underline{X}^{*})^{*} $$




</br>

### Time Complexity

DFT (N points): $ 2N^{2} $ (each DFT point requires 2N operations)

FFT (N points): $ \dfrac{3}{2} N \log_{2}(N) $
* $ N/2 $ products and $ N $ sum at each stage
* $ log_{2}(N) $ stages


</br><hr>
**Non/Basic-Examinable**
## Multi-Dimensional Variants

## 2D Z-Transform

$$ X_{z_{1}, z_{2}} = \sum_{k_{1}=0}^{\infty} \sum_{k_{2}=0}^{\infty} x(k_{1}, k_{2}) z_{1}^{-k_{1}} z_{2}^{-k_{2}} $$

## 2D Convolution
$$ x(k_{1}, k_{2})*y(k_{1}, k_{2}) = \sum_{k_{1}=0}^{\infty} \sum_{k_{2}=0}^{\infty} x(k_{1}, k_{2}) \ y(n_{1}-k_{1}, n_{2}-k_{2}) $$

### Z-Transform of Convolution
$$ X_{z_{1}, z_{2}} Y(z_{1}, z_{2}) = \mathcal{Z}\{ x(k_{1}, k_{2})*y(k_{1}, k_{2}) \}$$





