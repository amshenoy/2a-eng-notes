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


## Parameter Estimation
Solve for $ U $ upper bound and $ L $ lower bound for $ 100 P $ 
% confidence interval:
  
$$ \phi\Bigg( \dfrac{U - \hat{\mu}}{ \frac{\sigma}{\sqrt{N}} } \Bigg) = P + \dfrac{1-P}{2} $$

$ U = \hat{\mu} \quad + \underbrace{ \dfrac{\sigma}{\sqrt{N}} }_{\text{Standard Error}} \phi^{-1}\bigg( P + \dfrac{1-P}{2} \bigg) $

$ L = \hat{\mu} \quad - \underbrace{ \dfrac{\sigma}{\sqrt{N}} }_{\text{Standard Error}} \phi^{-1}\bigg( P + \dfrac{1-P}{2} \bigg) $


For proportions $ q $ and $ N $ given, consider $ \hat{\mu} = \dfrac{q}{N} $ and $ \sigma = \sqrt{q(1-q)} $:
 
$ U = q \quad + \underbrace{ \dfrac{\sqrt{q(1-q)}}{\sqrt{N}} }_{\text{Standard Error}} \phi^{-1}\bigg( P + \dfrac{1-P}{2} \bigg) $


