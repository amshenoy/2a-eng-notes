# Random Variables

## Prerequisites

$$ \Omega \text{ is sample space (set containing all possibilities) } $$
$$ P \text{ is probability space (set containing the probabilities of  } \Omega \text{)} $$
$$ P(A \cap B) = P(A|B) P(B) = P(B|A) P(A) $$

$$ p(x) = \dfrac{d}{dx} F(x) $$

$$ F(x) = \int^{x}_{-\infty} p(x) dx $$

</br><hr>

## Function of a RV

### General Formula
If $ Y= R(X) $, then:
$$ p_{Y}(y) = p_{X}\Big(R^{-1}(y)\Big) \enspace \cdot \enspace \Bigg|\dfrac{d R^{-1}(y)}{dy}\Bigg| $$

which is the same as: 

$$ p_{Y}(y) = \dfrac{ p_{X}\Big(R^{-1}(y)\Big) } { \Bigg|\dfrac{d R(x)}{dx}\Bigg| } $$

Since the following is true:

$ \Bigg|\dfrac{d R(x)}{dx}\Bigg| = \Bigg|\dfrac{dy}{dx}\Bigg| \quad \text{ and } \quad \Bigg|\dfrac{d R^{-1}(y)}{dy}\Bigg| = \Bigg|\dfrac{dx}{dy}\Bigg| \qquad $ ie. $ y = R(x) \quad \therefore x = R^{-1}(y) $

##### Note*: The formula can be derived from $ \int p_{Y}(y) dy = \int p_{X}(x) dx $

### Multiple Inverse Functions
If the function R(X) has more than one inverse function then the formula is the the sum over all of the inverse functions.

eg. $ R(X) = |X| $ has inverse $ R^{-1}(Y) = \begin{cases}  1 \quad y \gt 0 \\ -1 \quad y \lt 0 \end{cases} $

$$ p_{Y}(y) = \sum^{K}_{k=1} \dfrac{ p_{X}\Big(x\Big) } { \Bigg|\dfrac{dy}{dx}\Bigg| } \Bigg|_{x = R^{-1}_{k}(y) } = \sum^{K}_{k=1} p_{X}\Big(x\Big) \enspace \Bigg|\dfrac{d x}{dy}\Bigg| \enspace \Bigg|_{x = R^{-1}_{k}(y) } $$

### Multivariate Case

Notice how the above formulas are all involving the differentials.
For the multivariate case, we simply need to use the **Jacobian**.



