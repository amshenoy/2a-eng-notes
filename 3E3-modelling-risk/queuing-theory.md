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

## CTMCs Birth-Death Processes
