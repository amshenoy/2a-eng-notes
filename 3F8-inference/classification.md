# Classification

</br><hr></br>

# Binary Classification

</br>

## Introduction

### Deterministic Linear

**Binary Labels** &emsp; $ y_{n} \in \{0, 1\} $

$$ \large y_{n} = H(\underline{w}^{T}\underline{x}_{n})$$

However this does not allow for misclassification errors or for inference.

</br>

### Probabilistic Sigmoid

**Binary Labels** &emsp; $ y_{n} \in \{-1, 1\} $

$$ \large \begin{align*}
P(y_{n}|\underline{x}_{n}, \underline{w}) &= \dfrac{1+y_{n}}{2} \ \sigma(\underline{w}^{T}\underline{x}_{n}) + \dfrac{1-y_{n}}{2} \ (1-\sigma(\underline{w}^{T}\underline{x}_{n})) \\ \\
P(y_{n}|\underline{x}_{n}, \underline{w}) &= \sigma(y_{n} \ \underline{w}^{T}\underline{x}_{n})
\end{align*}
$$

</br>

# Logistic Regression

#### Note: We could use the **probit function** (Standard Normal CDF) $ \phi(x) $ instead of the **sigmoid/logistic** function $ \sigma(x) $.

#### Note: We could use non-linear functions $ g(\underline{x}) $  for non-linear logistic regression (as we did for non-linear linear regression). 

##### Note: "Non-linear (1) linear (2) regression" means (1 - Non-Linear Transformation of Inputs) and (2 - Linear Transformation of Outputs) 


</br>

### Logistic Function
$ \large \sigma(x) = \dfrac{1}{1+e^{-x}} $

**Properties:**

$ 1 - \sigma(x) = \sigma(-x) $

$ \large \color{green}{ \dfrac{d\sigma(x)}{dx} = \sigma(x)(1-\sigma(x)) } $

</br>

## Likelihood

For a given dataset $ \large \mathcal{D} = \{\underline{x}_{n}, y_{n}\}_{n=1}^{N}$, the likelihood is given by:

$$ \large \color{blue}{
L(\underline{w}) = \prod_{i} P(y_{i}|\underline{x}_{i}, \underline{w}) = \prod_{i} \sigma(y_{i} \ \underline{w}^{T}\underline{x}_{i})
}
$$

### Log-Likelihood

$$ \large \color{purple}{
\log(L(\underline{w})) = \sum_{i} \log(P(y_{i}|\underline{x}_{i}, \underline{w})) = \sum_{i} \log(\sigma(y_{i} \ \underline{w}^{T}\underline{x}_{i}))
}
$$

</br>

## Maximum Likelihood

Use $ \dfrac{d\sigma(x)}{dx} = \sigma(x)(1-\sigma(x)) $

$$ \large \color{purple}{
\dfrac{\partial \log(L(\underline{w}))}{\partial \underline{w}} = \sum_{i} \ y_{i}\ \underline{x}_{i} \enspace (1-\sigma(y_{i} \ \underline{w}^{T}\underline{x}_{i}) ) 
}
$$

##### Note: No closed form solution for ML but we can use numerical methods.

</br>

### Gradient Ascent

$$ \large \underline{w}_{new} = \underline{w}_{old} + \alpha \dfrac{\partial \log(L(\underline{w}))}{\partial \underline{w}} $$

$ \alpha $ - Learning rate

</br><hr></br>

# Multi Classification

### Deterministic 

$$ \large y_{n} = \arg_{k \in \{1, ..., K\}}\max \enspace \underline{w}_{k}^{T} \underline{x}_{n} $$

$ K $ - Number of classes

</br>

### Probabilistic
**Softmax function**

$$ \large P(y_{n}=c|\underline{x}_{n}, \underline{w}_{1}, ..., \underline{w}_{K} ) = \dfrac{\exp(\underline{w}_{c}^{T} \underline{x}_{n})}{\sum_{k=1}^{K} \exp(\underline{w}_{k}^{T} \underline{x}_{n}) }$$

$ K $ - Number of classes </br>
$ c $ - A specific class

#### Note: The softmax is equivalent to sigmoid for $ K = 2 $ (ie. binary classifier).



