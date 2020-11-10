# Channel Coding

To add redundancy in the information sequence so that
the sequence can be recovered at the receiver even in the
presence of noise and interference.

### Block Code $(n, k)$ : &emsp; $k$ bits each transmitted $n$ times

### Rate $ R = \dfrac{k}{n} $ bits per transmission

### $ k $ bits $ \leftrightarrow 2^{k} = 2^{nR} $ messages 


# Joint Typicality


## Joint AEP


</br>

# Error Estimation

### Minimum Error Probability Estimator 
$$ \large \hat{X}(Y) = \arg\max_{x \in \mathcal{X}} P_{X|Y}(x|Y) = \arg\max_{x \in \mathcal{X}} \dfrac{P_{XY}(x, Y)}{P_{Y}(Y)} $$ 

### Error Probability
$$ \large 
\begin{align*}
P_{e} &= P( \hat{X}(Y) \ne X ) \\ &= \sum_{x} P( \hat{X}(Y) \ne X | X = x) P_{X}(x) \\ P_{e} &= \sum_{x} P( \hat{X}(Y) \ne X, X = x) \\
\end{align*}
$$ 


### Fano's Inequality
$$ \large P_{e} \ge \dfrac{H(X|Y)-1}{\log|\mathcal{X}|}$$ 


</br>

# AWGN Channel
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

# Binary Linear Codes

</br>

#### Minimum Distance of Code &emsp; $ \large d_{\min} = \min_{i \ne j} d(c_{i}, c_{j}) $ &emsp; (Hamming distance to count number of bit flips)

#### Linear Code &emsp; $ \underline{0} $ must be a codeword and for any codeword $ \underline{c} $, $ \underline{c} + \underline{c} $ must be a codeword.


