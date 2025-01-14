# Inventory Management

<hr><hr>

# Introduction

### Considerations

**Order quantity (Q)**: How much should we order?

**Reorder level (R)**: When should we place an order?

**Safety stock (SS)**: How much safety stock should we maintain? 

</br><hr><hr></br>

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

</br><hr><hr></br>


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
\pi(Q) &= E[\pi(Q,D)] \\
&= \int \pi(Q, x) f(x) dx \\
&= \int_{0}^{Q} c (Q-x) f(x) dx + \int_{Q}^{\infty} (p-c) (x-Q) f(x) dx
\end{align*}
$$

### Expected Profit
Alternatively we could also consider the expected profit:

$$ \Large 
\begin{align*}
P(Q) &= p \ E(\min(Q, D)) − cQ \\
&= p \Big( \int_{0}^{Q} x \ f(x) dx + \int_{Q}^{\infty} Q \ f(x) dx \Big) - cQ
\end{align*}
$$

#### Note: We could subtract $ K $ from this to include the consideration of fixed cost however this does not affect the optimal value.

</br>

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

#### Note: For a normal distribution we can use the standard distribution table by converting to the standard form:
$ \large F_{D}(Q) = F_{Z}\Big(\dfrac{Q-\mu}{\sigma}\Big) $

</br><hr></br>

# Lost Sales $ (R, S) $ Policy

(**(s, S)** in lecture notes)

> A variation of the newsvendor model

## Expected Profit

$$ \large P_{o}(R, S) = p ( \mu_{D} - E_{b}[S] ) - c (S-R) + e E_{e}[S] - b E_{b}[S] - K $$

$ b $ - Unit backorder (shortage) cost </br>
$ e $ - Unit salvage cost (for unsold units) </br>

$ \mu = \int_{0}^{\infty} x f_{D}(x) dx $ </br>
$ E_{b}[S] = \int_{S}^{\infty} (x-S) f_{D}(x) dx $ </br>
$ E_{e}[S] = \int_{0}^{S} (S-x) f_{D}(x) dx $ </br>


To find the optimal stock level, we can ignore non-S terms since we will be taking the partial derivative to find $ S* $. Here we can see the similarity with the newsvendor model:
$$ \large P(S) = (p+b-e) \ E(\min(S, D)) − (c-e)S $$


#### Note: We could subtract $ K $ from this to include the consideration of fixed cost however this does not affect the optimal value.

</br>

## Optimal Stock Level

$$ \large F(S^{*}) = \dfrac{(p+(b-e)) - (c-e)}{(p+(b-e))} $$ 

</br>

## Expected Profit with No Orders (S=R and no K)
$$ \large P_{n}(R) = p ( \mu_{D} - E_{b}[R] ) + e E_{e}[R] - b E_{b}[R] $$

## Optimal Reorder Level

To find an optimal reorder point $ R^{*} $:

1) Set $ P_{o}(R^{*}, S^{*}) = P_{n}(R^{*}) $. </br>
2) Solve numerically for $ R^{*} $.



</br><hr></br>

# Backorder $ (R, Q) $ Policy

(**(s, Q)** in lecture notes and **(Q,R)** in lecture slides)

> **EOQ** with stochastic demand per unit time $ d $

**Constant lead time but random cycle time.**

## Total Cost per unit time
$$ \Large \pi(R,Q) = h (\dfrac{Q}{2} + \underbrace{R - d L}_{SS}) + K \dfrac{d}{Q} + B(R) \ \dfrac{d}{Q}$$

$ B(R) $ - Total shortage cost per cycle as function of $ R $

## Expected Total Cost per unit time

$$ \Large E( \pi(R,Q) ) = h (\dfrac{Q}{2} + \underbrace{R - d_{\mu} L}_{SS}) + K \dfrac{d_{\mu}}{Q} + E(B(R)) \ \dfrac{d_{\mu}}{Q} $$

## Shortage Cost per unit time

