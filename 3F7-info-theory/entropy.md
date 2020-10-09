# Entropy

$$ H(X) = \sum_{x} P(x) log \Big( \dfrac{1}{P(x)} \Big) $$

### Binary Entropy Function
$$ 
H_{2}(p) = p log(\dfrac{1}{p}) + (1-p)log(\dfrac{1}{1-p})
$$

## Properties of Entropy

### 1) $ H(X) \ge 0 $
### 2) $ H(X) \le log(M) $ where $ M $ is the alphabet size
### 3) Discrete Uniform Distribution with $ p = \dfrac{1}{M} $ has maximum entropy with a value of $ log(M) $

## Joint & Conditional Entropy

$$ H(X,Y) = \sum_{x,y} P_{XY}(x,y) log \Big(\dfrac{1}{P_{XY}(x,y)} \Big) 
$$
$$ H(Y|X) = \sum_{x,y} P_{XY}(x,y) log \Big(\dfrac{1}{P_{Y|X}(y|x))} \Big)
\\
= \sum_{x} P_{X}(x) \underbrace{ \sum_{y} P_{Y|X}(y|x) log \Big(\dfrac{1}{P_{Y|X}(y|x))} \Big) }_{\color{blue}{H(Y|X=x)}}
$$


</br>
$$ \color{red} { H(X,Y) = \sum_{x,y} P_{XY}(x,y) log \Big(\dfrac{1}{P_{XY}(x,y)} \Big) }
\\
= \sum_{x,y} P_{XY}(x,y) log \Big(\dfrac{1}{P_{Y|X}(y|x) P_{X}(x)} \Big)
\\
= \sum_{x,y} P_{XY}(x,y) \Bigg( log \Big(\dfrac{1}{P_{Y|X}(y|x)} \Big) + log \Big(\dfrac{1}{ P_{X}(x)} \Big) \Bigg)
$$
$$ \color{blue} { H(X,Y) = H(Y|X) + H(X) } $$
$$ \color{green} { P(X,Y) = P(Y|X) P(X) } $$


### Chain Rule of Joint Entropy
$$ \color{blue} { H(X_{1}, X_{2}, ..., X_{n}) = H(X_{1}) + H(X_{1}|X_{2}) + ... + H(X_{n}|X_{n-1}, ..., X_{1}) } 
\\
= \color{red} { \sum^{n}_{i=1} H(X_{i}|X_{i-1}, ..., X_{1}) }
$$

(Proof by analogous probability product rule)
$$ \color{green} { P(X_{1}, X_{2}, ..., X_{n}) = P(X_{1}) P(X_{1}|X_{2}) ... P(X_{n}|X_{n-1}, ..., X_{1}) }
\\ =  \color{purple} { \prod^{n}_{i=1} P(X_{i}|X_{i-1}, ..., X_{1}) }
$$

#### Independent Random Variables

$$ \color{blue} { H(X_{1}, X_{2}, ..., X_{n}) } = \color{red} { \sum^{n}_{i=1} H(X_{i}) }
$$

$$ \color{green} { P(X_{1}, X_{2}, ..., X_{n}) } = \color{purple} { \prod^{n}_{i=1} P(X_{i}) }
$$
