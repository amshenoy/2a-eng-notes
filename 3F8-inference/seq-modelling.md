# Sequence Modelling


## Markov Models

**1st Order Markov** - $ p(x_{1}, x_{2}, ..., x_{T}) = p(x_{1}) \ p(x_{2}|x_{1}) \ ... \ p(x_{T}| x_{T-1}) $

**2nd Order Markov** - $ p(x_{1}, x_{2}, ..., x_{T}) = p(x_{1}) \ p(x_{2}|x_{1}) \ p(x_{3}|x_{2}, x_{1}) \ ... \ p(x_{T}| x_{T-1}, x_{T-2}) $


</br></br><hr><hr></br></br>

## N-Gram (Discrete Markov) Model

**1-Gram (Unigram)** - $ P(x_{1}, x_{2}, ..., x_{T}) = \prod_{i=1}^{T} x_{i} $

</br>

**2-Gram (Bigram)** - $ P(x_{1}, x_{2}, ..., x_{T}) = P(x_{1}) P(x_{2}|x_{1}) \ ... \ P(x_{T}| x_{T-1}) $

**3-Gram (Trigram)** - $ P(x_{1}, x_{2}, ..., x_{T}) = P(x_{1}) P(x_{2}|x_{1}) P(x_{3}|x_{2}, x_{1}) \ ... \ P(x_{T}| x_{T-1}, x_{T-2}) $

</br> </br>

**The definitions are exactly the same as that of the Markov model except the following properties:**

</br>

**Discrete States** &emsp; $ \large \color{blue}{ x_{t} \in \{ 1, ..., K \} } $ states

**Initial State Probabilities** &emsp; $ \large \color{blue}{ P(x_{1} = k) = \pi_{k}^{0}  \qquad \qquad P( \ x_{1} \ ) = \underline{\pi}^{0} } $ </br>

**Transition Element (Bigram)** &emsp; $ \large \color{blue}{ P( \ x_{t}=k \ | \ x_{t-1}=l \ ) = T_{k,l} \qquad P( \ x_{t}\ | \ x_{t-1} \ ) = \mathbf{T} } $ </br>

</br> 

##### Instead of using $ T_{l,k} $ (the transition matrix that is conventionally used), we consider $ T_{k,l} $ (the transpose) so that we can use the conventional linear algebra techiques. The columns of $ T_{k,l} $ sum to 1 instead of the rows.


##### Note: **Transition Element (Trigram)** &emsp; $ \large P(x_{T}=k | x_{T-1}=l, x_{T-2}=m) = T_{k,l, m} $ </br>

</br> </br>

## Hidden Markov Model

> $ x_{t} $ is the **latent variable**, $ y_{t} $ is the **observed variable**. **HMM** uses a **mixture of Gaussians model** with **dynamic cluster assignments** given by an **underlying Markov model**.

**Emission Element (Bigram) &emsp; [Discrete]** &emsp;  $ \large \color{blue}{ P( \ y_{t}=m \ | \ x_{t}=k \ ) = S_{m,k} \qquad P( \ y_{t}\ | \ x_{t} \ ) = \mathbf{S} } $ </br>

**Emission Element (Bigram) &emsp; [Continuous]** &emsp;  $ \large \color{blue}{ P( \ y_{t} \ | \ x_{t}=k \ ) = \mathcal{N}(y_{t}, \mu_{k}, \sigma_{k}^{2}) } $ </br>

$$ \large P(y_{1:T}, x_{1:T}) = \prod_{t=1}^{T} P( \ x_{t}\ | \ x_{t-1} \ ) P( \ y_{t}\ | \ x_{t} \ ) $$

$$ P(y_{1}) = \sum_{k} \ P(x_{1}=k) \ P(y_{1}|x_{1}=k)  = \sum_{k} \ \pi_{k}^{0} \enspace \mathcal{N}(y_{t}, \mu_{k}, \sigma_{k}^{2}) \qquad \text{Mixture of Gaussians} $$



</br> </br>

### Examples

> $ P(x_{2} = k) = ? $, $ P(x_{t} = k) = ? $

$ \large P(x_{2} = k) = \sum_{l=1}^{K} P(x_{2}=k|x_{1}=l) P(x_{1}=l) = \sum_{l}^{K} T_{l, k} \ \pi_{l}^{0} = ( T \underline{\pi}^{0} )_{k}  $

$ \large P(x_{t} = k) = ( T^{t-1} \underline{\pi}^{0} )_{k} $

</br>

> **Stationary Distribution**

$ P(x_{t} = k) = \sum_{l=1}^{K} P(x_{T}=k | x_{T-1}=l) P(x_{t-1} = l) \\
\pi_{k}^{\infty} = \sum_{l=1}^{K} T_{l, k} \ \pi_{l}^{\infty}
$

