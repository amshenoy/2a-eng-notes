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

</br><hr>

# Norms

$$ \Large L_{p} \text{ or } I_{p} \enspace \text{Norm} = \lVert x \rVert_{p} = \Big( \sum_{i=1}^{n} |x_{i}|^{p} \Big)^{\dfrac{1}{p}} $$

$ \Large \lVert x \rVert_{1} = \sum_{i}|x_{i}| $

$ \Large \lVert x \rVert_{2} = \sum_{i} x_{i}^{2} $

$ \Large \lVert x \rVert_{2}^{2} = \mathbf{x}^{\mathbf{H}}  \mathbf{x} \quad ( = \mathbf{x}^{*T} \ \mathbf{x} ) \qquad (  = \mathbf{x}^{T} \ \mathbf{x} \quad $ **if real** $ \quad  \Large ) $

$ \Large \lVert x \rVert_{\infty} = \max_{i}(x_{i}) $



$ \Large \lVert x \rVert_{\mathbf{A}} = \mathbf{x}^{\mathbf{H}} A \ \mathbf{x} $ &emsp; &emsp; (**Matrix Norm**) 

</br>

## Frobenius Norm


</br><hr>

# Least Squares Fitting

$$ \mathbf{A} \mathbf{x} = \mathbf{b} $$

## Pseudoinverse


</br><hr>

# Singular Value Decomposition






