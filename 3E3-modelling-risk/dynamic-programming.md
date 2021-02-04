# Dynamic Programming

## Formulation

Given a state $ S_{n} $ and an action $ x_{n} $, the system function $ g( \cdot ) $ determines the next state $ S_{n+1} $:

$ \large S_{n+1} = g(S_{n}, x_{n}) $

</br>

### Total Cost
> The value of the best path $ f_{0}^{*}(S_{0}) $ starting from state $ S_{0} $ is the set of actions $ x_{n} $ at time $ n $ that minimises the total cost of the path.

$$ \large \color{purple}{ f_{0}^{*}(S_{0}) = \min_{x\in \mathcal{X}} \Big( \sum_{n=0}^{N-1} c_{n}(S_{n}, x_{n}) \Big) + c_{N}(S_{N}) } $$

</br>

## Bellman Equation

$ \large S_{n+1} = g(S_{n}, x_{n}) $

> From the **formulation**, starting from time $ n $, we get the total cost of the path starting from $ S_{n} $ with action $ x_{n} $ is given by the sum of the costs from $ n $ to $ N $.

$$ \large f_{n}(S_{n}, x_{n}) = \sum_{i=n}^{N-1} c_{i}(S_{i}, x_{i}) + c_{N}(S_{N}) $$

> The optimal action $ x_{n} $ at every stage is the one that **minimises the total cost at every stage** (or **maximises the reward at every stage**).

$ \large f_{n}^{*}(S_{n}) = \min_{x \in \mathcal{X}} f_{n}(S_{n}, x_{n}) $ 

</br>

### Iterative Equation

> The optimal total cost at $ n $ is the sum of the cost at $ S_{n} $ and the optimal total cost at $ n+1 $ minimised by the action $ x_{n} $.

$$ \large
\begin{align*}
f_{n}^{*}(S_{n}) &= \min_{x \in \mathcal{X}} \Big( c_{n}(S_{n}, x_{n}) + f_{n+1}^{*}(S_{n+1}) \Big) \\
f_{n}^{*}(S_{n}) &= \min_{x \in \mathcal{X}} \Big( c_{n}(S_{n}, x_{n}) + f_{n+1}^{*}( \ g(S_{n}, x_{n}) \ ) \Big) \\
\end{align*}
$$

</br>

### Probabilistic Equation

> This is essentially the **probability weighted average of for all the possible next states** as in the iteration equation.

$$ \large
\begin{align*}
f_{n}^{*}(S_{n}) &= \min_{x \in \mathcal{X}} \Bigg( \sum_{t \in \mathcal{S}} P_{n}(S_{n+1}=t) \Big( c_{n}(S_{n}, x_{n}) + f_{n+1}^{*}(S_{n+1} = t) \Big) \Bigg)
\end{align*}
$$
