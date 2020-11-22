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
For any estimator $ \hat{X} $ such that $ X - Y - \hat{X} $:

$$ \large \hat{X}(Y) = \arg\max_{x \in \mathcal{X}} P_{X|Y}(x|Y) = \arg\max_{x \in \mathcal{X}} \dfrac{P_{XY}(x, Y)}{P_{Y}(Y)} $$ 

### Error Probability
For any estimator $ \hat{X} $ such that $ X - Y - \hat{X} $
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

We can generate $n$-bit codewords (**block length**) using a generator matrix that takes a $k$-bit input (**dimension**). For the purpose of this topic, we will consider vectors to be by **default row vectors**.

$$ \Large \color{purple}{ \underbrace{\underline{u}}_{\qquad 1 \times k \\ \text{Information Vector}} \underbrace{G}_{\qquad k \times n \\ \text{Generator Matrix}} = \underbrace{\underline{c}}_{\qquad 1 \times n \\ \text{Code Vector}} 
}
$$

$$ \large \sum_{i=1}^{N} u_{i} \underline{g}_{i} = \underline{c} $$

### Rate $ R = \dfrac{k}{n} $ bits per transmission

</br>

## Systematic Encoder

$$ \Large \color{blue}{ 
G_{sys} = [ \underbrace{I_{k}}_{ \qquad k \times k \\ \text{Identity Matrix}} | \quad \underbrace{P}_{k \times (n-k)} \quad ] 
} $$

#### Note: | is concatenation

This means we can actually derive the codeword $ \underline{c} $ by just concatenating the parity bits $ \underline{u} P $ to $ \underline{u} $:

$$ \Large \underline{c} = \underline{u} [ I_{k} | P ] = [ \underline{u} | \underline{u} P ]$$

Given a $ G $ matrix, we can find $ G_{sys} $ by **swapping columns** and performing **row operations** to create an identity matrix as required.

</br>

## Parity Check Matrix

Given $ G_{sys} $ we can find a parity check matrix $ H $:

$$ \Large \color{blue}{ G_{sys} = [I_{k} | P] \qquad \underbrace{H}_{(n-k) \times n} = [\underbrace{P_{T}}_{(n-k) \times k} \quad | \quad \underbrace{I_{n-k} }_{(n-k) \times (n-k)} ] 
} $$ 

</br>

If $ \underline{c} $ is a codeword, then:

$$ \Large \underline{c} H^{T} = \underline{0} $$

$$ \large \sum_{i=1}^{n} c_{i} \enspace \underline{\text{h}_{i}} = \underline{0} $$

**Note: Intuitively this means the sum of all the $i$-th columns $ \text{h}_{i} $ of $ H $ ( only $ c_{i} = 1 $ actually matters) must equal $ \underline{0} $**


Therefore $ (\underline{u} G) H^{T} = \mathcal{O} $ and therefore $ \large G H^{T} = [I_{k} | P] \begin{bmatrix}
           P \\
           I_{n-k}
         \end{bmatrix} = P + P = \mathcal{O} $





$ H $ works for $ G $ not just $ G_{sys} $ as codewords remain the same, only the mapping is different.

</br>

## Minimum Distance

**Hamming distance to count number of bit flips**

### $$ d_{\min} = \min_{i \ne j} d(c_{i}, c_{j}) $$

### $$ d_{min} = \text{Min no. of columns of H that sum to } \underline{0} $$

Atleast $ \large t $ errors can be corrected where $ t = \big\lfloor \dfrac{ d_{min} - 1 }{2} \big\rfloor $:

$$ \Large \color{blue}{ t \ge \big\lfloor \dfrac{ d_{min} - 1 }{2} \big\rfloor } $$


</br>

##### Note: For iterative decoding (ie. each error can be corrected with a single parity equation), we require a **sparse $H$** (ie. $ H $ has to be a LDPC matrix). So now we shift to LDPC matrices since we want iterative decoding for easy computation purposes.

</br> <hr>

# Low Density Parity Check (LDPC) Codes

LDPC matrix $ H $ is a $ (n-k) \times n $ parity check matrix as for BLC:
$$ \underline{c} H^{T} = \underline{0} $$

</br>

In a regular $ (n, k) $ **LDPC code**, the **parity check** matrix has the same weight (no. of 1s) for every row $ \large d_{c} $ and the same weight (no. of 1s) for every column $ \large d_{v} $.

