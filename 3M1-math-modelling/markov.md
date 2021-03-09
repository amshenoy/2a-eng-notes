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

**Classes** - Markov chain nodes can be split into communicating sets called "classes" where a node is in the set if it communicates bidirectionally with every other node in the same set. (**Irreducible if only one class exists**)

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

$$ \Large \underline{x}_{N} = \underline{x}_{0} \ P^{N} = \underline{x}_{0} \ (Q \Lambda^{N} Q^{-1}) $$

#### Note that for a real and symmetric P, the eigenvectors for different eigenvalues are orthognal, ie. use $ Q \Lambda^{N} Q^{T} $.

</br>

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

### (Hitting Time / First Passage Time for Markov)

Solve for $ \underline{q} $ where $ \underline{q}_{0} $ is $ \underline{q} $ with the value of the end state (/an absorbing state) being 0 $ q_{e} = 0 $:

$$ \large \color{blue}{ \underline{q} = P (\underline{1} + \underline{q}_{0}) } $$

Since $ P $ has rows summing to 1, $ P \ \underline{1} = \underline{1} $. Therefore we can simplify this equation further to:

$$ \color{blue}{ \underline{q} = \underline{1} + P \underline{q}_{0} } $$

$$ \Large \color{blue}{ \underline{q} - P \underline{q}_{0} = \underline{1} } $$

We can now solve for $ \underline{q} $ by setting the vector as a series of variables with unknown values.

</br>

Above is also equivalent to:
$ \underline{h} = (I - P)^{-1} \underline{1} $

[Hitting Time](https://gtribello.github.io/mathNET/hitting-time-problems.html)



</br><hr>

# Continuous Time, Discrete State-Space


## Birth-Death Process

$$ \large \dfrac{d \underline{p}}{dt} = \underline{p} Q $$

$ \underline{p} $ - **Probability State Vector** (Infinite size) (**$ \underline{p} $ must sum to 1**)

$ Q $- **Transition Rate Matrix** (Infinite size) (**Rows of $ Q $ must sum to 0**)

</br>

**Steady State Distribution** $ \dfrac{d \underline{p}}{dt} = 0 \qquad \underline{p} \ Q = 0 $

(Get general expression by computing for each column and noticing general pattern)



##### Note: Links with 3F2


</br><hr>

# Continuous State-Space

## Random Walk
$ S_{k} \in \{-1, 1\} $ with uniform probability $ \frac{1}{2} $

Position after $ n $ steps, $ X_{n} = \sum_{k=1}^{n} S_{k} $

As $ N \rightarrow \infty $, $ X_{N} \sim \mathcal{N}(0, N) $.

Now taking a small step $ \delta $ in direction $ S_{k} $ every $\delta$ seconds; we get $ W_{t} \sim \mathcal{N}(0, \delta) = \mathcal{N}(0, t)$ and as $ \delta \rightarrow 0 $, this is Brownian motion (Wiener Process).

## Brownian Motion (Weiner Process)

### Extended Chapman-Kolmogorov Equation

$$ f(x, t+ \tau) = \int_{\infty}^{\infty} f(x+\Delta, t) p(-\Delta) d\Delta$$

Take Taylor series of $ f(x+\Delta, t) $, simplify, convert to $ f(x, t + \tau) - f(x, t) =  \dfrac{\partial f(x,t)}{\partial t} $ giving an expression for $ D = \dfrac{1}{2\tau} \int \Delta^{2} p(\Delta) d\Delta$

</br>

$$ \dfrac{\partial f(x,t)}{\partial t}  = D \dfrac{\partial^{2} f(x,t)}{\partial x^{2}} $$

### Drift Term

$$ \dfrac{\partial f(x,t)}{\partial t} = \color{green}{ m \dfrac{\partial f(x,t)}{\partial x} } + D \dfrac{\partial^{2} f(x,t)}{\partial x^{2}} $$



### Gaussianity

$ W_{t} $ is Gaussian with &emsp; $ E[ W_{t} ] = 0  \qquad E[ W_{t} W_{s} ] = 2D \min(t,s) $

### Continuity

$ W_{t} = W_{t-s} + W_{s} $ for $ t \ge s $ 

  
#### Note: Weiner process are **independent** and **continuous** in time, **stationary** and obey **gaussianity**. 
 
</br>

## Ornstein–Uhlenbeck Process

$$ \dfrac{\partial f(x,t)}{\partial t} = \color{green}{ m \dfrac{\partial 
 \ ( \ \color{red}{ x } f(x,t) \ ) }{\partial x} } + D \dfrac{\partial^{2} f(x,t)}{\partial x^{2}} $$


</br><hr></br>

## Markov Chain Monte Carlo (MCMC) Sampling Methods

### Importance Sampling

> We would like to sample from the distribution $ p(\underline{x}) $ but what if we can't sample $ p(\underline{x}) $ directly. Instead assume we can only generate samples $ \underline{x}_{i} $ from $ q(\underline{x}) $.

Let $ p(\underline{x}) = \dfrac{1}{Z_{p}} p^{*}(\underline{x}) $ and $ q(\underline{x}) = \dfrac{1}{Z_{q}} q^{*}(\underline{x}) $:

$$
\begin{align*}
E_{p}[ f(\underline{x}) ] &= \int f(\underline{x}) p(\underline{x}) \ d(\underline{x}) \\ &= \dfrac{ \int f(\underline{x}) p(\underline{x}) \ d(\underline{x}) } { \int p(\underline{x}) \ d(\underline{x}) } 
= \dfrac{ \int f(\underline{x}) \dfrac{p(\underline{x})}{q(\underline{x})} q(\underline{x}) \ d(\underline{x}) } { \int \dfrac{p(\underline{x})}{q(\underline{x})} q(\underline{x}) \ d(\underline{x}) } 
= \dfrac{ \int f(\underline{x}) \dfrac{p^{*}(\underline{x})}{q^{*}(\underline{x})} q(\underline{x}) \ d(\underline{x}) } { \int \dfrac{p^{*}(\underline{x})}{q^{*}(\underline{x})} q(\underline{x}) \ d(\underline{x}) }  \\
&= \dfrac{ E_{q}[ f(\underline{x}) \dfrac{p^{*}(\underline{x})}{q^{*}(\underline{x})} ] } { E_{q}[ \dfrac{p^{*}(\underline{x})}{q^{*}(\underline{x})} ] }  \\
&\approx \dfrac{ \dfrac{1}{N} \sum_{i=1}^{N} f(\underline{x}_{i}) 
 w_{i} }{ \dfrac{1}{N} \sum_{i=1}^{N} w_{i} } \qquad w_{i} = \dfrac{p^{*}(\underline{x}_{i})}{q^{*}(\underline{x}_{i})} \\
\end{align*}
$$


</br>

### Rejection Sampling

> We can sample a **probability distribution defined by constraints**, by **sampling using Monte-Carlo** and **rejecting samples that do not obey the constraints**.


</br>


### Metropolis Hastings

> Accept a new sample $ \underline{x}^{*} $ with probability $ \alpha $ else keep current sample $ \underline{x}_{i} $.

$ \large \underline{x}_{i+1} \leftarrow \begin{cases}
\underline{x}^{*}  \qquad \alpha = \min(\dfrac{p(\underline{x}^{*})} {p(\underline{x}_{i})}, 1) \\
\underline{x}_{i} \qquad \text{Otherwise}
\end{cases}
$


</br>

### Detailed Balance









