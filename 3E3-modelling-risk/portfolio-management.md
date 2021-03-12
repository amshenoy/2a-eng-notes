# Portfolio Management

</br>

# Modern Portfolio Theory

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
> Portfolio is efficient if return and risk cannot be improved at the same time (lies on the limit of optimality).

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

[Desmos Hedging Playground](https://www.desmos.com/calculator/izh8izazg4)

> Hedging can be shown to reduce the portfolio risk if $ \sigma_{p} < \min(\sigma_{i}, \sigma_{j}) $.

##### Note: That hedging works successfully even if the correlation coefficient is not negative (as shown in the Desmos sim)! Therefore diversification is a form of hedging that is robust for positive dependence.


</br> <hr> </br>

# Capital Asset Pricing Model (CAPM)

## Risk-Free Asset

> Consider a risk-free asset $ F $ with expected return $ \mu_{f} = E(R_{f}) $ and zero risk $ \sigma_{f}^{2} = 0 $

</br>

## Capital Allocation Line (CAL)

> **Line with gradient reward-to-risk ratio** $ \dfrac{\mu_{i} - \mu_{f}}{\sigma_{i}} $ where y-axis is $ \mu_{p} $ and x-axis is $ \sigma_{p} $ 

Consider a risky portfolio $ R_{i} $ weighted with $ w $ and $ 1 - w $ respectively. 

$ \therefore E(R_{p}) = w \ E(R_{f}) + (1-w) \ E(R_{i}) $

$$ \large \mu_{p} = w \ \mu_{f} + (1-w) \ \mu_{i} $$

$ Var(R_{p}) = w^{2} \cdot \underbrace{0}_{Var(R_{f})} + (1-w)^{2} \ Var(R_{i}) $

$$ \large \sigma_{p}^{2} = (1-w)^{2} \ \sigma_{i}^{2} $$

</br>

$ \large \sigma_{p} = (1-w) \ \sigma_{i} \qquad \Rightarrow \qquad (1-w) = \dfrac{\sigma_{p}}{\sigma_{i}} $ and $ \large w = \dfrac{\sigma_{i}-\sigma_{p}}{\sigma_{i}}$

</br>

$$ \Large 
\begin{align*}
\therefore \mu_{p} &= \Big(\dfrac{\sigma_{i}-\sigma_{p}}{\sigma_{i}} \Big) \ \mu_{f} + \Big(\dfrac{\sigma_{p} }{\sigma_{i}} \Big) \ \mu_{i} \\
\mu_{p} &= \mu_{f} + \dfrac{\mu_{i} - \mu_{f}}{\sigma_{i}} \ \sigma_{p} \\
\end{align*}
$$


</br>

### Capital Market Line (CML)

> **Capital Allocation Line with the highest gradient**. The gradient is also called "market price of risk".

</br>

### Market Portfolio

> **Portfolio** defined by the **intersection of the Capital Market Line with the original efficient frontier** of the risky portfolio. $ \large ( \ \mu_{M}, \sigma_{M} \ ) $


</br>

## Asset Risk

</br>

$ \text{Total Risk} = \text{Systematic Risk} + \text{Specific Risk} $

$ \large \sigma_{p}^{2} = \sum_{i \ne j} w_{i} w_{j} \sigma_{ij} \ + \ \sum_{i} w_{i}^{2} \sigma_{i}^{2}  $

##### Note: For a diversified portfolio, the specific risk tends to zero. However, systematic risk converges to the average of the covariances for all pairs of assets in the portfolio. (Law of average covariance showing that systematic risk does not disappear with diversification)

</br>

### Beta

$$ \Large \beta_{i} = \dfrac{Cov(R_{i}, R_{M})}{\sigma_{M}^{2}} = \dfrac{\sigma_{iM}}{\sigma_{M}^{2}} $$


</br>

## CAPM

If the market portfolio $ M $ is efficient (ie. on the frontier), the expected rate of return $ \mu_{i} $ for asset $ i $ is given by:

$$ \Large 
\begin{align*}
\mu_{i} = \mu_{f} + \beta_{i} (\mu_{m} - \mu_{f})
\end{align*}
$$

### Security Market Line (SML) 

> Line of **Beta** ($ x \leftarrow \beta_{i} $) vs **Excess Return** ($ y \leftarrow \mu_{i} - \mu_{f} $)

$$ \large \underbrace{ \mu_{i} - \mu_{f} }_{y} = \underbrace{ (\mu_{m} - \mu_{f}) }_{m} \underbrace{ \beta_{i} }_{x} $$

- If an asset is > SML, then it is **undervalued**.
- If an asset is < SML, then it is **overvalued**.

