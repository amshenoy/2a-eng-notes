# Channel Coding

To add redundancy in the information sequence so that
the sequence can be recovered at the receiver even in the
presence of noise and interference.

### Block Code $(n, k)$ : &emsp; $k$ bits each transmitted $n$ times

### Rate $ R = \dfrac{k}{n} $ bits per transmission

### $ k $ bits $ \leftrightarrow 2^{k} = 2^{nR} $ messages 


</br> <hr>

# Joint Typicality


## Joint AEP


</br> <hr>

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


</br><hr>

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

 
</br><hr>

# Binary Linear Codes

</br>

#### Linear Code &emsp; $ \underline{0} $ must be a codeword and for any codeword $ \underline{c} $, $ \underline{c} \text{ XOR }  \underline{c} $ must be a codeword.

</br>

## Linear Coding (n, k)

We can generate $n$-bit codewords (**block length**) using a generator matrix that takes a $k$-bit input (**dimension**). For the purpose of this topic, we will consider vectors to be by default row vectors.

$$ \Large \underbrace{\underline{u}}_{\qquad 1 \times k \\ \text{Information Vector}} \underbrace{G}_{\qquad k \times n \\ \text{Generator Matrix}} = \underbrace{\underline{c}}_{\qquad 1 \times n \\ \text{Code Vector}} $$

### Rate $ R = \dfrac{k}{n} $ bits per transmission

</br>

### Systematic Encoder

$$ \Large G_{sys} = [ \underbrace{I_{k}}_{ \qquad k \times k \\ \text{Identity Matrix}} | \quad \underbrace{P}_{k \times (n-k)} \quad ] $$

#### Note: | is concatenation

This means we can actually derive the codeword $ \underline{c} $ by just concatenating the parity bits $ \underline{u} P $ to $ \underline{u} $:

$$ \Large \underline{c} = \underline{u} [ I_{k} | P ] = [ \underline{u} | \underline{u} P ]$$

Given a $ G $ matrix, we can find $ G_{sys} $ by **swapping columns** and performing **row operations** to create an identity matrix as required.

</br>

### Parity Check Matrix

Given $ G_{sys} $ we can find a parity check matrix $ H $:

$$ \Large G_{sys} = [I_{k} | P] \qquad \underbrace{H}_{(n-k) \times n} = [\underbrace{P_{T}}_{(n-k) \times k} \quad | \quad \underbrace{I_{n-k} }_{(n-k) \times (n-k)} ]$$ 

</br>

If $ \underline{c} $ is a codeword, then:

$$ \Large \underline{c} H^{T} = \underline{0} \\
\sum_{i=1}^{n} c_{i} \enspace \underline{\text{h}_{i}} = \underline{0} 
 $$


**Note: Intuitively this means the sum of all the $i$-th columns $ \text{h}_{i} $ of $ H $ ( only $ c_{i} = 1 $ actually matters) must equal $ \underline{0} $**



$ H $ works for $ G $ not just $ G_{sys} $ as codewords remain the same, only the mapping is different.

</br>

### Minimum Distance

**Hamming distance to count number of bit flips**

### $$ d_{\min} = \min_{i \ne j} d(c_{i}, c_{j}) $$

### $$ d_{min} = \text{Min no. of columns of H that sum to } \underline{0} $$

Atleast $ \large t $ errors can be corrected where $ t = \big\lfloor \dfrac{ d_{min} - 1 }{2} \big\rfloor $:

$$ \Large \color{blue}{ t \ge \big\lfloor \dfrac{ d_{min} - 1 }{2} \big\rfloor } $$



</br> <hr>

# Low Density Parity Check (LDPC) Codes

In a regular $ (n, k) $ **LDPC code**, the **parity check** matrix has the same weight (no. of 1s) for every row $ \large d_{c} $ and the same weight (no. of 1s) for every column $ \large d_{v} $.

For **irregular codes**, we need to specify the **weight distributions** on the columns and rows.

If $ \overline{d_{v}} $ is the average weight of columns and $ \overline{d_{c}} $ is the average weight of rows:

### In any LDPC matrix, $ \text{ No. of 1s } = \overline{d_{v}} n = \overline{d_{c}} (n − k) $.

### Rate &emsp; $ R = \dfrac{k}{n} = 1 - \dfrac{\overline{d_{v}}}{\overline{d_{c}}} $ bits per transmission

</br>

<font style="font-size: 18px;">Consider the **LDPC matrix** $ H_{ij} $ to be an **adjacency matrix** of a **bipartite graph** with  **row variables $ \large c_{i} $** and **column variables $ \large v_{h} $**.</font>

</br>

## Degree Distributions

### Node Perspective


### Edge Perspective



</br>








