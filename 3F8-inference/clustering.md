# Clustering

Given a dataset $ \mathcal{D} = \{ \underline{x}_{n} \}_{n=1}^{N} $, we want to determine $ K $ classes to which these data points belong in by giving an output $ \{ s_{n} \}_{n=1}^{N} $ where $ s_{n} \in \{1, ..., K \} $ (a scalar representing the class in which the datapoint belongs).

##### Note that unlike classification, this is an unsupervised algorithm.


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

 
