# Discrete Memoryless Channels (DMC)

"The current output only depends on the current input."

**Diagram shows the $ P_{Y|X} $.**


## Channel Capacity
### $$ \color{blue}{ \mathcal{C} = \max_{P_{X}} I(X; Y) = \max_{P_{X}} H(Y) - H(Y|X) } $$

### $$ \text{The channel capacity } \mathcal{C} \text{ is the maximum transmission rate over the DMC } $$

### To find $\mathcal{C}$:

$$
\mathcal{C} = \max_{P_{X}} I(X; Y) = \max_{P_{X}} H(Y) - H(Y|X) \\
$$

#### 1) Assign probabilities $ \color{blue}{ P_{X} = ( \alpha, 1-\alpha ) } $ and find the probabilities of $ \color{blue}{ Y } $.

#### 2) $ \color{blue}{ H(Y|X) = \sum_{x \in \Chi} P_{X}(x) H(Y | X=x) } \qquad ( = \sum_{x \in \Chi} P_{X}(x) H_{2}(P(Y | X=x)) \text{ for a binary output Y }) $

#### 3) Find $ \color{blue}{H(Y)} \qquad ( = H_{2}(P_{Y}(0)) = H_{2}(P_{Y}(1)) \text{ for a binary output Y }) $ </br> $ \text{Use } \color{blue}{P(Y) = \sum_{x \in \Chi} P_{X}(x) P(Y | X=x)} $

#### 4) $ \color{blue}{ \text{ Maximise } I(X; Y) \text{ over } \alpha \quad \mathcal{C} = I(X; Y)(\alpha) \quad P_{X} = (\alpha, 1-\alpha) \text{ is the maximising input distribution.} } $ 


</br><hr>

### $ \color{green}{ \text{All channels can be expressed as a probability matrix } P_{Y|X} }$.

## Binary Symmetric Channel (BSC)

### $$ P(Y=\overline{x} | X=x) = p $$

(Insert Diagram Here)

$ p $ is the crossover (switching) probability.


### $$ \color{blue}{ \mathcal{C} = 1- H_{2}(p) } $$

### Repetition Code
(1, 3) - 1 bit is repeated 3 times

#### $ P(\text{decoding error}) = P( \text{errors} \ge 2 ) = 3C2 p^{2}(1-p) + 3C3 (1-p)^{3} $


</br>


## Cascade Channel

A **cascade channel** is just a series of **connected BSCs**.
A **cascade channgel** can be represented as a **single BSC with a crossover probability** given by:
$$ p_{c} = P(Y=1 | X=0) = P(Y=0 | X=1) = P(Y=\overline{x} | X=x) $$

The probability can be calculated by considering the different pathways to go from the corresponding $ X $ value to the corresponding $ Y $ value.

A set of $m$ BSC channels $$ CC_{m} = BSC(p_{c}) $$


<small> **Note: The actual $p_{c}$ for $ m $ BSCs is given by $ p_{c}(m) = \dfrac{1}{2}(1 - (1-2p)^{m}) $ however the derivation and analysis is outside the scope of this course. Can be proved by induction by considering m-1 attached to a single BSC.** </small>




</br>

## Binary Erasure Channel (BEC)

### $$ P_{Y|X} (y: P_{y|X}) = \{ 0: 1-\epsilon, \quad ?: \epsilon, \quad 1: 1-\epsilon \} $$

(Insert Diagram Here)

### $ P(Y=? | X=x) = \epsilon $


### $$ \mathcal{C} = 1 - \epsilon $$

</br>


## Z-Channel

## $ P_{Y|X} $ - Asymmetric Matrix (Diagram looks like a Z)



</br><hr>


# AWGN Channel (Continuous)

Additive White Gaussian Noise Channel

For a channel with input $X_{k}$, output $Y_{k}$ and gaussian noise $ Z_{k} = \mathcal{N}(0, \sigma^{2}) $:

#### Example Channel
$$ \Large Y_{k} = X_{k} + Z_{k} $$

Gaussian has the maximum possible differential entropy:

$$ \large \color{blue}{ h(Z) = \dfrac{1}{2} \log_{2} (2\pi e \sigma^{2}) } $$

$$ \large \color{blue}{ \large h(Y) \le \dfrac{1}{2} \log_{2} (2\pi e \ E(Y_{k}^{2})) } $$ 

### Power Constraint $ \color{blue}{ P = E(X_{k}^{2}) } $

#### Method of Calculation &emsp; $ E(Y_{k}^{2}) = E((X_{k}+Z_{k})^{2}) = E(X_{k}^{2})+E(Z_{k}^{2}) = P + \sigma^{2} $

## Channel Capacity

### For a general AWGN channel where $ \color{green}{ Y = f(X) + g(Z) } $:

$$
\begin{align*}
\mathcal{C} = \max I(X; Y) &= H(Y) - H(Y|X) = H(Y) - H(f(X)+g(Z)|X) \\
&= H(Y) - H(Z|X) \\
&= H(Y) - H(Z)
\end{align*}
$$

$ \large \color{blue}{ \text{SNR} = \dfrac{\text{Input Power}}{\text{Noise Power}} = \dfrac{E(f(X)^{2})}{E(g(Z)^{2})} } $
 
$$ \Large \color{blue}{
\mathcal{C} = h(Y) - h(Z) = \dfrac{1}{2} \log_{2} (1 + \text{SNR})
 \quad \small \text{bits / transmission} 
} $$

### A channel with bandwidth $ W $ has capacity $ C = 2W \mathcal{C} \quad \small \text{bits / sec} $.

</br>
 
</br><hr>



