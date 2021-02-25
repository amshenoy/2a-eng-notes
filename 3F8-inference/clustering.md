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
&= \small \sum_{k} p(\underline{x}_{n}, s_{n}=k| \theta) \\ \\
p(\underline{x}_{n} | \theta) &= \sum_{k}^{K} \pi_{k} \ \mathcal{N}(\underline{x}_{n}; \ \underline{m}_{k}, \Sigma_{k})
\end{align*}
$$

$$ \Large \color{blue}{ p(\underline{x}_{n} | \theta) = \sum_{k}^{K} \pi_{k} \ \mathcal{N}(\underline{x}_{n}; \ \underline{m}_{k}, \Sigma_{k}) } $$

## Likelihood

$$ \large \color{green}{
\log \big( p(\{x_{n}\}_{n=1}^{N}|\theta \big) = \log \big( 
 \prod_{n=1}^{N} p(x_{n}|\theta) \big) = \sum_{n=1}^{N} \log \ p(x_{n}|\theta)
} 
$$

$$ \therefore \log \big( p(\{x_{n}\}_{n=1}^{N}|\theta \big) = \sum_{n=1}^{N} \log \big( \ \sum_{k}^{K} \pi_{k} \ \mathcal{N}(\underline{x}_{n}; \ \underline{m}_{k}, \Sigma_{k}) \ \big)
$$

### Maximum Likelihood

$$ \large \theta_{ML} = \arg_{\theta} \max \enspace \log( p(\{x_{n}\}_{n=1}^{N}|\theta) ) $$

#### Possible Methods:
1) **Gradient Descent** &emsp; $ \theta_{new} = \theta_{old} + \alpha \dfrac{d}{d\theta} \log \big( p(\{x_{n}\}_{n=1}^{N}|\theta \big)  $

2) **Expectation Maximisation** Algorithm

</br> </br>

## Expectation Maximisation









</br> </br>

## Prediction

$$ \large p(s_{n} = k | \underline{x}_{n}, \theta_{ML}) $$








