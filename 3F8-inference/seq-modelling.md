# Sequence Modelling


## Markov Models

**1st Order Markov** - $ p(y_{1}, y_{2}, ..., y_{T}) = p(y_{1}) \ p(y_{2}|y_{1}) \ ... \ p(y_{T}| y_{T-1}) $

**2nd Order Markov** - $ p(y_{1}, y_{2}, ..., y_{T}) = p(y_{1}) \ p(y_{2}|y_{1}) \ p(y_{3}|y_{2}, y_{1}) \ ... \ p(y_{T}| y_{T-1}, y_{T-2}) $


</br><hr></br>

## N-Gram (Discrete Markov) Model

**1-Gram (Unigram)** - $ P(y_{1}, y_{2}, ..., y_{T}) = \prod_{i=1}^{T} y_{i} $

</br>

**2-Gram (Bigram)** - $ P(y_{1}, y_{2}, ..., y_{T}) = P(y_{1}) P(y_{2}|y_{1}) \ ... \ P(y_{T}| y_{T-1}) $

**3-Gram (Trigram)** - $ P(y_{1}, y_{2}, ..., y_{T}) = P(y_{1}) P(y_{2}|y_{1}) P(y_{3}|y_{2}, y_{1}) \ ... \ P(y_{T}| y_{T-1}, y_{T-2}) $

</br> </br>

**The definitions are exactly the same as that of the Markov model except the following properties:**

</br>

**Discrete States** &emsp; $ \large y_{t} \in \{ 1, ..., K \} $ states

**Initial State Probabilities** &emsp; $ \large P(y_{1} = k) = \pi_{k}^{0} $ </br>

**Transition Element (Bigram)** &emsp; $ \large P(y_{T}=k | y_{T-1}=l) = T_{k,l} $ </br>

</br>

#### Instead of using $ T_{l,k} $ (the transition matrix that is conventionally used), we consider $ T_{k,l} $ (the transpose) so that we can use the conventional linear algebra techiques. The columns of $ T_{k,l} $ sum to 1 instead of the rows.


##### Note: **Transition Element (Trigram)** &emsp; $ \large P(y_{T}=k | y_{T-1}=l, y_{T-2}=m) = T_{k,l, m} $ </br>


</br> </br>

### Examples

> $ P(y_{2} = k) = ? $, $ P(y_{t} = k) = ? $

$ \large P(y_{2} = k) = \sum_{l=1}^{K} P(y_{2}=k|y_{1}=l) P(y_{1}=l) = \sum_{l}^{K} T_{l, k} \ \pi_{l}^{0} = ( T \underline{\pi}^{0} )_{k}  $

$ \large P(y_{t} = k) = ( T^{t-1} \underline{\pi}^{0} )_{k} $

> **Stationary Distribution**

$ P(y_{t} = k) = \sum_{l=1}^{K} P(y_{T}=k | y_{T-1}=l) P(y_{t-1} = l) \\
\pi_{k}^{\infty} = \sum_{l=1}^{K} T_{l, k} \ \pi_{l}^{\infty}
$

**Actual Method:** $ \large (T-I) \pi^{\infty} = \underline{0} $

> **Which state diagram / transition matrix is most compatible given a sequence?**

**Create transition matrix of counts from the given sequence**, **divide by the total in each column**. This is the maximum likelihood estimate of the actual transition matrix.


</br><hr></br>

## AR Gaussian (Continuous Markov) Model

**Continuous Vector States** &emsp; $ \large \underline{y}_{t} \in \mathbb{R}^{D} $

**Initial State Density** &emsp; $ \large p(\underline{y}_{1}) = \mathcal{N}(\underline{y}_{1}; \underline{m}_{0}, \Sigma_{0} ) $

**Transition Density AR(1)** &emsp; $ \large p(\underline{y}_{t} | \underline{y}_{t-1}) = \mathcal{N}(\underline{y}_{t}; \Lambda \underline{y}_{t-1}, \Sigma )  $

This can be equivalently written as $ \large \color{blue}{ \underline{y}_{t} = \Lambda \underline{y}_{t-1} + \Sigma^{\frac{1}{2}} \underline{\epsilon}_{t} } $ where $ \large \color{blue}{  \underline{\epsilon}_{t} \sim \mathcal{N}(\underline{0}, I) } $.

In the 1D ($ D = 1 $) case, $ y_{t} = \mu \ y_{t-1} + \sigma \epsilon_{t} $ where $ \epsilon_{t} \sim \mathcal{N}(0, 1) $.

</br>

##### Note: $ \Sigma $ assumed not to be dependent on data!

##### Note: **Transition Density AR(2)** &emsp; $ p(\underline{y}_{t} | \underline{y}_{t-1}, \underline{y}_{t-2}) = \mathcal{N}(\underline{y}_{t}; \ \Lambda_{1} \underline{y}_{t-1} + \Lambda_{2} \underline{y}_{t-2}, \Sigma )  $

</br> </br>

### Examples

> **Stationary Distribution**

**The stationary distribution must be a Gaussian.**

$ \large p(\underline{y}_{\infty}) = \mathcal{N}(\underline{y}_{\infty}; \underline{m}_{\infty}, \Sigma_{\infty}) $


$ \underline{m}_{t} = E(\underline{y}_{t}) = E ( \Lambda \underline{y}_{t-1} + \Sigma^{\frac{1}{2}} \underline{\epsilon}_{t} ) = \Lambda E(\underline{y}_{t-1}) + \underline{0}  = \Lambda \ \underline{m}_{t-1} $

Therefore as $ t \rightarrow \infty $, $ \large \underline{m}_{\infty} = 0 $ for the above to hold true.


Similary for $ \Sigma_{\infty} $:

$ E(\underline{y}_{t}^{2}) = E ( (\Lambda \underline{y}_{t-1} + \Sigma^{\frac{1}{2}} \underline{\epsilon}_{t})^{2} ) = \Lambda^{2} E(\underline{y}_{t-1}^{2}) + 2 \underbrace{ E( (\Lambda \underline{y}_{t-1})^{T} \Sigma^{\frac{1}{2}} \underline{\epsilon}_{t} ) }_{=0} + \Sigma E(\underline{\epsilon}_{t}^{2}) = \Lambda^{2} E(\underline{y}_{t-1}^{2}) + \Sigma $

Since $ \underline{m}_{\infty} = 0 $,

$ \large \Sigma_{\infty} = E(\underline{y}_{\infty}^{2}) = (I-\Lambda^{2})^{-1} \Sigma $