### 1) Fixed Cost per Stockout 
Cost of Stockout $ \times $ Probability of Stockout
$$ \Large E(B(R)) = \alpha_{1} P(D > R) = \alpha_{1} (1- F(R)) $$


### 2) Fixed Cost per Unit ($ B(R) = b \ n(R) $)

$$
n(R) = \begin{cases}
0 \qquad \qquad D < R \\
D-R \qquad D > R 
\end{cases}
$$

</br>

$$
\Large 
\begin{align*}
E( B(R) ) &= b \ E(n(R)) \\
&= b \int_{R}^{\infty} (x-R) f(x) dx \\ \\
&= b \ L \Big(R\Big) \quad \small (\text{if } f(x) \text{ is a normal distribution} )\\
&= b \ \sigma_{d} L_{z} \Big(\dfrac{R-d_{\mu}}{\sigma_{d}}\Big) \quad \small (\text{if } f(x) \text{ is a normal distribution} )
\end{align*}
$$



### 3) Fixed Cost per Unit per Time

$$ \Large E( B(R) ) = \alpha_{3} \dfrac{1}{2 d_{\mu}} \int_{R}^{\infty} (x-R)^{2} f(x) dx $$

</br>

## Optimal QR

### Solutions

### 1) $ \dfrac{\partial}{\partial Q} E(\pi(R, Q)) = 0 $

$$ \large
\dfrac{\partial}{\partial Q} \Big( \quad \dfrac{h}{2} Q + (K + E\big( B(R) \big) ) \ \dfrac{d_{\mu}}{Q} \quad \Big) = 0
$$

$$ Q^{*} = \sqrt{ \dfrac{2d_{\mu} \bigg(K + E\Big( B(R) \Big) \bigg)}{h} } $$

### 2) $ \dfrac{\partial}{\partial R} E(\pi(R, Q)) = 0 $

$$ \Large
\dfrac{\partial}{\partial R} \Big( \quad \dfrac{h}{2} R + E\big( B(R) \big) \ \dfrac{d_{\mu}}{Q} \quad \Big) = 0
$$

#### Solutions for different shortage types
$$
\begin{align*}
(1) \qquad h + \Bigg(- \alpha_{1} f(R) \Bigg) \dfrac{d_{\mu}}{Q} &= 0\\
(2) \qquad h + \Bigg( b ( 1-F(R)) \Bigg) \dfrac{d_{\mu}}{Q} &= 0 \\
(3) \qquad h + \Bigg( - \dfrac{\alpha_{3}}{d_{\mu}} \ \sigma_{d} \ L_{z}\big(\dfrac{R-d_{\mu}}{\sigma_{d}}\big) \Bigg) \dfrac{d_{\mu}}{Q} &= 0
\end{align*}
$$

Rearrange and solve for $ R $ to find optimal $ R^{*} $.
Use the standard tables to find $ z $ and calculate $ R^{*} = \sigma_{d} z + d_{\mu} $.

### Iteration

Consider **shortage type 1** with **normal r.v** $ d $ (using $ z $ instead of $ R $ is considerably easier for hand calculation avoiding the de/re-normalisation. ):

**Iter 0** (EOQ) &emsp; - &emsp; $ Q_{0} = \sqrt{\dfrac{2 d_{\mu} K}{h}} \qquad z_{0} = fn(Q_{0}) $

**Iter 1** &emsp; - &emsp; $ Q_{1} = \sqrt{\dfrac{2 d_{\mu} (K + b \sigma_{d} L_{z}(z_{0}) )}{h}} \qquad z_{1} = fn(Q_{1}) $

**Iter 2** &emsp; - &emsp; $ Q_{2} = \sqrt{\dfrac{2 d_{\mu} (K + b \sigma_{d} L_{z}(z_{1}) )}{h}} \qquad z_{2} = fn(Q_{2}) $

### . . .

</br><hr></br>

## Backorder $ (T, S) $ policy

(**(R, S)** in lecture notes)


