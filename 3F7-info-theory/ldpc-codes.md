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

</br><hr></br>

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

$ \lambda_{i} $ &emsp; **Sum of 1s in columns of weight $ i$** / **Sum of 1s in H** </br>
&emsp; &emsp; **Fraction of 1s in H** that are in **columns** of weight $ i $ </br>
&emsp; &emsp; (**Fraction of total edges** connected to **variable nodes** with degree $ i $)

$ \rho_{i} $  &emsp; **Sum of 1s in rows of weight $ i$** / **Sum of 1s in H** </br>
&emsp; &emsp; **Fraction of 1s in H** that are in **rows** of weight $ i $ </br> &emsp; &emsp; (**Fraction of total edges** connected to **check nodes** with degree $ i $)



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
 

</br><hr></br>

## Iterative Decoding as Message Passing

Analogy of solving single equations of $ \underline{c} H^{T} = \underline{0} $ for BEC by passing messages between the two side of the bipartite graph.

</br>

### Time Complexity

$ \mathcal{O}(N \cdot I ) $ where $ N $ is **total number of edges** and $ I $ is the **number of iterations**.  

Low number of 1s in H $ \longrightarrow $ Low complexity of decoder


</br>

## Density Evolution

Density evolution is a technique to predict the decoding
performance of codes with a given $\lambda(x)$, $\rho(x)$ for large $n$.

Let $ p_{t} $ denote the probability that an outgoing $ v → c $ message is an erasure $ ? $ at step $ t $.

Let $ q_{t} $ denote the probability that an outgoing $ c → v $ message is an erasure $ ? $ at step $ t $.

For a BEC, $ p_{0} = \epsilon $ where $ \epsilon $ is the erasure probablity.

$ q_{0} = 1 $ as the first $ c → v $ messages are all
erasures.

</br>

### Regular Codes

Probability of the **variable and all $ d_{v} - 1 $ messages being erased**: &emsp; &emsp; $ \large p_{t} = \epsilon (q_{t-1})^{d_{v}-1} $

Probability of **atleast one of $ d_{c} - 1 $ messages being erased**: &emsp; &emsp; &emsp; $ \large q_{t} = (1 - (1-p_{t})^{d_{c}-1} )$

</br>

$$ \Large \therefore p_{t} = \epsilon (1 - (1-p_{t-1})^{d_{c}-1} )^{d_{v}-1} $$

#### This density evolution recursion predicts the fraction of erased bits at the end of each step $t$.

### We want to find the maximum $ \epsilon $ for which $ p_{t} \rightarrow 0 $ as $ t \rightarrow \infty $. For the BEC case, this threshold is found to be $ \epsilon_{MP} = 0.4294 $.

### Shannon Limit (max. possible $\epsilon$ for a given R) &emsp; $ \epsilon^{∗} = 1 − R $ &emsp; $ \epsilon^{∗}_{\max} = 0.5  \quad (R=0.5) $



</br>

### Irregular Codes

To get closer to the Shannon Limit, we use irregular codes as they provide more flexibility.

Probability of **outgoing message from a variable node with deg. $ i $ being erased**: &emsp; $ \large p_{t, i} = \epsilon (q_{t-1})^{i-1} $

Probability of **outgoing message from a check node with deg. $ i $ being erased**: &emsp; $ \large q_{t, i} = (1 - (1-p_{t})^{i-1} ) $


$$ \large p_{t} = \sum_{i} \lambda_{i} \ p_{t, i} = \epsilon \sum_{i} \lambda_{i} (q_{t-1})^{i-1} = \epsilon \ \color{green}{\lambda(}q_{t-1}\color{green}{)} $$

$$ \large q_{t} = \sum_{i} \rho_{i} \ q_{t, i} = \sum_{i} \rho_{i} \ (1 - (1-p_{t})^{i-1} ) = 1 - \color{red}{\rho(} 1 - p_{t} \color{red}{)} $$

</br>

$$ \Large p_{t} = \epsilon \ \color{green}{\lambda(}1 - \color{red}{\rho(} 1 - p_{t-1} \color{red}{)}\color{green}{)} $$

Therefore to find the maximum $ \epsilon $ for which $ p_{t} \rightarrow 0 $ as $ t \rightarrow \infty $, we need to optimise $ R = 1 − \dfrac{\int_{0}^{1} \color{red}{\rho(}x\color{red}{)} dx } {\int_{0}^{1} \color{green}{\lambda(}x\color{green}{)} dx } $.

</br></br>

### Key Assumption
> Incoming messages at each node are independent

- Strictly true only if no cycles (loops) in the bipartite graph (graph is a tree).

- Practical LPDC code is almost never cycle-free but independence assumption is close enough for large $ n $ (as long as there are no short cycles).


</br><hr></br>


# Application on Channels

## Optimal Decoding

### Blockwise Decoding
$$ \Large \hat{\underline{c}} = \arg_{\underline{c} \in \mathcal{C}} \max P(\underline{c} | \underline{y}) =  \underbrace{\arg_{\underline{c} \in \mathcal{C}} \max P(\underline{y} | \underline{c}) }_{ \small(\text{Provided that all codewords are equally likely (from Bayes)}) }$$

### Bitwise Decoding
$$ \Large \hat{c_{j}} = \arg_{c_{j} \in \{0,1\}} \max P(c_{j} | \underline{y}) $$

