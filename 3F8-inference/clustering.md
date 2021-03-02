# Clustering

Given a dataset $ \mathcal{D} = \{ \underline{x}_{n} \}_{n=1}^{N} $, we want to determine $ K $ classes to which these data points belong in by giving an output $ \{ s_{n} \}_{n=1}^{N} $ where $ s_{n} \in \{1, ..., K \} $ (a scalar representing the class in which the datapoint belongs).

##### Note that unlike classification, this is an unsupervised algorithm.


</br><hr></br>

# K-Means


### 1) Initialise 
Randomly initialise $ K $ mean vectors $ \{ \underline{m}_{k} \}_{k=1}^{K} $ of the same dimension as $ \underline{x}_{n} $.

</br>

### 2) Assignment
$$ \large s_{n} = \arg_{k}\min ||\underline{x}_{n} - \underline{m}_{k}|| $$

**For every data point, assign the datapoint to the cluster with the closest mean vector.**

</br>

### 3) Update

$$ \large m_{k} = \text{mean}(\underline{x}_{n} | s_{n} = k ) $$

**For every mean vector (centroid), compute the new mean as the mean of the assigned datapoints in that cluster.**

</br>

### 4) Repeat

**Repeat till convergence** ie. till the datapoint cluster assignments do not change $ \big( \{ s_{n} \}_{n=1}^{N} \big)_{t} = \big( \{ s_{n} \}_{n=1}^{N} \big)_{t-1} $.

</br>

## Limitations

- Strange results for different shapes of clusters
- Returns hard assignments
- Initialisation is delicate

 
</br><hr></br>

# Mixture of Gaussians Model

## Cluster Probability
> Probability of $ \underline{x}_{n} $ being in cluster $ k $
$$ \Large p(s_{n}=k | \theta) = \pi_{k} \qquad \big(\sum_{k=1}^{K} \pi_{k} = 1 \big) $$

## Datapoint Probability
> Probability of $ \underline{x}_{n} $ given that it is in cluster $ k $
$$ \Large p(\underline{x}_{n} | s_{n}=k, \theta) = \mathcal{N}(\underline{x}_{n}; \ \underline{m}_{k}, \Sigma_{k})$$ </br>
$ \large \theta $ - "Parameters" $ \large \{ \ \pi_{k}, \underline{m}_{k}, \Sigma_{k} \ \}_{k=1}^{K} $ </br>


</br>


$$ \large
\begin{align*}
p(\underline{x}_{n} | \theta) &= \sum_{k}^{K} \ p(\underline{x}_{n} | s_{n}=k, \theta) \ p(s_{n}=k | \theta) \\
&= \sum_{k}^{K} p(\underline{x}_{n}, s_{n}=k| \theta) \\ 
\end{align*}
$$

$$ \Large \color{blue}{ p(\underline{x}_{n} | \theta) = \sum_{k}^{K} \pi_{k} \ \mathcal{N}(\underline{x}_{n}; \ \underline{m}_{k}, \Sigma_{k}) } $$

## Likelihood

