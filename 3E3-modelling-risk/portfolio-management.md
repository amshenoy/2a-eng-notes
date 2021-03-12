# Portfolio Management


## Modern Portfolio Theory

> **Markowitz Mean-Variance Model** </br> </br>
Consider a set of weights $ w_{i} $ such that $ \sum_{i=1}^{N} w_{i} = 1 $ (ie. a vector $ \underline{w} $). We can now consider a **random variable** $ R_{i} $  giving the return for the **asset** $ i $. </br> </br>
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

$$ \large Var(R_{P}) = \sum_{i=1}^{N} \ w_{i} \ \sum_{j=1}^{N} \ w_{j} \ Var(R_{i} R_{j}) = \underline{w}^{T} \ \Sigma \ \underline{w} $$

</br>

##### Note: $ Var(R_{i}R_{j}) = \dfrac{1}{T} \sum_{t=1}^{T} ( r_{t}^{(i)} - \overline{r}^{(i)} ) ( r_{t}^{(j)} - \overline{r}^{(j)} ) $

</br>

## Efficient Frontier

### Max Return



</br>

### Min Risk





</br></br>

## Hedging

> Reducing risk by 



</br> </br>

## Capital Asset Pricing Model (CAPM)










