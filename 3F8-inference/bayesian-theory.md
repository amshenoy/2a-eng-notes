# Bayesian Theory
$$ \text{Bayes' Theorem} \qquad p(B|A) = \dfrac{p(B)}{p(A)} \ p(A|B) $$

## Bayesian Inference
Replacing $ B $ with some parameter set $ \color{blue}{\boldsymbol{\theta}} $ and replacing $ A $ with some data set $ \color{green}{\boldsymbol{x}} $: 

### $$ \Bigg[ \quad \underbrace{ p( \color{blue}{\boldsymbol{\theta}} | \color{green}{\boldsymbol{x}} ) }_{\textbf{Posterior}}
 = \dfrac{ \overbrace{p(\color{blue}{\boldsymbol{\theta}})}^{\textbf{Prior}} }{ \underbrace{ p(\color{green}{\boldsymbol{x}})}_{\textbf{Marginal Likelihood}} } \ 
\overbrace{ p(\color{green}{\boldsymbol{x}} | \color{blue}{\boldsymbol{\theta}}) }^{\textbf{Likelihood}}
\quad \Bigg]
$$

An alternate representation where $ \mathcal{M} $ denotes all the modelling and probability distribution assumptions:
$$ p\Big( \ \color{blue}{\boldsymbol{\theta}} \ | \ \color{green}{\{x_{n}\}_{n=1}^{N}}, \mathcal{M} \ \Big) = \dfrac{p\Big( \ \color{blue}{\boldsymbol{\theta}}, \mathcal{M} \ \Big)}{p\Big( \ \color{green}{\{x_{n}\}_{n=1}^{N}} \ \Big)} \ p\Big( \ \color{green}{\{x_{n}\}_{n=1}^{N}} \ | \ \color{blue}{\boldsymbol{\theta}} \ \Big) $$

</br>


$$ \underbrace{ p( \color{blue}{\boldsymbol{\theta}} | \color{green}{\boldsymbol{x}} ) }_{\textbf{Posterior}} = \dfrac{ p(\color{blue}{\boldsymbol{\theta}}) }{ p(\color{green}{\boldsymbol{x}}) } p(\color{green}{\boldsymbol{x}} | \color{blue}{\boldsymbol{\theta}} ) 
\quad \propto \quad
\underbrace{p(\color{blue}{\boldsymbol{\theta}})}_{\textbf{Prior}} \ \underbrace{p(\color{green}{\boldsymbol{x}} | \color{blue}{\boldsymbol{\theta}} )}_{\textbf{Likelihood}}  $$
</br>
### $$ \Bigg[ \quad \therefore \underbrace{ p( \color{blue}{\boldsymbol{\theta}} | \color{green}{\boldsymbol{x}} ) }_{\textbf{Posterior}}
\quad \propto \quad
\underbrace{p(\color{blue}{\boldsymbol{\theta}})}_{\textbf{Prior}} \ \underbrace{p(\color{green}{\boldsymbol{x}} | \color{blue}{\boldsymbol{\theta}} )}_{\textbf{Likelihood}} \quad \Bigg] $$

##### Note*: We can convert the equals sign to a proportional sign as the marginal likelihood  is just the normalizing constant of Bayes' Theorem.
$ p(\color{green}{\boldsymbol{x}}) = \int \underbrace{p(\color{blue}{\boldsymbol{\theta}})}_{\textbf{Prior}} \ \underbrace{p(\color{green}{\boldsymbol{x}} | \color{blue}{\boldsymbol{\theta}} )}_{\textbf{Likelihood}} d\color{blue}{\boldsymbol{\theta}} $
 
We can also write the likelihood function as a product of the probabilities as each of the data points are considered to be independent events:

### $$ \underbrace{ p( \color{blue}{\boldsymbol{\theta}} | \color{green}{\boldsymbol{x}} ) }_{\textbf{Posterior}}
\quad \propto \quad
\underbrace{p(\color{blue}{\boldsymbol{\theta}})}_{\textbf{Prior}} \quad \underbrace{p(\color{green}{\boldsymbol{x}} | \color{blue}{\boldsymbol{\theta}} )}_{ {\displaystyle \prod_{\color{green}{i=1}}^{\color{green}{N}} p( \color{green}{x_{i}} | \color{blue}{\boldsymbol{\theta}} )} \\ \  \textbf{Likelihood} }  $$

For general problem-solving, to calculate the posterior distribution:
### $$ \Bigg[ \quad \underbrace{ p( \color{blue}{\boldsymbol{\theta}} | \color{green}{\boldsymbol{x}}, \mathcal{M} ) }_{\textbf{Posterior}}
\quad \propto \quad
\underbrace{p(\color{blue}{\boldsymbol{\theta}}, \mathcal{M})}_{\textbf{Prior}} \quad \underbrace{ \prod_{\color{green}{i=1}}^{\color{green}{N}} p(\color{green}{x_{i}} | \color{blue}{\boldsymbol{\theta}}) }_{ \textbf{Likelihood} } \quad \Bigg] $$

## Maximum Estimation
Finding the parameter for which the posterior or the likelihood is maximised.
##### Note*: Often easier to compute the maximum of the log of the function and hence give rise to the terms log-likelihood and log-posterior functions.

### Maximum a Posteriori (MAP) Estimation
$$ \color{blue}{\boldsymbol{\theta}}^{\color{red}{\text{MAP}}} = \arg \max_{\color{blue}{\boldsymbol{\theta}}} \Big\{ p( \ \color{blue}{\boldsymbol{\theta}} \ | \ \color{green}{\boldsymbol{x}} \ ) \Big\} $$
For single dimension and general problem-solving, simply compute the following:
$$ \dfrac{d}{d\color{blue}{\theta}} \Big( ln(\color{red}{\small\text{Posterior}}) \Big) = \dfrac{d}{d\color{blue}{\theta}} \Big( p( \ \color{blue}{\theta} \ | \ \color{green}{\boldsymbol{x}} \ ) \Big) = 0 $$ 

### Maximum Likelihood (ML) Estimation

$$ \color{blue}{\boldsymbol{\theta}}^{\color{red}{\text{ML}}} = \arg \max_{\color{blue}{\boldsymbol{\theta}}} \Big\{ p( \ \color{green}{\boldsymbol{x}} \ |  \ \color{blue}{\boldsymbol{\theta}} \ ) \Big\} $$


