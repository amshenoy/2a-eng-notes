# Decision Analysis

## Decision Trees

**Decision** Node $ \rightarrow $ **Probability** Node

Simplify to:

**Decision** Node $ \rightarrow $ **Value** Node 

</br><hr></br>

## Payoff Tables

### Maximax
> Maximise maximum payoff

### Maximin 
> Maximise minimum payoff

</br>

### Max EMV
> Maximise expected monetary value

#### Expected Value (EMV)
$ \large \underline{v} = R \underline{p} $

$$ v_{i} = \sum_{j} r_{ij} \ p_{j} $$

</br>

### Min ERL(/EOL)
> Minimise regret (/opportunity) loss

#### Expected Regret Loss (ERL)
$$ v_{i} = \sum_{j} (\max_{k} r_{kj} - r_{ij}) \ p_{j} $$

**The decision with the largest EMV also has the smallest ERL.**


#### EVPI (Min ERL)
> Expected Value of Perfect Information

$$ EVPI = \sum_{j} ( \max_{k} r_{kj} ) \ p_{j} - \max_{i} EMV_{i} = PI − \max_{i} EMV_{i} = \min_{i} ERL_{i} $$



### EVSI
> Expected Value of Sample Information

$$ EVSI = EMV_{new} - EMV_{old} $$

$ EMV_{new} $ is the new $ EMV $ by **adjusting the probabilities of the decision tree using Bayes rule**.

$ EMV_{old} $ is the prior $ EMV $ assumption.



</br><hr></br>


## Utility Theory

Given two random yields $Y_{1}$ and $Y_{2}$, a decision maker prefers $Y_{1}$ to $Y_{2}$, if and only if the expected utility of $Y_{1}$ is larger than the expected utility of $Y_{2}$.

Consider a utility function $ U(x) $:

### Risk-Averse (Concave)
$ E(U(Y)) < U(E(Y)) $


### Risk-Seeking (Convex)
$ E(U(Y)) > U(E(Y)) $

### Risk-Neutral (Linear)
$ E(U(Y)) = U(E(Y)) $