For **irregular codes**, we need to specify the **weight distributions** on the columns and rows.

</br>

### If $ \color{green}{ \overline{d_{v}} } $ is the average weight of columns and $ \color{red}{ \overline{d_{c}} } $ is the average weight of rows:

### In any LDPC matrix, $ \text{ Total Number of Edges (No. of 1s) } \color{blue}{ N = \overline{d_{v}} n = \overline{d_{c}} (n − k) } $.

### Rate &emsp; $ \color{blue}{ R = \dfrac{k}{n} = 1 - \dfrac{\overline{d_{v}}}{\overline{d_{c}}} } $ bits per transmission

</br>

<font style="font-size: 18px;">Consider the **LDPC matrix** $ H_{ij} $ to be an **adjacency matrix** of a **bipartite graph** with $ \color{green}{ n \text{ variable}} $ nodes **column variables $ \large \color{green}{v_{j}} $** and $ \color{red}{ (n-k) \text{ check}} $ nodes (**row variables $ \large \color{red}{c_{i}} $**).</font>

</br></br>

## Degree Distributions

### Node Perspective
This is simple and intuitive, just take the **mean of the weights**. Using **weight fractions** $ Fv_{i} $ and $ Fc_{i} $ for each value of weight $ \large i $, we get the following:

$$ \large \color{blue}{
\overline{d_{v}} = \sum_{i \in \{d\}} i \ Fv_{i} 
}
= \dfrac{d}{dx} \Big( \sum_{i \in \{d\}} \ Fv_{i} \ x^{i} \Big)|_{x=1} = Fv^{'}(1) $$

$$ \large \color{blue}{ 
\overline{d_{c}} = \sum_{i \in \{d\}} i \ Fc_{i} 
}
= \dfrac{d}{dx} \Big( \sum_{i \in \{d\}} \ Fc_{i} \ x^{i} \Big)|_{x=1} = Fc^{'}(1) $$


### Edge Perspective

From the equation for **total number of edges** $ N = \overline{d_{v}} n = \overline{d_{c}} (n − k) $, we can derive the edge perspective equations.

$ \lambda_{i} $ &emsp; **Fraction of 1s in H** that are in **columns** of weight $ i $ </br> &emsp; &emsp; (**Fraction of total edges** connected to **variable nodes** with degree $ i $)

$ \rho_{i} $  &emsp; **Fraction of 1s in H** that are in **rows** of weight $ i $ </br> &emsp; &emsp; (**Fraction of total edges** connected to **check nodes** with degree $ i $)



$$ \large \color{blue}{ 
\overline{d_{v}} = \Big(\dfrac{n}{N}\Big)^{-1}
= \Big(\sum_{i \in \{d\}} \dfrac{\lambda_{i}}{i} \Big)^{-1} 
}
= \Big(\sum_{i \in \{d\}} \lambda_{i} \big(\int_{0}^{1} x^{i-1}\big) dx \Big)^{-1}
= \Bigg( \int_{0}^{1} \color{green}{\Big(\sum_{i \in \{d\}} \lambda_{i} x^{i-1} \Big)} dx \Bigg)^{-1}
= \Big(\int_{0}^{1} \color{green}{\lambda(x)} dx \Big)^{-1} $$

$$ \large \color{blue}{
\overline{d_{c}} = \Big(\dfrac{n-k}{N}\Big)^{-1}
= \Big(\sum_{i \in \{d\}} \dfrac{\rho_{i}}{i} \Big)^{-1}
}
= \Big(\sum_{i \in \{d\}} \rho_{i} \big(\int_{0}^{1} x^{i-1}\big) dx \Big)^{-1}
= \Bigg( \int_{0}^{1} \color{red}{\Big(\sum_{i \in \{d\}} \rho_{i} x^{i-1} \Big)} dx \Bigg)^{-1}
= \Big(\int_{0}^{1} \color{red}{\rho(x)} dx \Big)^{-1} $$
 

</br></br>

## Iterative Decoding as Message Passing



</br>

### Time Complexity

$ \mathcal{O}(N \cdot I ) $ where $ N $ is **total number of edges** and $ I $ is the **number of iterations**.  

Low number of 1s in H $ \longrightarrow $ Low complexity of decoder


</br>

## Density Evolution