$$ \large \color{green}{
\log \big( p(\{\underline{x}_{n}\}_{n=1}^{N}|\theta \big) = \log \big( 
 \prod_{n=1}^{N} p(\underline{x}_{n}|\theta) \big) = \sum_{n=1}^{N} \log \ p(\underline{x}_{n}|\theta)
} 
$$

$$ \therefore \color{blue}{ \log \big( p(\{x_{n}\}_{n=1}^{N}|\theta \big) = \sum_{n=1}^{N} \log \big( \ \sum_{k}^{K} \pi_{k} \ \mathcal{N}(\underline{x}_{n}; \ \underline{m}_{k}, \Sigma_{k}) \ \big) }
$$

### Maximum Likelihood

$$ \large \color{blue}{ \theta_{ML} = \arg_{\theta} \max \enspace \log( p(\{x_{n}\}_{n=1}^{N}|\theta) ) } $$

#### Possible Methods:
1) **Gradient Descent** &emsp; $ \theta_{new} = \theta_{old} + \alpha \dfrac{d}{d\theta} \log \big( p(\{x_{n}\}_{n=1}^{N}|\theta \big)  $

2) **Expectation Maximisation** Algorithm

</br> </br>

## Expectation Maximisation

### Free Energy

For simplification of notation at this stage, consider $ X = \{\underline{x}_{n}\}_{n=1}^{N} $ and $ \underline{s} = \{s_{n}\}_{n=1}^{N} $ with $ q(\underline{s}) $ being an arbitrary distribution over $ S $:

$$
\begin{align*}
\color{green}{ \text{Free Energy} } &= \color{blue}{ \text{Log-Likelihood} } - \color{red}{ \text{KL-Divergence} }\\
\color{green}{ \mathcal{F}( q(\underline{s}), \theta ) } &= \color{blue}{ \log \Big( \ p(X|\theta) \ \Big) } - \color{red}{ \mathcal{KL}\Big( \ q(\underline{s}) \ || \ p(\underline{s} | X, \theta) \ \Big) } \\
&= \color{blue}{ \log \Big( \ p(X|\theta) \ \Big) } - \color{red}{ \sum_{\underline{s}} \ q(S) \log \Big( \ \dfrac{q(\underline{s})}{p(\underline{s} | X, \theta)} \ \Big) } \\ \\

&= \underbrace{\sum_{\underline{s}} \ q(\underline{s})}_{1} \log \Big( \ p(X|\theta) \ \Big) - \sum_{\underline{s}} \ q(\underline{s}) \log \Big( \ \dfrac{q(\underline{s})}{p(\underline{s} | X, \theta)} \ \Big) \\
&= \sum_{\underline{s}} \ q(\underline{s}) \log \Big( \ \dfrac{p(\underline{s} | X, \theta) \ p(X|\theta)}{q(\underline{s})} \ \Big) \\ \\
&= \sum_{\underline{s}} \ q(\underline{s}) \log \Big( \ \dfrac{p(X | \underline{s}, \theta) \ p(\underline{s}|\theta)}{q(\underline{s})} \ \Big) \\
&= \sum_{\underline{s}} \ q(\underline{s}) \log \Big( \ p(X | \underline{s}, \theta) \ p(\underline{s}|\theta) \ \Big) \ + \ \underbrace{ - \sum_{\underline{s}} q(\underline{s}) \log \Big( q(\underline{s}) \Big)}_{H(q(\underline{s}))} \\
&= \sum_{\underline{s}} \ q(\underline{s}) \log \Big( \ p(\underline{s}|\theta) \ p(X | \underline{s}, \theta) \ \Big) + H(q(\underline{s}))
\end{align*}
$$

## Algorithm

### 1) We can use an **iterative maximisation rule** starting with a random $ \theta_{0} $:

### 2) E Step

Here we maximise the free-energy $ \color{green}{ \mathcal{F}( q(\underline{s}), \theta ) } $ wrt $ q(\underline{s}) $ which is the equivalent of minimising the KL-Divergence term (use of Lagrange multiplier to prove) giving the denominator $ p(\underline{s} | X, \theta) $ as the optimum value.

$$ \large 
\begin{align*}
q_{t}(\underline{s}) &= \color{green}{ \arg_{q(\underline{s})}\max \  \mathcal{F}( q(\underline{s}), \theta ) } \\ \\
q_{t}(\underline{s}) &= p(\underline{s} | X, \theta_{t-1})
\end{align*}
$$

</br>

$$ \large 
\begin{align*}
q(s_{n} = k) &= p(s_{n} = k | \underline{x}_{n}, \theta) \\
&= \ \dfrac{p(s_{n}=k|\theta) \ p(\underline{x}_{n} | s_{n}=k, \theta) \ }{p(\underline{x}_{n}|\theta)} \\
&= \ \dfrac{p(s_{n}=k|\theta) \ p(\underline{x}_{n} | s_{n}=k, \theta) \ }{ \sum_{k} p(s_{n}=k|\theta) \ p(\underline{x}_{n} | s_{n}=k, \theta) \ } \\ \\
q(s_{n} = k) &= \dfrac{ \pi_{k} \ \mathcal{N}(\underline{x}_{n}; \ \underline{m}_{k}, \Sigma_{k}) }{\sum_{k} \pi_{k} \ \mathcal{N}(\underline{x}_{n}; \ \underline{m}_{k}, \Sigma_{k}) } \qquad ( = \dfrac{u_{nk}}{u_{n}} = \dfrac{u_{nk}}{\sum_{k} u_{nk}} )
\end{align*}
$$

#### Note: that $ q(s_{n} = k) $ can be denoted as "responsibility" &emsp; $ q(s_{n} = k) = r_{nk} = \dfrac{u_{nk}}{u_{n}} = \dfrac{u_{nk}}{\sum_{k} u_{nk}} $ where $ \large u_{nk} = \pi_{k} \ \mathcal{N}(\underline{x}_{n}; \ \underline{m}_{k}, \Sigma_{k}) $

</br>

### 3) M Step
Here we maximise the free energy $ \color{green}{ \mathcal{F}( q(\underline{s}), \theta ) } $ wrt $ \theta $.

We can ignore the entropy term $ H(q(\underline{s})) $ since it is independent of $ \theta $.

$$ \large
\begin{align*}
\theta_{t} &= \color{green}{ \arg_{\theta}\max \ \mathcal{F}( q(\underline{s}), \theta ) } \\
&= \arg_{\theta}\max \ \sum_{\underline{s}} \ 
q_{t}(\underline{s}) \log \Big( \ p(\underline{s}|\theta) \ \ p(X | \underline{s}, \theta) \ \Big) \\
\end{align*}
$$

</br>

$$ 
\begin{align*}
\mathcal{F}( q(\underline{s}), \theta ) &= \sum_{n}^{N} \sum_{k}^{K} q(s_{n}=k) \log \Big( \ p(s=k|\theta) \ p(\underline{x}_{n}|s=k, \theta) \ \Big) \\
&= \sum_{n}^{N} \sum_{k}^{K} q(s_{n}=k) \log \Big( \ \pi_{k} \ \ \mathcal{N}(\underline{x}_{n}; \ \underline{m}_{k}, \Sigma_{k}) \ \Big) \\
&= \sum_{n}^{N} \sum_{k}^{K} q(s_{n}=k) \Bigg( \log( \ \pi_{k} \ ) - \dfrac{1}{2} (\underline{x}_{n} - \underline{m}_{k})^{T} \ \Sigma_{k}^{-1} \ (\underline{x}_{n} - \underline{m}_{k}) \ + const. \Bigg) \\
\end{align*}
$$

We can work out the parameters $ \theta = \{ \pi_{k},  \underline{m}_{k}, \Sigma_{k} \}_{k=1}^{K} $ by partially differentiating wrt to each parameter and solving for the parameter.

$$
\begin{align*}
\dfrac{\partial \mathcal{F}}{\partial \underline{m}_{k}} = \sum_{n}^{N} q(s_{n}=k) \ \big( 2 \Sigma_{k}^{-1} (\underline{x}_{n} - \underline{m}_{k} ) \big) = 0
\\
\dfrac{\partial \mathcal{F}}{\partial \Sigma_{k}} = \sum_{n}^{N} q(s_{n}=k) \ \big( - \Sigma_{k}^{-T} \ (\underline{x}_{n} - \underline{m}_{k} ) (\underline{x}_{n} - \underline{m}_{k} )^{T}  \ \Sigma_{k}^{-T} \big) = 0
\\
\dfrac{\partial (\mathcal{F} + \lambda( 1 - \sum_{k} \pi_{k} ) )}{\partial \pi_{k}} = \sum_{n}^{N} \dfrac{q(s_{n}=k)}{\pi_{k}} - \lambda = 0 
\\
\end{align*}
$$

Note that after solving for $ \pi_{k} $, $ \lambda = \dfrac{1}{N} $ so that the constraint is fulfilled.

### 4) Repeat E-step and M-step till convergence

</br> </br>

## Prediction

$$ \large p(s_{n} = k | \underline{x}_{n}, \theta_{ML}) $$








