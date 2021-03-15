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

**Transition Element** &emsp; $ \large \color{blue}{ P( \ x_{t}=k \ | \ x_{t-1}=l \ ) = T_{k,l} \qquad P( \ x_{t}\ | \ x_{t-1} \ ) = \mathbf{T} } $ </br>

</br> 

##### Instead of using $ T_{l,k} $ (the transition matrix that is conventionally used), we consider $ T_{k,l} $ (the transpose) so that we can use the conventional linear algebra techiques. The columns of $ T_{k,l} $ sum to 1 instead of the rows.


##### Note: **Transition Element (Trigram)** &emsp; $ \large P(x_{T}=k | x_{T-1}=l, x_{T-2}=m) = T_{k,l, m} $ </br>

</br> </br>

## Discrete Hidden State Model [DHSM] &emsp; (Discrete HMM)

> $ x_{t} $ is the **discrete latent variable**, $ y_{t} $ is the **discrete/continuous observed variable**. </br> </br>
**HMM** uses a **mixture of Gaussians model** with **dynamic cluster assignments** given by an **underlying Markov model**.

**Emission Element &emsp; [Discrete]** &emsp;  $ \large \color{blue}{ P( \ y_{t}=m \ | \ x_{t}=k \ ) = S_{m,k} \qquad P( \ y_{t}\ | \ x_{t} \ ) = \mathbf{S} } $ </br>

**Emission Element &emsp; [Continuous]** &emsp;  $ \large \color{blue}{ P( \ y_{t} \ | \ x_{t}=k \ ) = \mathcal{N}(y_{t}, \mu_{k}, \sigma_{k}^{2}) } $ </br>

$$ \large P(y_{1:T}, x_{1:T}) = \prod_{t=1}^{T} P( \ x_{t}\ | \ x_{t-1} \ ) P( \ y_{t}\ | \ x_{t} \ ) $$

$$ P(y_{1}) = \sum_{k} \ P(x_{1}=k) \ P(y_{1}|x_{1}=k)  = \sum_{k} \ \pi_{k}^{0} \enspace \mathcal{N}(y_{t}, \mu_{k}, \sigma_{k}^{2}) \qquad \text{Mixture of Gaussians} $$



</br><hr></br>

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

## Linear Gaussian State-Space Model [LGSSM] &emsp; (Continuous HMM)

> $ x_{t} $ is the **continuous latent variable**, $ y_{t} $ is the **continuous observed variable**. </br>

**Emission Density &emsp; [Continuous]** &emsp;  $ \large \color{blue}{ p( \ \underline{y}_{t} \ | \ \underline{x}_{t} \ ) = \mathcal{N}(\underline{y}_{t}, C \underline{x}_{t}, Q ) } $ </br>






</br><hr></br>

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

</br></br><hr><hr></br></br>

# HMM Inference

> Various methods of learning parameters $ \theta $ where the **posterior depends on the purpose**.

## Posterior Table
$$ 
\begin{array}{|c|c|c|}
\hline
  \text{Purpose} & \text{Marginal (Sample)} & \text{Joint (Sequence)} \\ 
\hline
   \text{Online ("Predicting") [Filter]} & p(\underline{x}_{t}|\underline{y}_{1:t}) & p(\underline{x}_{1:t}|\underline{y}_{1:t})  \\
\hline
   \text{Batch/Offline ("Learning") [Smoother]} & p(\underline{x}_{t}|\underline{y}_{1:T}) & p(\underline{x}_{1:T}|\underline{y}_{1:T}) \\
\hline
\end{array}
$$

</br>

## Maximum a Posteriori (MAP)

</br>

#### Most Probable Sample
$ \large \underline{x}_{t}^{*} = \arg_{\underline{x}_{t}}\max p( \ \underline{x}_{t} \ | \ \underline{y}_{1:T} \ ) $

