# Inventory Management

## Introduction

### Considerations

**Order quantity (Q)**: How much should we order?

**Reorder level (R)**: When should we place an order?

**Safety stock (SS)**: How much safety stock should we maintain? 


## Deterministic Models

### EOQ Model (Basic) (with no shortages)
"Wilson-Harris Lot Size Model"

#### Total Cost per unit Time
$$ \Large \pi(Q) = C_{h} \dfrac{Q}{2} + K \dfrac{D}{Q} + C_{h} \ SS + C_{v} D $$ 

$ Q $ - Order quantity </br>
$ D $ - Demand per cycle </br>
$ C_{h} $ - Unit holding cost </br>
$ K $ - Fixed order cost </br>
$ C_{v} $ - Unit purchasing cost </br>
$ SS $ - **Safety stock** / Stock Threshold

</br>

#### Reorder level
$$ \Large R = d \cdot L + SS = \mu + SS $$

$ \mu = d \cdot L $ - **Demand during lead time** </br>
$ d = D/T $ - **Average demand per unit time** </br>
$ L $ - **Lead time** (Time between supply order and delivery ) </br>
 
</br>

#### Optimal Order Quantity

$$ \dfrac{d}{dQ} \pi(Q) = 0 $$
$$ Q^{*} = $$

(TBD)

### EOQ Model with shortages backordered




</br>

## Stochastic Models



</br>

### Newsvendor Problem



Leibniz Integral Rule


### Lost Sales $ (s, S) $ Policy




### Backorder $ (s, Q) $ Policy



### Backorder $ (R, S) $ policy



