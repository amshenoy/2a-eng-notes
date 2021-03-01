# Queuing Theory

</br><hr></br>

## Kendall's Notation

$$ \Large U / V / s / \kappa / W $$

$ \large U $ - **Inter-arrival time distribution**

$ \large V $ - **Service time distribution**

$ \large U $ and $ \large V $ can be one of the following: </br>

$ M $ for **memoryless** (eg. exponential) </br>
$ D $ for **deterministic** (non-probabilistic) </br>
$ G $ for **general** (unspecified) distribution </br>

$ \large s $ - **Number of Servers**

$ \large \kappa $ - **System Capacity** (**max number of customers in the system**)

$ \large W $ - **Queueing Protocol/Discipline**. Common examples are **FIFO (First In FirstOut)**, **LIFO (Last In First Out)** and **priority-based**.

#### Note: $ \kappa $ and $ W $ are optional with default values $ \kappa = \infty $ and $ W = FIFO $.


</br>

## Types of Queues

- Single Queue / Single Server
- Single Queue / Multi Server
- Multi Queue / Single Server
- Multi Queue / Multi Server

### Special Behaviour (assumptions ignored)

- Balking (Choosing to not enter the queue)
- Jockeying (Changing between queues)
- Reneging (Leaving the queue without finishing)

</br><hr></br>

# Formulation

$ \large N(t) $ - **Number of customers** at time $ t $

$ \large P_{n}(t) $ - **Probability of $ n $ customers** in the queue at time $ t $

$ \large \lambda_{n} $ - **Mean arrival time** when $ n $ customers are in the system

$ \large \mu_{n} $ - **Mean service time** when $ n $ customers are in the system

Traffic Intensity (Utilisation) $ \Large \color{blue}{ \rho = \dfrac{\lambda}{s\mu} } $

</br>

## Steady-State Metrics

</br>

$ p_{n} = P(N=n) $

**Expected Number of customers** in the system
$$ \Large \color{blue}{ L = \sum_{n=0}^{\infty} n \ p_{n} } $$

**Expected Queue Length** (excluding people at server) 
$$ \Large \color{blue}{ L_{q} = \sum_{n=s}^{\infty} (n-s) \ p_{n} } $$


</br>

### Little's Law

**Lead Time of full process** - $ \large \color{blue}{ W = \dfrac{L}{\lambda} } $

**Lead Time in Queue** - $ \large \color{blue}{ W_{q} = \dfrac{L_{q}}{\lambda} } $

$ \color{blue}{ W = W_{q} + \dfrac{1}{\mu} } $

Mean Service Time $ \dfrac{1}{\mu} $

</br>

#### Extras:
$ L = L_{q} + \dfrac{\lambda}{\mu} $


</br>

#### Note: Simple queueing system reaches steady state only if $ \rho < 1 $

</br><hr></br>

## Birth-Death Process (CTMC)

Let $ p_{n} = P(N=n) $

We can consider the following parameters for a birth-death process:

</br>

### For an $ M / M / 1 $: &emsp; $ \lambda_{n} = \lambda $, &emsp; $ \mu_{n} = \mu $

For **steady state**, we need the **expected output = expected input** for each node $ n $:

$ \large \mu_{n} p_{n} = \lambda_{n-1} p_{n-1}$

This gives us the full formula for $ p_{n} $:

$ \large \color{green}{ p_{n} = \dfrac{\prod_{i=0}^{n-1} \lambda_{i}}{\prod_{i=1}^{n} \mu_{i}} p_{0} = (1-\rho) \rho^{n} } $

We can now use the formulas for $ p_{n} $ to find $ L $  which in turn can be used to find the other steady-state metrics $ L_{q}, W, W_{q} $ for an $ M / M / 1 $ queueing system.

$ \large \color{green}{ L_{q} = \dfrac{\rho^{2}}{1-\rho} } $


</br>

### For an $ M / M / s $: &emsp; $ \lambda_{n} = \lambda $, &emsp; $ \mu_{n} = \begin{cases} n \mu \qquad n < s \\ s \mu \qquad n \ge s \end{cases} $

#### Note: The derivation for this is the same but the solution is more complicated.




