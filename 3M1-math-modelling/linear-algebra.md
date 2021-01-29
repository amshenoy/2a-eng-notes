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


### Note: Large $ \kappa(A) $ is bad since any error is amplified.


</br><hr></br>

# Least Squares Fitting

Consider $ A $ as a $ m \times n $ matrix:

$$ \Large \mathbf{A}^{H} \mathbf{A} \mathbf{x} = \mathbf{A}^{H} \mathbf{b} $$

This is derived by calculating $ \large r(\hat{\underline{x}}) = \min ||A \hat{\underline{x}} - \underline{b} ||_{2}^{2} $ by considering the **Gateaux derivative** to be equal to 0 (ie. minimise the residual):
$$ \dfrac{d \ r(\hat{\underline{x}} + \epsilon \underline{v})}{d \epsilon}|_{\epsilon=0} = 0$$




## Pseudoinverse (Moore-Penrose)
$$ \Large \mathbf{x} = ( \mathbf{A}^{H} \mathbf{A} )^{-1} \mathbf{A}^{H} \mathbf{b} = \mathbf{A}^{+} \mathbf{b} $$

$ A^{+} = ( A^{H} A )^{-1} A^{H} $ is the pseudoinverse of $ A $.

This is only valid when $ A $ is **full rank** (**columns are linearly independent**). 

- If $ m < n $, $ A^{+} = ( A^{H} A )^{-1} A^{H} $.
- If $ m > n $, $ A^{+} = A^{H} ( A A^{H} )^{-1} $.

#### Note: If $ A $ is not full rank, then there are multiple solutions to the least squares problem and cannot be done with this method.

</br><hr></br>

# Solving $ A x = b $

- Direct Methods (eg. LU Decomposition)
- Iterative Methods

</br>

## Power-Iteration (Iterative)

Writing $ \underline{x} $ as a linear combination of eigenvectors $ \underline{u}_{i} $ of $ A $:

$$ \underline{x} = \sum_{i} c_{i} \underline{u}_{i} $$

Then the following is true where $ \lambda_{i} $ are the eigenvalues of $ A $:

$$ \large A^{k} \underline{x} = \sum_{i} c_{i} \lambda_{i}^{k} \underline{u}_{i} $$

### Rayleigh Quotient

If we have an estimate of an eigenvector $ \underline{u} $ of $ A $, then we can estimate a corresponding eigenvalue $ \lambda^{*} $ by computing $ \min ||A\underline{u}-\lambda^{*}\underline{u} ||_{2}  $:

$$ \lambda^{*} = R(A, \underline{u}) = \dfrac{\underline{u}^{H}A\underline{u}}{\underline{u}^{H}\underline{u}}$$

#### Note: $ A $ must be Hermitian

</br></br>

## Stationary Methods (Iterative)

Split $ A $ into 2 matrices $ N$ and $ P $ giving $ A = N - P $:

Solve $ N \underline{x} = \underline{b} + P\underline{x} $ which can be solved by iteration in the following way for an estimate $ \underline{x}_{k} $:

$$ \large N \underline{x}_{k+1} = \underline{b} + P\underline{x}_{k} $$

### Methods
* Richardson &emsp; - &emsp; $ N = I $
* Jacobi &emsp; - &emsp; $ N = diag(A) $
* Gauss-Seidel &emsp; - &emsp; $ N = L(A) $ (Lower Triangular of A)

</br>

### Convergence

Consider the error $ \large \underline{e}_{k} = \underline{x}_{exact} - \underline{x}_{k} $ :

$$ \large
\begin{align*}
N \underline{e}_{k+1} &= P \underline{e}_{k} \\
\underline{e}_{k+1} &= N^{-1} P \underline{e}_{k} \\
\therefore \underline{e}_{k} &= ( N^{-1} P )^{k} \ \underline{e}_{0}
\end{align*}
$$

Now we can perform **power-iteration** on this simplified form.
We can **express $ \underline{e}_{0} $ as a linear combination of the eigenvectors $ \underline{u}_{i} $ of $ N^{-1} P $** :

$$ \large \underline{e}_{0} = \sum_{i} c_{i} \underline{u}_{i} $$

$$ \large \underline{e}_{k} = (N^{-1} P)^{k} \underline{e}_{0} = \sum_{i} c_{i} \lambda_{i}^{k} \underline{u}_{i} $$


### Convergence if &emsp; $ \large |\lambda \Big( N^{-1} P \Big)|_{max} < 1 $

#### Note: $ |\lambda|_{max} $ of a matrix is known as the *spectral radius*.



</br></br>

## Conjugate Gradient



</br>

</br><hr></br>

# Singular Value Decomposition






