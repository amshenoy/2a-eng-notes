# Dimensionality Reduction

# Principal Component Analysis (PCA)

**Linear dimensionality reduction** method: Data manifold assumed to be linear.

**Objective**: Minimise square reconstruction error


Given a dataset $ \Large \mathcal{D} = \{\underline{x}_{i}\}_{i=1}^{N} $ with $ \large \sum_{i=1}^{N} \underline{x}_{i} = \underline{0} $ and using the **orthonormal basis** $ \{\underline{u}_{i}\}_{i=1}^{D} $ (aka **principal component vectors**): 

$$ \Large \underline{x}_{n} = \underbrace{\sum_{i=1}^{M} \underline{x}_{n}^{T} \ \underline{u}_{i} \underline{u}_{i} }_{\hat{x}_{n}} + \underbrace{\sum_{i=M+1}^{D} \underline{x}_{n}^{T} \ \underline{u}_{i} \underline{u}_{i} }_{ \epsilon_{n} } $$

$ \large \underline{x}_{n}^{T} \ \underline{u}_{i} $ - Principal component scores

PCA finds the **orthonormal basis** $ \{\underline{u}_{i}\}_{i=1}^{D} $ by minimising the square reconstruction error:

$$ \large
\begin{align*}
Cost(\ \{\underline{u}_{i}\}_{i=1}^{D} \ ) &= \dfrac{1}{N} \sum_{n=1}^{N} \epsilon_{n}^{T} \epsilon_{n} \\
\text{Simplifies to the following} \\
&= \sum_{i=M+1}^{D} \underline{u}_{i}^{T} ( \dfrac{1}{N} \sum_{n=1}^{N} \underline{x}_{n} \underline{x}_{n}^{T} ) \underline{u}_{i} \\
Cost(\ \{\underline{u}_{i}\}_{i=1}^{D} \ ) &= \sum_{i=M+1}^{D} \underline{u}_{i}^{T} C \underline{u}_{i} \\
\end{align*}
$$

$ C $ is the **covariance matrix** of the data.

#### We minimise subject to normalised unit basis vectors. This requires us to use the method of Lagrange multipliers!


</br>

### Method of Lagrange Multipliers

This method allows us to **solve optimization problems with equality constraints**.

> Maximise $ f(\underline{x}) $ with the constraint $ g(\underline{x}) = c $ where $ c $ specifies contour line of $ g(x, y) $.

#### The solution should therefore satisfy: 

$$ \nabla f(\underline{x}) = - \lambda \nabla g(\underline{x}) \qquad g(\underline{x}) = c $$















