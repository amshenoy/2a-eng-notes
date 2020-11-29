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
 

</br></br>

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

Therefore to find the maximum $ \epsilon $ for which $ p_{t} \rightarrow 0 $ as $ t \rightarrow \infty $, we need to optimise $ R = 1 − \dfrac{\int \color{red}{\rho} } {\int \color{green}{\lambda} } $.

</br></br>

### Key Assumption
> Incoming messages at each node are independent

- Strictly true only if no cycles (loops) in the bipartite graph (graph is a tree).

- Practical LPDC code is almost never cycle-free but independence assumption is close enough for large $ n $ (as long as there are no short cycles).



