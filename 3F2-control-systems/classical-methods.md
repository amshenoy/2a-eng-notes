# Classical Methods

## Feedback Control Review

</br>
</br>

## Root Locus Method

> Useful when the open loop $ L(s) $ is fixed, and only the gain $ k $ varies.

Given open-loop $ \large L(s) $, locate poles $ \large p_{i} $ and zeros $ \large z_{i} $.

Let $ \large P $ be the number of poles and $ \large Z $ be the number of zeros.

</br>

### Plotting Rules

1) Root locus **symmetrical about real-axis**

2) **Points on the real-axis** &ensp; ***left*** *(k > 0)* | ***right*** *(k < 0)* &ensp; of an **(odd number of poles + zeros)** &ensp; are on the root locus

3) $ P $ branches start at the poles (at $ k=0 $) </br>
$ Z $ branches end at the zeros (as $ k \rightarrow \infty $) </br>
$ P-Z $ branches $ \rightarrow \infty $ at **straight line asymptotes** &ensp; at **angle** $ \dfrac{(2l+1)\pi}{P-Z} $ *(k > 0)* $ \Bigg| $ $ \dfrac{(2l)\pi}{P-Z} $ *(k < 0)* &ensp; emanating from **COM** $ \dfrac{\sum_{i} p_{i} - \sum_{i} z_{i}}{P+Z} $ </br> </br>
Total $ N = \max(P, Z) ( = P ) $ branches

4) Breakaway points $ \dfrac{dL(s)}{ds} = 0 $ (ie. $ \dfrac{dk}{ds} = 0$)



</br> </br>

## Stability Criterion $ k $

$ k $ is **unstable when the root locus intersects the im-axis**.

Let $ \large s_{0} = \omega_{0} j $:

### Routh-Hurwitz Criterion

**Poles of Closed Loop** are given by:
$$ \Large 1 + k \ L(s) = 0 $$# Classical Methods

## Feedback Control Review

</br>
</br>

## Root Locus Method

> Useful when the open loop $ L(s) $ is fixed, and only the gain $ k $ varies.

Given open-loop $ \large L(s) $, locate poles $ \large p_{i} $ and zeros $ \large z_{i} $.

Let $ \large P $ be the number of poles and $ \large Z $ be the number of zeros.

</br>

### Plotting Rules

1) Root locus **symmetrical about real-axis**

2) **Points on the real-axis** &ensp; ***left*** *(k > 0)* | ***right*** *(k < 0)* &ensp; of an **(odd number of poles + zeros)** &ensp; are on the root locus

3) $ P $ branches start at the poles (at $ k=0 $) </br>
$ Z $ branches end at the zeros (as $ k \rightarrow \infty $) </br>
$ P-Z $ branches $ \rightarrow \infty $ at **straight line asymptotes** &ensp; at **angle** $ \dfrac{(2l+1)\pi}{P-Z} $ *(k > 0)* $ \Bigg| $ $ \dfrac{(2l)\pi}{P-Z} $ *(k < 0)* &ensp; emanating from **COM** $ \dfrac{\sum_{i} p_{i} - \sum_{i} z_{i}}{P+Z} $ </br> </br>
Total $ N = \max(P, Z) ( = P ) $ branches

4) Breakaway points $ \dfrac{dL(s)}{ds} = 0 $ (ie. $ \dfrac{dk}{ds} = 0$)



</br> </br>

## Stability Criterion $ k $

$ k $ is **unstable when the root locus intersects the im-axis**.

Let $ \large s_{0} = \omega_{0} j $:

### Routh-Hurwitz Criterion

**Poles of Closed Loop** are given by:
$$ \Large 1 + k \ L(s) = 0 $$





### Root Locus Conditions

#### Angle Condition

$$ \large
\begin{align*}
\angle{L(s_{0})} &= \sum \angle(s_{0} - z_{i}) - \sum \angle(s_{0} - p_{i}) \\
&= \dfrac{(2l+1)\pi}{P-Z} \enspace (k > 0) \quad \Bigg| \quad \dfrac{(2l)\pi}{P-Z} \enspace (k < 0) 
\end{align*}
$$

#### Gain from Root Locus

$$ \large 
\begin{align*}
k = \dfrac{1}{|L(s_{0})|} = \dfrac{\prod |s_{0} - p_{i}|}{\prod |s_{0} - z_{i}|} \\
\end{align*}
$$









### Root Locus Conditions

#### Angle Condition

$$
\begin{align*}
\angle{L(s_{0})} &= \sum \angle(s_{0} - z_{i}) - \sum \angle(s_{0} - p_{i}) \\
&= \dfrac{(2l+1)\pi}{P-Z} \enspace (k > 0) \quad \Bigg| \quad \dfrac{(2l)\pi}{P-Z} \enspace (k < 0) 
\end{align*}
$$

#### Gain from Root Locus

$$
\begin{align*}
k = \dfrac{1}{|L(s_{0})|} &= \sum \angle(s_{0} - z_{i}) - \sum \angle(s_{0} - p_{i}) \\
&= \dfrac{(2l+1)\pi}{P-Z} \enspace (k > 0) \quad \Bigg| \quad \dfrac{(2l)\pi}{P-Z} \enspace (k < 0) 
\end{align*}
$$







