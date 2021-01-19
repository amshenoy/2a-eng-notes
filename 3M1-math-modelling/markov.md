# Markov Processes

## Prerequisites

(Here consider column vectors as default)

Eigenvalues - $ det(A-\lambda_{i} I) = 0 $

Eigenvectors - $ (A-\lambda_{i} I) \underline{u}_{i}  = \underline{0} = \underline{u}_{i}^{T} (A^{T}-\lambda_{i} I) $

Eigenvalues of $ A $ and $ A^{T} $ are the same however eigenvectors are not!
 
To avoid confusion with $ P $ and $ P^{T} $, we will switch to using the row form of calculating these vectors using only $ P $.
   
</br>

# Discrete (Finite) State-Space

</br>

## Definitions

**Communicate** - Two states $ j $ and $ k $ communicate with each other if $ j \rightarrow k = m $ steps but $ k \rightarrow j = n $ steps.

**Irreducible** - All states communicate with each other. (Also **aperiodic** if irreducible)

**Recurrent state** if $ \sum P_{in} = 1 $ else **Transient state** ($ \sum P_{in} < 1 $)

**Recurrent Set** - Set of Recurrent States

**Aperiodic** - A state is not periodic if it can return to the same state in $ m $ and $ n $ states where $ m $ and $ n $ are coprime. (Periodic state eg. returns to the same state only in 2,4,6,8, etc. steps) 

**Aperiodic Chain** - All states of the chain are aperiodic.

</br>


## Expected Distribution after N steps

(Here consider row vectors as default)

</br>

$ \underline{x}_{0} $ - Initial Distribution (eg. $(1,0,0)$ if starting at the first node)
$$ \Large \underline{x}_{N} = \underline{x}_{0} \ P^{N} $$

### Find $\lambda_{i} $ by $ \det(P-\lambda_{i}) = 0 $ (ie. an eigenvalue of $P$ or $P^{T}$).

### Find $\underline{u}_{i} $ by $ \underline{u}_{i} (P-\lambda_{i}) = \underline{0} $ (ie. an eigenvector of $P^{T}$).

</br>

Simplify this by:

#### 1) Eigen-Decomposition

$ \Lambda $ - Diagonal Matrix of Eigenvalues

$ Q $ - Normalised Eigenvectors as Columns

$$ \Large \underline{x}_{N} = \underline{x}_{0} \ P^{N} = \underline{x}_{0} \ (Q \Lambda^{N} Q^{T}) $$


#### 2) Eigen-Summation

$ \underline{x}_{0} = \sum_{i} c_{i} \underline{u}_{i} $ as a linear combination of eigenvectors $ \underline{u}_{i} $ of $ P^{T} $ where $ c_{i} $ is found by inspection.

$$ \Large \underline{x}_{N} = \underline{x}_{0} \ P^{N} = \sum_{i} (c_{i} \underline{u}_{i}) \lambda_{i}^{N} $$

## Stationary Distribution 

**Expected Distribution after $ \infty $ steps**

A stationary distribution $ \pi $ exists if $ \lambda = 1 $ is an eigenvalue and all other $ \lambda \le 1 $ (ie. Markov process is **regular ergodic**).

$ \large \underline{x}_{\infty} = \pi P^{\infty} = c_{\lambda=1} \ \underline{u}_{\lambda=1} = \pi $ 

Alternatively equivalent to the corresponding eigenvector of $ P^{T} $ for $ \lambda = 1 $:

$ \large \pi P = \pi $

**Provided a stationary distribution exists** (**regular ergodic**, $\lambda = 1$): $ \Large \color{blue}{ \pi (P-I) = \underline{0} } $

The final distribution $ \pi $ must sum to 1, therefore divide by the sum of the row vector $ \pi $. 


</br>

## Waiting Time

Solve for $ \underline{q} $ where $ \underline{q}_{0} $ is $ \underline{q} $ with the value of the initial state being 0 $ q_{i} = 0 $:

$$ \large \color{blue}{ \underline{q} = P (\underline{1} + \underline{q}_{0}) } $$

Since $ P $ has rows summing to 1, $ P \ \underline{1} = \underline{1} $. Therefore we can simplify this equation further to:

$$ \color{blue}{ \underline{q} = \underline{1} + P \underline{q}_{0} } $$

$$ \Large \color{blue}{ \underline{q} - P \underline{q}_{0} = \underline{1} } $$

We can now solve for $ \underline{q} $.

</br>





</br><hr>

## Continuous Time, Discrete State-Space


### Birth-Death Process






</br><hr>

## Continuous State-Space


### Brownian Motion

#### Wiener Process


### Ornstein–Uhlenbeck Process