#### Most Probable Sequence
$ \large \underline{x}_{1:T}^{*} = \arg_{\underline{x}_{1:T}}\max p( \ \underline{x}_{1:T} \ | \ \underline{y}_{1:T} \ ) $

</br>

### LGSSM - Sample and Sequence estimates are the same (Mean $ = $ Mode)

### DHSM - Sample and Sequence estimates are not the same (Mean $ \ne $ Mode)

</br> </br>

## Kalman Filter

> Online recursive sample prediction

</br>

### Step 1 - Prediction

$$ \large
\begin{align*}
\color{blue}{ p( \ \underline{x}_{t} \ | \ \underline{y}_{1:t-1} ) }
&= \int \color{red}{ p( \ \underline{x}_{t} \ | \ \underline{x}_{t-1}, \ \underline{y}_{1:t-1} \ ) } \ \color{green}{ p( \ \underline{x}_{t-1} \ | \ \underline{y}_{1:t-1} ) } \ d\underline{x}_{t-1} \\

&= \int \color{green}{ p( \ \underline{x}_{t-1} \ | \ \underline{y}_{1:t-1} ) } \ \color{red}{ \underbrace{ p( \ \underline{x}_{t} \ | \ \underline{x}_{t-1} \ ) }_{\text{Transition}} } \ d\underline{x}_{t-1} \\

\end{align*}
$$

</br> </br>

### Step 2 - Posterior

$$
\large \begin{align*}
\color{green}{ p( \ \underline{x}_{t} \ | \ \underline{y}_{1:t} ) }

&= p( \ \underline{x}_{t} \ | \ \underline{y}_{t} , \  \underline{y}_{1:t-1} ) \\

&= \dfrac{  \color{orange}{  p( \ \underline{y}_{t} \ | \ \underline{x}_{t} , \ \underline{y}_{1:t-1} )  } \ \color{blue}{ p( \ \underline{x}_{t} \ | \ \underline{y}_{1:t-1} ) }  } { p( \ \underline{y}_{t} \ | \ \underline{y}_{1:t-1} ) } \\ \\

&= \dfrac{\color{blue}{ p( \ \underline{x}_{t} \ | \ \underline{y}_{1:t-1} ) } \ \color{orange}{ \overbrace{ p( \ \underline{y}_{t} \ | \ \underline{x}_{t} \ ) }^{\text{Emission}} } } { p( \ \underline{y}_{t} \ | \ \underline{y}_{1:t-1} ) } \\ \\

\color{green}{ p( \ \underline{x}_{t} \ | \ \underline{y}_{1:t} ) } &\propto \color{blue}{ p( \ \underline{x}_{t} \ | \ \underline{y}_{1:t-1} ) } \ \color{orange}{ \underbrace{ p( \ \underline{y}_{t} \ | \ \underline{x}_{t} \ ) }_{\text{Emission}} } 

\end{align*}
$$

Let:
- $ \color{blue}{ p( \ \underline{x}_{t} \ | \ \underline{y}_{1:t-1} ) } =  \color{blue}{ \mathcal{N}(\underline{x}_{t}, \underline{\mu}_{t}^{t-1}, V_{t}^{t-1}) } $ where $ \underline{\mu}_{t}^{t-1} = \Lambda \underline{\mu}_{t-1}^{t-1} $ and $ V_{t}^{t-1} = \Lambda V_{t-1}^{t-1} \Lambda^{T} + \Sigma $ where $ \Lambda $ and $ \Sigma $ are from the **AR(1) transition density** $ \color{blue}{ 
 p(\underline{x}_{t} | \underline{x}_{t-1}) = \mathcal{N}(\underline{x}_{t}; \Lambda \underline{x}_{t-1}, \Sigma ) } $.

- $ \color{green}{ p( \ \underline{x}_{t} \ | \ \underline{y}_{1:t} ) } =  \color{green}{ \mathcal{N}(\underline{x}_{t}, \underline{\mu}_{t}^{t}, V_{t}^{t}) } $:



