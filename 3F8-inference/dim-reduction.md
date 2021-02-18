# Dimensionality Reduction

# Principal Component Analysis (PCA)

**Linear dimensionality reduction** method: Data manifold assumed to be linear.

</br>

Given a dataset $ \Large \mathcal{D} = \{\underline{x}_{i}\}_{i=1}^{N} $ with $ \large \sum_{i=1}^{N} \underline{x}_{i} = \underline{0} $ and using the **orthonormal basis** $ \{\underline{u}_{i}\}_{i=1}^{D} $ (aka **principal component vectors**): 

$$ \Large \underline{x}_{n} = \underbrace{\sum_{i=1}^{M} \underline{x}_{n}^{T} \ \underline{u}_{i} \underline{u}_{i} }_{\hat{x}_{n}} + \underbrace{\sum_{i=M+1}^{D} \underline{x}_{n}^{T} \ \underline{u}_{i} \underline{u}_{i} }_{ \epsilon_{n} } $$

$ \large \underline{x}_{n}^{T} \ \underline{u}_{i} $ - Principal component scores

PCA finds the **orthonormal basis** $ \{\underline{u}_{i}\}_{i=1}^{D} $ by **minimising the square reconstruction error**:

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


</br><hr></br>

### Method of Lagrange Multipliers &emsp; (Side Note)

This method allows us to **solve optimization problems with equality constraints**.

> Maximise $ f(\underline{x}) $ with the constraint $ g(\underline{x}) = c $ where $ c $ specifies contour line of $ g(x, y) $.

#### The solution should therefore satisfy: 

$$ \large \nabla f(\underline{x}) = - \lambda \nabla g(\underline{x}) \qquad g(\underline{x}) = c $$

where $ \lambda $ is the lagrangian multiplier.

</br>

The **Lagrangian function to maximise** is given by:

$$ L(\underline{x}, \lambda) = f(\underline{x}) + \lambda(g(\underline{x}) - c) $$

We need $ \nabla_{\underline{x}} L(\underline{x}, \lambda) = \underline{0} $ therefore satisfying $ \nabla f(\underline{x}) = - \lambda \nabla g(\underline{x}) $ and $ g(\underline{x}) = c $.

</br><hr></br>


## Cost Function

Since we require $ \underline{u}_{i}^{T} \underline{u}_{i} = 1 $ for $ i = 1, ..., D $, we can set this as our constraint $ g(\{\underline{u}_{i}\}_{i=1}^{D}) = \sum_{i=M+1}^{D} \underline{u}_{i}^{T} \underline{u}_{i} $.

We can then formulate the **Lagrangian** as follows:
$$
L(\ \{\underline{u}_{i}\}_{i=1}^{D} , \{\lambda_{i}\}_{i=1}^{D} \ ) = \sum_{i=M+1}^{D} \underline{u}_{i}^{T} C \underline{u}_{i} + \lambda_{i} (1 - \underline{u}_{i}^{T} \underline{u}_{i})\\
$$

The **optimal solution** is $ \large C \underline{u}_{i} = \lambda_{i} \underline{u}_{i} $ meaning that $ \underline{u}_{i} $ are the eigenvectors and $ \lambda_{i} $ are the eigenvalues of $ C $.


The cost function therefore simplifies to:

$$ \large 
\begin{align*}
Cost(\ \{\underline{u}_{i}\}_{i=1}^{D} \ ) &= \sum_{i=M+1}^{D} \underline{u}_{i}^{T} C \underline{u}_{i} \\
&= \sum_{i=M+1}^{D} \underline{u}_{i}^{T} \lambda_{i} \underline{u}_{i} \\
Cost(\ \{\underline{u}_{i}\}_{i=1}^{D} \ ) &= \sum_{i=M+1}^{D} \lambda_{i}
\end{align*}
$$

**The minimum of the cost function $ \sum_{i=M+1}^{D} \lambda_{i} $ gives the PCA solution.**

</br>

Therefore the PCA solution is given by $ \{\underline{u}_{i}\}_{i=1}^{D} $ such that:

$ \{\underline{u}_{i}\}_{i=M+1}^{D} $ eigenvectors of $ C $ have the $ D-M $ smallest eigenvalues.

$ \{\underline{u}_{i}\}_{i=1}^{M} $ eigenvectors of $ C $ have the $ M $ largest eigenvalues.

**Therefore, the PCA solution is also obtained by maximising $ \sum_{i=1}^{M} \lambda_{i} $, which is the same as maximising the square projected data**.


</br>

### M-Eigenvalue-Sum Maximisation

> How do we select $ M $?

We can **sort and plot eigenvalues** and pick the first $ M $ eigenvalues **beyond which there is an inflection point**.  








