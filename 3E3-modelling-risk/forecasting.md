# Forecasting

## Linear Regression

$ S_{xx} = \sum_{i} (x_{i} - \overline{x})^{2} $ </br>
$ S_{yy} = \sum_{i} (y_{i} - \overline{y})^{2} $

$ S_{xy} = \sum_{i} (x_{i} - \overline{x}) (y_{i} - \overline{y}) $

**Correlation Coefficient**

$ r = \dfrac{S_{xy}}{\sqrt{S_{xx} S_{yy}}} $


### Formulation

$ \dfrac{ \sum_{i} \partial (y_{i} - (a+bx_{i}))^{2} } {\partial a} = \sum_{i} -(y_{i} - (a+bx_{i})) = 0 $

$ \dfrac{ \sum_{i} \partial (y_{i} - (a+bx_{i}))^{2} } {\partial b} = \sum_{i} -x_{i}(y_{i} - (a+bx_{i})) = 0 $

</br>

## Parameter Estimation
Solve for $ U $ upper bound and $ L $ lower bound for $ 100 P $ 
% confidence interval:
  
$$ \phi\Bigg( \dfrac{U - \hat{\mu}}{ \frac{\sigma}{\sqrt{N}} } \Bigg) = P + \dfrac{1-P}{2} $$

$ U = \hat{\mu} \quad + \underbrace{ \dfrac{\sigma}{\sqrt{N}} }_{\text{Standard Error}} \phi^{-1}\bigg( P + \dfrac{1-P}{2} \bigg) $

$ L = \hat{\mu} \quad - \underbrace{ \dfrac{\sigma}{\sqrt{N}} }_{\text{Standard Error}} \phi^{-1}\bigg( P + \dfrac{1-P}{2} \bigg) $


For proportions $ q $ and $ N $ given, consider $ \hat{\mu} = \dfrac{q}{N} $ and $ \sigma = \sqrt{q(1-q)} $:
 
$ U = q \quad + \underbrace{ \dfrac{\sqrt{q(1-q)}}{\sqrt{N}} }_{\text{Standard Error}} \phi^{-1}\bigg( P + \dfrac{1-P}{2} \bigg) $


</br> <hr> </br>

# Time-Series Fitting

### Note: $ 0 < \alpha, \enspace \beta, \enspace \gamma < 1 $ to prevent divergence.

</br>

## Moving Average ($ M $-Period)

$$ \large  \color{blue}{ \hat{X}_{t+1} = \dfrac{X_{t-(M+1)} + ... + X_{t}}{M} } $$

## Single Exponential Smoothing

$$ \large \color{blue}{ E_{t} = \alpha X_{t} + (1 − \alpha) E_{t−1} = \alpha \sum_{i=0}^{t} (1-\alpha)^{i} X_{t-i} } $$

We can use single exponential smoothing to find the $ k $-step prediction. Taking the $ E_{t} $ as the predicted $ t+1 $ point:

$$ \large \hat{X}_{t+1} = E_{t} $$ 

We can use the prediction to generate the next $ k-1 $ points:

$ \hat{X}_{t+2} = E_{t+1} = \alpha \hat{X}_{t+1} + (1-\alpha) E_{t} $

$ \hat{X}_{t+k} = E_{t+(k-1)} = \cdots $

</br>

## Multiplicative Smoothing (Holt-Winters)

### Base

$$ \large \color{red}{ E_{t} } = \alpha \color{orange}{ \dfrac{X_{t}}{S_{t-c}} } + (1-\alpha) (E_{t-1} - T_{t-1}) $$

### Trend

$$ \large \color{lime}{ T_{t} } = \beta (E_{t} - E_{t-1}) + (1-\beta) T_{t-1} $$

### Seasonality

$$ \large \color{blue}{ S_{t} } = \gamma \color{orange}{ \dfrac{X_{t}}{E_{t}} } + (1-\gamma) S_{t-c} $$

</br>

### Prediction

$$ \large \color{purple}{ \hat{X}_{t+k} } = (E_{t} + k \ T_{t}) \ \color{orange}{ S_{t+k−c} } $$

where $ \large c $ is the number of time periods in the season.

</br>

## Additive Smoothing (Holt-Winters)

### Base

$$ \large \color{red}{ E_{t} } = \alpha \color{orange}{( X_{t}- S_{t-c} )} + (1-\alpha) (E_{t-1} - T_{t-1}) $$

### Trend

$$ \large \color{lime}{ T_{t} } = \beta (E_{t} - E_{t-1}) + (1-\beta) T_{t-1} $$

### Seasonality

$$ \large \color{blue}{ S_{t} } = \gamma \ \color{orange}{ (X_{t} - E_{t}) } + (1-\gamma) S_{t-c} $$

</br>

### Prediction

$$ \large \color{purple}{ \hat{X}_{t+k} } = (E_{t} + k \ T_{t} ) \color{orange}{ + S_{t+k−c} } $$

where $ \large c $ is the number of time periods in the season.

</br>





