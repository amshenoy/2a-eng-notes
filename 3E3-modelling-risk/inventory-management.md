# Inventory Management

# Introduction

### Considerations

**Order quantity (Q)**: How much should we order?

**Reorder level (R)**: When should we place an order?

**Safety stock (SS)**: How much safety stock should we maintain? 


# Deterministic Models (EOQ)

"Wilson-Harris Lot Size Model"

## Basic

### Total Cost per unit Time
$$ \Large \pi(Q) = \Big( h \dfrac{Q}{2} + K \dfrac{D}{Q} \Big) + h \ SS + c D $$ 

$ Q $ - Order quantity </br>
$ D $ - Demand per cycle </br>
$ h $ - Unit holding cost </br>
$ c $ - Unit purchasing cost </br>
$ K $ - Fixed order cost </br>
$ SS $ - **Safety stock** / Stock Threshold

</br>

## Shortages backordered

### Total Cost per unit Time
$$ \Large \pi(Q, S) = \Big( h \dfrac{S^{2}}{2Q} + K \dfrac{D}{Q} + \dfrac{b \ (Q-S)^{2}}{2Q} \Big) + h \ SS + c D  $$ 

$ b $ - Unit backorder (shortage) cost

#### Note: In the case, $ S = Q $ we get the original EOQ model.

</br>

## Reorder Level (R)
$$ \Large R = d \cdot L + SS = \mu + SS $$

$ \mu = d \cdot L $ - **Demand during lead time** </br>
$ d = D/T $ - **Average demand per unit time** </br>
$ L $ - **Lead time** (Time between supply order and delivery ) </br>
 
</br>

## Optimal Order Quantity (Q*)

### EOQ Basic
$$ \large \dfrac{d}{dQ} \pi(Q) = 0 $$
$$ \Large Q^{*} = $$

(TBD)

### EOQ Backordered

$$ \large \dfrac{\partial}{\partial Q} \pi(Q, S) = 0 \qquad \dfrac{\partial}{\partial S} \pi(Q,S) = 0 $$

</br>

</br><hr></br>

# Stochastic Models



</br>

## Newsvendor Problem
> Maximise the expected profit or minimise the total cost

Daily sales cannot be predicted exactly therefore the demand is represented by the random variable $ D $.

### Total Cost
$$ \large \pi(Q,D) = c \max(0, Q-D) + (p-c) \max(0, D-Q) $$

$ c $ - Unit purchasing cost </br>
$ p $ - Unit selling cost

$$ \large 
\begin{align*}
\pi(Q) &= E[\pi(Q,D)] = \int \pi(Q, x) f(x) dx \\
&= \int_{0}^{Q} c (Q-x) f(x) dx + \int_{Q}^{\infty} (p-c) (x-Q) f(x) dx
\end{align*}
$$

Alternatively we could also consider the expected profit:

$$ \Large P(Q) = p \ E(\min(Q, D)) − cQ $$


 ### Optimal Order Quantity

Using $ \pi(Q) $:

We can differentiate $ \pi(Q) $ to find the minimum and then use the **Leibniz integral rule for definite integrals** to simplify (basically apply the partial derivative inside the integral, non Q terms become 0 ):

$$
\begin{align*} 
\dfrac{d}{dQ} \pi(Q) &= c \int_{0}^{Q} f(x) dx + (p-c) \int_{Q}^{\infty} f(x) dx \\
&= c \int_{0}^{\infty} f(x) dx - p \int_{Q}^{\infty} f(x) dx \\
&= c - p ( 1 - F(Q) ) = 0 
\end{align*}
$$

</br>

Using $ P(Q) $:

$$ 
\begin{align*}
\dfrac{d}{dQ} P(Q) &= p \Big( \int_{0}^{Q} \dfrac{\partial}{\partial Q} \big( x \ f(x) \big) dx + \int_{Q}^{\infty} \dfrac{\partial}{\partial Q} \big( Q \ f(x) \big) dx \Big) - c \\
&= p \int_{Q}^{\infty} f(x) dx - c \\
&= p ( 1 - F(Q) ) - c = 0
\end{align*}
$$


</br>

$$ \Large \therefore F(Q^{*}) = \dfrac{p-c}{p} $$ 
where $ F(x) $ is the CDF of the r.v $ D $. 


</br>

## Lost Sales $ (s, S) $ Policy




## Backorder $ (s, Q) $ Policy





## Backorder $ (R, S) $ policy