</br>

## Channels

### BEC
Solve $ \Large \hat{\underline{c}} H^{T} = \underline{0} $ where $ \Large \hat{\underline{c}} $ consists of variables for erasures.

### BSC
For a binary symmetric channel (BSC): 
$ \large \hat{\underline{c}} = \arg\min_{\underline{c} \in \{c_{0}, ..., \underline{c}_{m}\} } d(\underline{y}, \underline{c}) $

This is because for a BSC $ P(\underline{y}|\underline{c}) = (p)^{d(\underline{y}, \underline{c})} (1-p)^{n - d(\underline{y}, \underline{c})} = (1-p)^{n} (\dfrac{p}{1-p})^{d(\underline{y}, \underline{c})} $. Therefore to maximise the probability, we need $ d(\underline{y}, \underline{c}) $ to be as small as possible. $ p $ is the crossover probability and $ d(\underline{y}, \underline{c}) $ is the number of bits that have flipped.

### B-AWGN

$ Y = X + N $, where the input $ X \in \{+1, −1\} $ and $ N ∼ \mathcal{N}(0, \sigma^{2}) $ where $ \mathcal{N} $ is additive white Gaussian noise. Channel input generated from binary by mapping $ 0 \rightarrow X=+1 $ and $ 1 \rightarrow X=-1 $.


Optimal decoding in general tends to be unfeasible hence we use message pass decoding.

</br><hr></br>

# Message Pass Decoding

We focus on a message passing algorithm that approximately computes the desired bitwise a posteriori probabilities (APPs) &emsp; $ \large P(c_{j} = 0 | \underline{y}) $.

Index the **variable** nodes as $ j = 1, ..., n $ and **check** nodes as $ i= 1, ..., n-k $.

Consider belief propagation in **log-likelihood domain (LLR domain)**.

$$ \Large L_{ji} = \ln\Big( \dfrac{m_{ji}(0)}{m_{ji}(1)} \Big) \qquad L_{ij} = \ln\Big( \dfrac{m_{ij}(0)}{m_{ij}(1)} \Big) $$


$ m_{ji}(0) = 1 - m_{ji}(1) $ </br>
$ m_{ij}(0) = 1 - m_{ij}(1) $

</br>

## Channel Evidence
**Channel evidence $ \underline{y} $ is the given observation of the channel output.**

$ c_{j} $ is the output of the parity equation at check node $ j $. 
 
$$ L(y_{j}) = \ln \dfrac{P(c_{j}=0|y_{j})}{P(c_{j}=1|y_{j})} = \ln \dfrac{P(c_{j}=0) P(y_{j}|c_{j}=0)}{P(c_{j}=1) P(y_{j}|c_{j}=1)} = \ln \dfrac{P(y_{j}|c_{j}=0)}{P(y_{j}|c_{j}=1)} $$


$$ \Large \color{blue}{ L(y_{j}) = \ln \dfrac{P(y_{j}|c_{j}=0)}{P(y_{j}|c_{j}=1)} } $$


#### Note: $ P(y_{j} | c_{j} = x ) $ is simply from the channel matrix $ P_{Y|X}(y|x) $. 

</br></br>

## Variable-to-Check

$ m_{ji}(0) $ is an updated estimate of the posterior probability (or belief) that code bit $ c_{j} = 0 $.

$$ \Large m_{ji}(0) = \dfrac{a_{0}}{a_{0} + a_{1}}, \qquad m_{ji}(1) = \dfrac{a_{1}}{a_{0} + a_{1}}  $$

Application of Bayes' Rule $$ \Large a_{x} = P(c_{j}=x \ | \ y_{j}) P(c_{j}=x) = P(c_{j}=x \ | \ y_{j}) \prod_{i'\ne i} m_{i' j}(x) $$

### LLR Update

$$ \Large \color{blue}{ L_{ji} = L(y_{j}) + \sum_{i' \ne i} L_{i' j} } $$


</br></br>

## Check-to-Variable

$ m_{ij}(0) $ is an updated estimate of the probability that the
parity check equation $ i $ is satisfied when $ c_{j} = 0 $ (ie.
probability of an even number of ones to make $ c_{j} = 0 $ ).

$$ \Large m_{ij}(0) = \dfrac{1}{2} + \dfrac{1}{2} \prod_{j' \ne j }(1-2m_{j' i}(1)) $$

### LLR Update

$$ \Large \color{blue}{ \tanh( \dfrac{1}{2} L_{ij} ) = \prod_{j' \ne j} \tanh( \dfrac{1}{2} L_{j' i} ) } $$


#### Practical Computation
$ \Large \color{red}{ L_{j' i} = ( \underline{h_{i}} \circ L(\underline{y}) )_{j'} = \underline{h_{i}}_{j'} L(y_{j'}) } $

where $ \underline{h_{i}}_{j'} $ is the $ j' $-th element of the parity vector $ \underline{h_{i}} $ in row $ i $ of the matrix $ H $.


</br></br>

## Termination Rule

$$ \Large L_{j} = L(y_{j}) + \sum_{i'} L_{i' j} $$

where the sum in this final stage is over all the checks $ i' $ connected to code bit $ j $.

$$ \large
\hat{c_{j}} = \begin{cases}
0 \qquad L_{j} \ge 0 \\
1 \qquad L_{j} < 0
\end{cases}
$$







