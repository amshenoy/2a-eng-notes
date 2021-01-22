# Linear Algebra



</br><hr>

## Hermitian Operator

Dot Product (Complex Case) &emsp; $ \large  \mathbf{x} \cdot \mathbf{y} = \mathbf{x}^{\mathbf{H}} \mathbf{y} = ( \mathbf{y}^{\mathbf{H}} \mathbf{x} )^{*}$

Note: In the complex case, $ \mathbf{x} \cdot \mathbf{y} \ne \mathbf{y} \cdot \mathbf{x} $

</br>

## Hermitian Matrix (H : 1)

$$ \large A^{\textbf{H}} = A $$

$ \large A^{*T} = A  $

Hermitian matrix has **real eigenvalues** and **orthognal eigenvectors** $ \mathbf{u_{i}}^{\mathbf{H}} \mathbf{u_{j}} = 0 $

### Symmetric Matrix (T : 1) [Real Case]

</br>

## Unitary Matrix (H : -1)

$$ \large U^{\mathbf{H}} = U^{-1} $$

$ \large U^{\mathbf{H}} U = I $

### Orthognal Matrix (T : -1) [Real Case]


</br>

## Positive Definite Matrix

**A positive definite matrix has all eigenvalues > 0 and must be Hermitian.**

$$ \Large Re( \ \underline{x}^{H} A \underline{x} \ ) > 0 \qquad \small( \text{ for all non-zero } \underline{x} ) $$

**Note: Semi-definite means $ \ge 0 $. Negative definite means $ < 0 $.**

In the **real case**, this simplifies to:
$$ \large \underline{x}^{T} A \underline{x} > 0 \qquad \small( \text{ for all non-zero } \underline{x} ) $$

</br>

A matrix $ M^{\mathbf{H}} M $ is always Hermitian since $ ( M^\mathbf{H} M )^{\mathbf{H}} = M^{\mathbf{H}} M $ and also always **positive semi-definite**.

</br>

## Rank
Rank of a matrix is the number of linearly independent rows or columns (the number is equal for either rows or columns).

$$ rank(A) \le \min(m, n) $$
 
**Full Rank** - $ rank(A) = \min(m, n) $

**Deficient Rank** - $ rank(A) < \min(m, n) $


</br><hr>

# Norms

Norms are used to measure how big a specific data structure is. Norms must be non-negative. 

$$ \Large L_{p} \enspace \text{Norm} = \lVert x \rVert_{p} = \Big( \sum_{i=1}^{n} |x_{i}|^{p} \Big)^{\dfrac{1}{p}} $$


$ \Large \lVert x \rVert_{1} = \sum_{i}|x_{i}| $

$ \Large \lVert x \rVert_{2} = \sum_{i} x_{i}^{2} $

$ \Large \lVert x \rVert_{2}^{2} = \mathbf{x}^{\mathbf{H}}  \mathbf{x} \quad ( = \mathbf{x}^{*T} \ \mathbf{x} ) \qquad (  = \mathbf{x}^{T} \ \mathbf{x} \quad $ **if real** $ \quad  \Large ) $

$ \Large \lVert x \rVert_{\infty} = \max_{i}(x_{i}) $

$ \Large \lVert x \rVert_{\mathbf{A}}^{2} = \mathbf{x}^{\mathbf{H}} A \ \mathbf{x} $ &emsp; &emsp; (**Matrix Norm** - A must be **positive definite** so that the norm is > 0) 

</br>

#### Triangle Inequality
$ \Large  \lVert x + y \rVert \le  \lVert x \rVert +  \lVert y \rVert $


</br>

## Operator Norm (Norm of a Matrix)

Measures the maximum amount $ A $ can rescale a vector $ \underline{x}$.

$$ \Large ||A|| = \max_{\underline{x} \in \mathbb{C}^{n}} \dfrac{||A\underline{x}||}{||x||} $$

Therefore $ \large ||A\underline{x}|| \le ||A|| \ ||\underline{x}|| $.

Similarly for matrices $ A $ and $ B $, $ \large ||AB|| \le ||A|| \ ||B|| $.

</br>

## Frobenius Norm

$$ \large ||A||_{F} = \sqrt{\sum_{i}\sum_{j} |a_{ij}|^{2}} $$


</br>

## Rotation Invariance
If $ Q $ is a **unitary matrix**:
  
$$ ||Qx||_{2} = ||x||_{2} $$
$$ ||QA||_{2} = ||A||_{2} $$

</br>

$$ ||QA||_{F} = ||A||_{F} $$


</br><hr></br>

# Error Bounding

## Condition Number

$$ \Large \kappa(A) = ||A|| \ ||A^{-1}|| $$

$ \large \kappa_{2}(A) = \sqrt{ \dfrac{\lambda_{max} \big( A^{H} A \big)}{\lambda_{min} \big( A^{H} A \big)} } \Big( = \dfrac{|\lambda_{max} \big( A \big)|}{|\lambda_{min} \big( A \big)|}  \small\text{ if } A \text{ is Hermitian } \large \Big)$

</br>

### 1) $ A (\underline{x} + \delta \underline{x}) = \underline{b} + \delta \underline{b} $

$ ||\underline{b}|| = ||A \underline{x}|| \qquad \le \qquad ||A|| \ ||\underline{x}||$ 

$ ||\delta \underline{x}|| = ||A^{-1} \delta \underline{b}|| \qquad \le \qquad ||A^{-1}|| \ ||\delta \underline{b}||$

$$ \large
\begin{align*}
\therefore \dfrac{||\delta \underline{x}||}{||\underline{x}||} &\le ||A|| \ ||A^{-1}|| \dfrac{||\delta \underline{b}||}{||\underline{b}||} \\
\dfrac{||\delta \underline{x}||}{||\underline{x}||} &= \kappa(A) \dfrac{||\delta \underline{b}||}{||\underline{b}||}
\end{align*}
$$

### 2) $ (A + \delta A) (\underline{x} + \delta \underline{x}) = \underline{b} $

$$ \therefore \dfrac{||\delta \underline{x}||}{||\underline{x} + \delta \underline{x}||} \le ||\delta A|| \ ||A^{-1}|| \quad = \quad \kappa(A) \dfrac{||\delta A|| }{||A||}
 $$





</br><hr></br>

# Least Squares Fitting

$$ \mathbf{A} \mathbf{x} = \mathbf{b} $$

## Pseudoinverse


</br><hr></br>

# Singular Value Decomposition






