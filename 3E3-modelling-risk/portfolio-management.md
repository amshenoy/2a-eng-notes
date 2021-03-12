# Portfolio Management


## Modern Portfolio Theory

> **Markowitz Mean-Variance Model** </br> </br>
Consider a set of weights $ w_{i} $ such that $ \sum_{i=1}^{N} w_{i} = 1 $ (ie. a vector $ \underline{w} $ such that $ \underline{w}^{T} \underline{1} = 1 $). We can now consider a **random variable** $ R_{i} $  giving the **return for asset** $ i $. </br> </br>
In general, we can only use the **past asset prices** (ie generate **statistics** of $ R_{i} $) and the **key assumption is the central-limit theorem**. 

</br>

### Expected Asset Return
**Return from time $ t-1 $ to $ t $** &emsp; $ r_{t} = \dfrac{ p_{t} - p_{t-1} }{p_{t-1}} $

$$ \large E(R_{i}) = \dfrac{1}{T} \sum_{t=1}^{T} \dfrac{ p_{t} - p_{t-1} }{p_{t-1}} $$

</br>

### Expected Portfolio Return
$$ \large E(R_{P}) = \sum_{i=1}^{N} \ w_{i} \ E(R_{i}) = \underline{w}^{T} \underline{R}  $$

##### Side Note: $ R_{P} = \sum_{i=1}^{N} \ w_{i} \ R_{i} $  Notice how this is actually an implicit definition of a mixture of Gaussians model with means $ E(R_{i}) $ and variances $ Var(R_{i} R_{j}) $

</br>

### Expected Portfolio Risk

$$ \large Var(R_{P}) = \sum_{i=1}^{N} \ w_{i} \ \sum_{j=1}^{N} \ w_{j} \ Var(R_{i}, \ R_{j}) = \underline{w}^{T} \ \Sigma \ \underline{w} $$

</br>

##### Note: $ Var(R_{i}, \ R_{j}) = Cov(R_{i}, \ R_{j}) = \dfrac{1}{T} \sum_{t=1}^{T} ( r_{t}^{(i)} - \overline{r}^{(i)} ) ( r_{t}^{(j)} - \overline{r}^{(j)} )  \qquad = \qquad \sigma_{ij} = \sigma_{i} \sigma_{j} \rho_{ij} $

</br>

#### Alternative Risk Meaasures

- Semi-Variance (SVar) (Downside Deviation only)
- Mean Absolute Deviation (MAD)
- Value-at-Risk (VAR)
- Conditional Value-at-Risk (CVAR) [Coherent Risk Measure]

</br>

## Efficient Frontier

### Max Return

Maximise:  $ E(R_{p}) = \underline{w}^{T} \underline{R} $ </br>

Subject to: </br>
$ \underline{w}^{T} \ \Sigma \ \underline{w} \ \le \ \sigma^{2} $ </br>
$ \underline{w}^{T} \ \underline{1} = 1 $


</br>

### Min Risk

Minimise:  $ Var(R_{p}) = \underline{w}^{T} \ \Sigma \ \underline{w} $ </br>

Subject to: </br>
$ \underline{w}^{T} \underline{R} \ge \ \mu $ </br>
$ \underline{w}^{T} \ \underline{1} = 1 $




</br></br>

## Hedging

> Reducing overall risk by holding multiple assets

A perfect correlation coefficient of $ \rho_{ij} = -1 $ gives a perfect hedge.

Consider a portfolio of 2 assets $ R_{p} = w R_{i} + (1-w) R_{j} $:

$
\begin{align*}
Var(R_{p}) &= w^{2} \ Var(R_{i}) + (1-w)^{2} \ Var(R_{j}) + 2 w(1-w) \ Cov(R_{i}, R_{j}) \\
\sigma_{p}^{2} &= w^{2} \ \sigma_{i}^{2} + (1-w)^{2} \ \sigma_{j}^{2} + 2 w(1-w) \ \sigma_{i} \ \sigma_{j} \ \rho_{ij} \\
\end{align*}
$

[Desmos Hedging Playground](https://www.desmos.com/calculator/h9hmsq0pkp)

> Hedging can be shown to reduce the portfolio risk if $ \sigma_{p} < \min(\sigma_{i}, \sigma_{j}) $.

##### Note: That hedging works successfully even if the correlation coefficient is not negative (as shown in the Desmos sim)! 

</br> </br>

## Capital Asset Pricing Model (CAPM)










