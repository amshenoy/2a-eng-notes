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
**Let $ X_{1}, X{2}, ..., X_{n} $ be a sequence of i.i.d rvs with finite mean $ \mu $:**
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



