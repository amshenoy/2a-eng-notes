# Markov Processes

## Prerequisites

(Here consider column vectors as default)

Eigenvalues - $ det(A-\lambda_{i} I) = 0 $

Eigenvectors - $ (A-\lambda_{i} I) \underline{u}_{i}  = \underline{0} = \underline{u}_{i}^{T} (A^{T}-\lambda_{i} I) $

Eigenvalues of $ A $ and $ A^{T} $ are the same however eigenvectors are not!
 
To avoid confusion with $ P $ and $ P^{T} $, we will switch to using the row form of calculating these vectors using only $ P $.
   
</br>

# Discrete (Finite) State-Space

(Here consider row vectors as default)
</br>

## Expected Distribution after N steps

$ \underline{x}_{0} $ - Initial Distribution (eg. $(1,0,0)$ if starting at the first node)
$$ \Large \underline{x}_{N} = \underline{x}_{0} \ P^{N} $$

### Find $\lambda_{i} $ by $ \det(P-\lambda_{i}) = 0 $ (ie. an eigenvalue of $P$ or $P^{T}$).

### Find $\underline{u}_{i} $ by $ \underline{u}_{i} (P-\lambda_{i}) = \underline{0} $ (ie. an eigenvector of $P^{T}$).


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

Provided a stationary distribution exists (**regular ergodic**, $\lambda = 1$): $ \Large \color{blue}{ \pi (P-I) = \underline{0} } $

The final distribution $ \pi $ must sum to 1, therefore divide by the sum of the row vector $ \pi $. 


</br><hr>

## Continuous Time, Discrete State-Space


### Birth-Death Process






</br><hr>

## Continuous State-Space


### Brownian Motion

#### Wiener Process


### Ornstein–Uhlenbeck Process

