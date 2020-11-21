# Channel Coding

To add redundancy in the information sequence so that
the sequence can be recovered at the receiver even in the
presence of noise and interference.

### Block Code $(n, k)$ : &emsp; $k$ bits each transmitted $n$ times

### Rate $ R = \dfrac{k}{n} $ bits per transmission

### $ k $ bits $ \leftrightarrow 2^{k} = 2^{nR} $ messages 

## Overview

We have take some information $ \underline{u} $, we turn it into some codeword $ \underline{c} $, transmit it over some channel (we consider discrete channels for binary problems but AWGN is given as a continuous channel example) to receive a possibly modified codeword $ \underline{y} $ due to noise and we need to decode this optimally to get an estimate of the original codeword $ \hat{\underline{c}}$. From this we can recover the estimated information $ \hat{\underline{u}} $.

$$ \Large \underline{u} \underbrace{\longrightarrow}_{\text{Codeword Encoding}} \underline{c} \underbrace{\longrightarrow}_{\text{Channel Transmission}} \underline{y} \underbrace{\longrightarrow}_{\text{Estimation}} \hat{\underline{c}} \underbrace{\longrightarrow}_{\text{Codeword Decoding}}  \hat{\underline{u}}  $$

__Note: The step from $ \underline{y} \longrightarrow \hat{\underline{u}} $ can be considered as a single decoding step.__

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

For any estimator $ \hat{X} $ such that $ X - Y - \hat{X} $, the $ P_{e} = P(\hat{X} \ne X) $ satisfies:
$$ \large P_{e} \ge \dfrac{H(X|Y)-1}{\log|\mathcal{X}|}$$ 


</br><hr>

# Optimal Codeword Estimation

For a received codeword $ \underline{y} $ and a block code $ \mathcal{B} $ consisting of codewords $ \underline{c}_{i} $, the optimally estimateed codeword $ \hat{\underline{c}} $ is given by:

$$ \Large \hat{\underline{c}} = \arg\max_{\underline{c} \in \{c_{0}, ..., \underline{c}_{m}\} } P(\underline{y}|\underline{c}) $$   

For a binary symmetric channel (BSC), this simplifies to the following:
$$ \Large \hat{\underline{c}} = \arg\min_{\underline{c} \in \{c_{0}, ..., \underline{c}_{m}\} } d(\underline{y}, \underline{c}) $$   

This is because for a BSC $ P(\underline{y}|\underline{c}) = (p)^{d(\underline{y}, \underline{c})} (1-p)^{n - d(\underline{y}, \underline{c})} = (1-p)^{n} (\dfrac{p}{1-p})^{d(\underline{y}, \underline{c})} $. Therefore to maximise the probability, we need $ d(\underline{y}, \underline{c}) $ to be as small as possible.

__Note: $ d(\underline{y}, \underline{c}) $ is the Hamming distance between the received codeword $ \underline{y} $ and the actual codeword $ \underline{c} $  (ie. The number of bits that are different or the number of bits that flipped during channel transmission).__
 
</br>

# Binary Linear Codes

</br>

#### Linear Code &emsp; $ \underline{0} $ must be a codeword and for any codeword $ \underline{c} $, $ \underline{c} \text{ XOR }  \underline{c} $ must be a codeword.

</br>

## Linear Coding (n, k)

We can generate $n$-bit codewords (**block length**) using a generator matrix that takes a $k$-bit input (**dimension**). For the purpose of this topic, we will consider vectors to be by default row vectors.

$$ \Large \color{purple}{ \underbrace{\underline{u}}_{\qquad 1 \times k \\ \text{Information Vector}} \underbrace{G}_{\qquad k \times n \\ \text{Generator Matrix}} = \underbrace{\underline{c}}_{\qquad 1 \times n \\ \text{Code Vector}} 
}
$$

### Rate $ R = \dfrac{k}{n} $ bits per transmission

</br>

### Systematic Encoder

$$ \Large \color{blue}{ 
G_{sys} = [ \underbrace{I_{k}}_{ \qquad k \times k \\ \text{Identity Matrix}} | \quad \underbrace{P}_{k \times (n-k)} \quad ] 
} $$

#### Note: | is concatenation

This means we can actually derive the codeword $ \underline{c} $ by just concatenating the parity bits $ \underline{u} P $ to $ \underline{u} $:

$$ \Large \underline{c} = \underline{u} [ I_{k} | P ] = [ \underline{u} | \underline{u} P ]$$

Given a $ G $ matrix, we can find $ G_{sys} $ by **swapping columns** and performing **row operations** to create an identity matrix as required.

</br>

### Parity Check Matrix

Given $ G_{sys} $ we can find a parity check matrix $ H $:

$$ \Large \color{blue}{ G_{sys} = [I_{k} | P] \qquad \underbrace{H}_{(n-k) \times n} = [\underbrace{P_{T}}_{(n-k) \times k} \quad | \quad \underbrace{I_{n-k} }_{(n-k) \times (n-k)} ] 
} $$ 

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