**Actual Method:** $ \large (T-I) \pi^{\infty} = \underline{0} $

</br>

> **Which state diagram / transition matrix is most compatible given a sequence?**

**Create transition matrix of counts from the given sequence**, **divide by the total in each column**. This is the maximum likelihood estimate of the actual transition matrix.

$$ T_{kl} = \dfrac{N_{kl}}{\sum_{k} N_{kl}} \qquad N_{kl} = \text{Count}(x_{t}=k \cap x_{t-1}=l)$$

</br></br><hr><hr></br></br>

## AR Gaussian (Continuous Markov) Model

**Continuous Vector States** &emsp; $ \large \underline{x}_{t} \in \mathbb{R}^{D} $

**Initial State Density** &emsp; $ \large \color{blue}{ 
 p(\underline{x}_{1}) = \mathcal{N}(\underline{x}_{1}; \underline{m}_{0}, \Sigma_{0} ) } $

**Transition Density AR(1)** &emsp; $ \large \color{blue}{ 
 p(\underline{x}_{t} | \underline{x}_{t-1}) = \mathcal{N}(\underline{x}_{t}; \Lambda \underline{x}_{t-1}, \Sigma ) } $

This can be equivalently written as $ \large \color{blue}{ \underline{x}_{t} = \Lambda \underline{x}_{t-1} + \Sigma^{\frac{1}{2}} \underline{\epsilon}_{t} } $ where $ \large \color{blue}{  \underline{\epsilon}_{t} \sim \mathcal{N}(\underline{0}, I) } $.

</br>

> **In the 1D ($ D = 1 $) case:** </br></br>
$ \large \color{blue}{ 
 p(x_{t} | x_{t-1}) = \mathcal{N}(x_{t}; \ \lambda \ x_{t-1}, \ \sigma^{2} \ ) }  $ </br></br>
$ \large \color{blue}{ x_{t} = \lambda \ x_{t-1} + \sigma \epsilon_{t} \qquad \epsilon_{t} \sim \mathcal{N}(0, 1) 
 } $.
</br></br> **Note:** Conversely if $ \large \color{red}{ n_{t} \sim \mathcal{N}(\mu, \sigma^{2}) } $, we can write this as $ \large \color{red}{ n_{t} = \mu + \sigma \epsilon_{t} } $.
</br></br> 
If $ x_{t} = \lambda x_{t-1} + n_{t} $
</br></br> 
$ \therefore p(x_{t}|x_{t-1}) = \mathcal{N}(x_{t}; \ \lambda \ x_{t-1} + \mu, \ \sigma^{2} \ ) $
</br>


##### Note: $ \Sigma $ assumed not to be dependent on data!

##### Note: **Transition Density AR(2)** &emsp; $ p(\underline{x}_{t} | \underline{x}_{t-1}, \underline{x}_{t-2}) = \mathcal{N}(\underline{x}_{t}; \ \Lambda_{1} \underline{x}_{t-1} + \Lambda_{2} \underline{x}_{t-2}, \Sigma )  $

</br> </br>

### Examples

> **Stationary Distribution**

**The stationary distribution must be a Gaussian.**

$ \large p(\underline{x}_{\infty}) = \mathcal{N}(\underline{x}_{\infty}; \underline{m}_{\infty}, \Sigma_{\infty}) $


$ \underline{m}_{t} = E(\underline{x}_{t}) = E ( \Lambda \underline{x}_{t-1} + \Sigma^{\frac{1}{2}} \underline{\epsilon}_{t} ) = \Lambda E(\underline{x}_{t-1}) + \underline{0}  = \Lambda \ \underline{m}_{t-1} $

Therefore as $ t \rightarrow \infty $, $ \large \underline{m}_{\infty} = 0 $ for the above to hold true.


Similary for $ \Sigma_{\infty} $:

$ E(\underline{x}_{t}^{2}) = E ( (\Lambda \underline{x}_{t-1} + \Sigma^{\frac{1}{2}} \underline{\epsilon}_{t})^{2} ) = \Lambda^{2} E(\underline{x}_{t-1}^{2}) + 2 \underbrace{ E( (\Lambda \underline{x}_{t-1})^{T} \Sigma^{\frac{1}{2}} \underline{\epsilon}_{t} ) }_{=0} + \Sigma E(\underline{\epsilon}_{t}^{2}) = \Lambda^{2} E(\underline{x}_{t-1}^{2}) + \Sigma $

Since $ \underline{m}_{\infty} = 0 $,

$ \large \Sigma_{\infty} = E(\underline{x}_{\infty}^{2}) = (I-\Lambda^{2})^{-1} \Sigma $

##### Note: Methodology is same as 3F3 except in the continuous case, the stationary distribution parameters are calculated in the limit $ t \rightarrow \infty $.

</br> </br>




