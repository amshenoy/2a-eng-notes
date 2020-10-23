# Mutual Information

## Relative Entropy
Also known as KL-Divergence:
$$
D(P||Q) = \sum_{i}^{n} P(X_{i}) \log \Big(\dfrac{P(X_{i})}{Q(X_{i})} \Big)
$$


## Log-Likelihood Ratio (LLR)
Consider $P$, $Q$ are two pmfs defined on the same alphabet $ X_{i} $ where $ X_{i} $ is i.i.d generated according to either $P$ or $Q$:
$$ 
\begin{align*}
LLR(X_{1}, ..., X_{n}) &= \dfrac{1}{n} \log \Big(\dfrac{P(X_{1}, ..., X_{n})}{Q(X_{1}, ..., X_{n})} \Big) = \dfrac{1}{n} \sum_{i}^{n} \log \Big(\dfrac{P(X_{i})}{Q(X_{i})} \Big) \\ \\
&\overbrace{\approx}^{WLLN} E\Bigg(\log\Big(\dfrac{P(X_{i})}{Q(X_{i})} \Big) \Bigg) \\

\\ \\
&= \sum_{i}^{n} P(X_{i}) \log \Big(\dfrac{P(X_{i})}{Q(X_{i})} \Big) = D(P||Q) \qquad \text{If }X_{i}\text{ i.i.d according to P}
\\
= \sum_{i}^{n} Q(X_{i}) \log \Big(\dfrac{P(X_{i})}{Q(X_{i})} \Big) &= - \sum_{i}^{n} Q(X_{i}) \log \Big(\dfrac{Q(X_{i})}{P(X_{i})} \Big) = - D(Q||P) \qquad \text{If }X_{i}\text{ i.i.d according to Q}
\end{align*}

$$

</br>

## Mutual Information

### Entropy Properties
### $$
\begin{align*}
I(X; Y) &= I(Y; X) \\
&= H(X) - H(X|Y) \\
&= H(Y) - H(Y|X) \\
&= H(X) + H(Y) - H(X,Y) \\ \\
&= D(P_{XY}||P_{X}P_{Y}) \\

\end{align*}
$$

### Conditionality Switching
### $$
I(X; Y|Z) = I(X|Z; Y) \\
I(X; Y,Z) = I(X,Z; Y) 
$$

### Chain Rule

$$ I(\color{blue}{X_{1}, X_{2}, ..., X_{n}} | Y ) = \sum_{i}^{n} I(\color{red}{X_{i}|X_{i-1}, X_{i-2}, ..., X_{1}}; Y) $$

#### Proof

Let $ \color{blue}{A} = (\color{blue}{X_{1}, X_{2}, ..., X_{n}}) $, $ \color{red}{B} = (\color{red}{X_{i}| X_{i-1}, X_{i-2} ..., X_{1}}) $

Chain Rule for Entropy:
$
H(\color{blue}{A}) = \sum_{i}^{n} H(\color{red}{B}) \qquad H(\color{blue}{A}|Y) = \sum_{i}^{n} H(\color{red}{B}|Y)
$

</br>

$$ 
\begin{align*}
I(\color{blue}{A}; Y) &= H(\color{blue}{A}) - H(\color{blue}{A}|Y) \\
&= \sum_{i}^{n} H(\color{red}{B}) - \sum_{i}^{n} H(\color{red}{B}|Y) \\
&= \sum_{i}^{n} H(\color{red}{B}) - H(\color{red}{B}|Y) \\
\therefore I(\color{blue}{A}; Y) &= \sum_{i}^{n} I(\color{red}{B}; Y) \\

\end{align*}
$$

### Data Processing Inequality

Let three random variables $X, Y, Z$ for a Markov Chain $ X \rightarrow Y \rightarrow Z $ ie that the conditional distribution $ Z $ is dependent only on $Y$ and conditionally independent of $X$ (ie. $ P_{Z|Y} = P_{Z|XY} $) then the following is true:

### $$ I(X; Y) \ge I(X; Z) $$

Essentially means that any processing on $Y$ ($Z$) does not increase the information $Y$ contains about $X$.
