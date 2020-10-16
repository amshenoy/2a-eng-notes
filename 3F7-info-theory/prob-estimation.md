# Probability Estimation

## Tail Probabilities
Markov and Chebyshev inequalities are ways to bound tail
probabilities with limited information about the random variable.
* **Markov** is for **non-negative** rvs and requires only $ mean (\mu) $ 
* **Chebyshev** is for **general** rvs, and requires $ mean (\mu) $ and $ variance (\sigma^{2}) $

### Markov Inequality

### $$ 
\text{For a non-negative rv X and any a > 0:} \\
\color{blue} { P(X \ge a) \le \dfrac{E[X]}{a} }
\\
\small\text{(Only useful for a > E[x] as otherwise RHS is greater than 1 which is an obvious statement)}
$$

### Chebyshev Inequality

### $$ 
\color{blue} { P\Big(\big| X - E[X] \big| \ge a \Big) \le \dfrac{Var[X]}{a^{2}} }
$$
**Chebyshev** can be directly **derived from Markov** as follows:
$$
P\Big(\color{orange}{\big| X - E[X] \big|} \ge \color{orange}{a} \Big) = P\Big( \color{red}{\big| X - E[X] \big|^{2} } \ge \color{red}{ a^{2} } \Big)
\\
\text{ Let } \color{blue}{Y} = \color{red}{\big| X - E[X] \big|^{2} }
\\
\text{By Markov's Inequality: } \qquad
\color{blue} { P(Y \ge a^{2}) \le \dfrac{E[Y]}{a^{2}} } \qquad
E[\color{blue}{Y}] = E\Big[ \color{red}{ \big| X - E[X] \big|^{2} } \Big] = Var[X]
$$
#### Full Summary
$$
P\Big(\color{orange}{\big| X - E[X] \big|} \ge \color{orange}{a} \Big) = P\Big( \color{red}{\big| X - E[X] \big|^{2} } \ge \color{red}{ a^{2} } \Big) = P(\color{blue} {Y} \ge \color{red} {a^{2}}) \quad \le \quad \dfrac{E[\color{blue} {Y}]}{\color{red} {a^{2}}}  \quad = \dfrac{Var[\color{red} {X}]}{\color{red} {a^{2}}} 
$$

## Weak Law of Large Numbers (WLLN)

$ \color{blue}{\text{'Empirical average converges to the mean'}} $
</br>
**Let $ X_{1}, X{2}, ..., X_{n} $ be a sequence of i.i.d rvs with finite mean $ \mu $ and let $ S_{n} = \dfrac{1}{n} \sum_{i}^{n} X_{i} $:**
$$
\text{Informal Statement of WLLN:} \color{blue}{ \qquad S_{n} \rightarrow \mu \qquad \text{ as } \quad n \rightarrow \infty }
\\
\text{Formal Statement of WLLN:} \qquad
\text{For any } \color{blue}{ \epsilon > 0
\qquad \lim_{n \rightarrow \infty} P\Big( | S_{n} - \mu | \ge \epsilon \Big) = 0 }
$$

</br>
Proof using Chebyshev's Inequality:
$$

\qquad \lim_{n \rightarrow \infty} P\Big( | S_{n} - \mu | \ge \epsilon \Big) \le \dfrac{\color{red}{Var(S_{n})}}{\epsilon^{2}} = \dfrac{\color{red}{\sigma^{2}}}{\color{red}{n} \epsilon^{2}}
\\
\text{For } \epsilon > 0, \text{ as } n \rightarrow \infty, \dfrac{\color{red}{\sigma^{2}}}{\color{red}{n} \epsilon^{2}} \rightarrow 0
\\
\text{Therefore WLLN is true!}
$$

</br>

## Typicality

### A typical sequence for a random variable $ X $ has probability $ \color{blue}{ p_{T} = 2^{-n H(X)} } $ 

A typical set $ \mathcal{A}_{\epsilon, n} $ is therefore defined as the set of sequences $ (x_{1}, ..., x_{n}) $ for which:

$ 2^{-n (H(X)+\epsilon)} < P(x_{1}, ..., x_{n}) < 2^{-n (H(X)-\epsilon) } $ 

This essentially means:

$ \color{blue} { P((x_{1}, ..., x_{n}) \in \mathcal{A}_{\epsilon, n}) \quad \Leftrightarrow \quad 2^{-n (H(X)+\epsilon)} < P(x_{1}, ..., x_{n}) < 2^{-n (H(X)-\epsilon)} } $

### The number of typical sequences is close to $ \color{blue}{ N = 2^{n H(X)} } $.

</br>

### Asymptotic Equipartition Property (AEP)
The observation of typicality gives an operational meaning to entropy.
The **AEP** makes this precise for **any i.i.d. discrete source**, not just Bernoulli sources.

</br>

If $X_{1}, ..., X_{n}$ are i.i.d, then for any $ \epsilon > 0 $:
$$ \color{blue}{ \lim_{n \rightarrow \infty} P \Big( 2^{-n (H(X)+\epsilon)} < P(X_{1}, ..., X_{n}) < 2^{-n (H(X)-\epsilon)} \Big) = 1 } $$

**In words, as $ n \rightarrow \infty $ the probability of a typical sequence being generated is certain.**

$$ \color{green}{ P((x_{1}, ..., x_{n}) \in \mathcal{A}_{\epsilon, n})|_{n \rightarrow \infty} \rightarrow 1 } $$
</br>

To get the actual AEP definition, apply $ - \dfrac{1}{n} \log_{2}$ of the inner probability and convert to absolute sign:
$$ \lim_{n \rightarrow \infty} P \Big( H(X)-\epsilon < -\dfrac{1}{n} \log_{2} P(X_{1}, ..., X_{n}) < H(X)+\epsilon \Big) = 1 $$
$$ \color{red}{ \lim_{n \rightarrow \infty} P \Big( \Big| -\dfrac{1}{n} \log_{2} P(X_{1}, ..., X_{n}) - H(X) \Big| < \epsilon \Big) = 1 } $$

#### Proof using WLLN

Let $ Y_{i} = - \log(P(X_{i})) $
$$ \color{red}{ \lim_{n \rightarrow \infty} P \Big( \Big| \dfrac{1}{n} \sum_{i}^{n} Y_{i} - E\{Y_{1}\} \Big| < \epsilon \Big) = 1 } $$

Note*: $ \color{purple}{ E\{Y_{1}\} = H(X) } $ and $ \color{purple}{ \sum_{i}^{n} Y_{i} = - \log(\prod^{n}_{i=1} P(X_{i})) = - \log(P(X_{1}, ..., X_{n})) } $



