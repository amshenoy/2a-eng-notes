# Convolutional Code

> Given a string $ \underline{X} $ of $ K $ bits, every $ k $ bits (**starting from the MSB (our convention)**) is fed into a $ S $-stage shift register of length $ L = Sk $ and transformed into $ n $ bits from the contents of the register. Hence the output code has length $ N = \dfrac{K}{k} \times n $.

##### Note: Dependence between code bits is created via the shift register. Instead of having a single generator matrix (as in 3F7), the convolution means that there is equivalently $ n $ generator matrices (or vectors). This means that convolutional codes are linear codes.

##### Note: For simplicity we assume $ k = 1 $ and $ S $ is of arbitrary size so that the conversion to arbitrary $ k $ bits is doable and theoretically not neccessary (has practical purposes).

##### Note: Although a convolutional code can be thought of as a block code, the blocklength is not fixed.

</br>

## Finite-State Machine

**Convolutional codes can be represented as FSMs**:

**States** (**Nodes**) - **Contents of the first** $ \large S-1 $ **stages of the shift register**. ($ \large 2^{S-1} $ states)

**Transitions** (**Edges**) - Input ( $ \large k $ bits ), Output ( $ \large n $ bits )

</br>

## Trellis Representation

> The **trellis representation** is a **directed graph with a notion of time**.

The representation **consists of all possible paths** starting at **a specific state** at time $ t $ and ending at time $ t+1 $ **using any input**.


##### Note: The finite-state machine and the trellis are equivalent representations of a convolutional code except that the former does not have the notion of time

</br>

### Optimal Decoding

In general we should use the Viterbi algorithm for the probabilistic case.

> In the **deterministic case**, the **Viterbi algorithm** is simply the **minimum distance decoding** which is **equivalent to the Dijkstra algorithm for a directed graph**.

##### Note: Both are dynamic programming algorithms where Viterbi is a stochastic version (a form of the Bellman-Ford algorithm).

</br>

> For easy decoding, use **Dijkstra (forward dynamic programming)** giving the optimal path from the start state $ \underline{s}_{0} $  to every state $ \underline{s}_{t} $ at time $ t $.

Given a transmitted codeword output $ \large \{ \hat{\underline{y}}_{0}, ..., \hat{\underline{y}}_{\frac{K}{k}} \} $ :

1) Start at $ \underline{s}_{0} $. For every input (single bit) $ x $, output $ \underline{y} $ pair, compute the cost $ \underline{y} \oplus \hat{\underline{y}} $ at the corresponding next state $ \underline{s}_{1} $.

2) Perform for all timesteps $ t = 0, ..., \dfrac{K}{k} $ and note the minimum total cost for all the states.

3) Determine the lowest total cost path and note the inputs at the timesteps $ \hat{x} $.   


</br>

##### Note: Given a transmitted codeword output $ \{ \hat{\underline{y}}_{0}, ..., \hat{\underline{y}}_{\frac{K}{k}} \} $, the cost function is $ C(\underline{s}_{t}, \underline{x}_{t}) = \sum_{t=0}^{t} | \underline{y}_{t} -\hat{\underline{y}}_{t} | = \sum_{t=0}^{t} | h( \underline{s}_{t}, \underline{x}_{t} ) -\hat{\underline{y}}_{t} | $ where $ \underline{y}_{t} = h( \underline{s}_{t}, \underline{x}_{t} ) $ is the output at state $ \underline{s}_{t} $ for an input $ \underline{x}_{t} $ (for k = 1, this is a single bit) and $ h( \cdot, \cdot ) $ is the function that calculates the output (ie. the FSM or a more explicit definition use left-shift, truncation and XOR).

</br> <hr> </br>

## Convolution Representation

$ \underline{X} $ is the **full string input** and $ \underline{g} $ are the **generator vectors** of length $ n $ bits.

$$ \large \underline{y}_{t} = \underline{X} * \underline{g}_{t} $$

### ---------------------------------
### (Non-Examinable)

We can take the D-transform (z-transform where $ D = z^{-1} $) giving us the following:

$$ Y(D) = X(D^{n}) \ \Big( \ \sum_{i=0}^{n} D^{i} \ G_{i}(D^{n}) \ \Big)
$$

##### Note: The $ D^{n} $ within $ X(D^{n}) $ and $ G_{i}(D^{n}) $ is so that we get the exact desired output of $ N = n K $ terms for $ Y(D) $ (ie. $ N = n K $ bits in the discrete-time domain) [assuming $ k = 1 $].

### ---------------------------------

</br><hr></br>

## Performance

> In linear codes, we considered the minimum distance $ \large d_{min} $ between any two codewords but since convolutional codes do not have a fixed blocklength we consider the free distance $  \large d_{\text{free}} $.

$ \le \lfloor \dfrac{d_{free}-1}{2} \rfloor $ errors can be corrected.

**We can compute $ \large d_{free} $ using the code transfer function:**

1) **Simplify state labels** (Use letters instead of the state vectors)

2) **Duplicate the all-zero state** (creating two nodes; **a start and an end**)

3) **Label each transition edge with $ \large D^{w} $** where **$  \large w $** is the **weight of the output** at that edge.

4) **$ d_{\text{free}} $** is the **minimum sum of the edges** going **from the start to the end node**.


</br>

##### Note: Free distance is the difference in path metrics between the all-zeroes output and the path with the smallest non-zero path metric going from the initial all-zero state to some future all-zero state. (In our case the path metric is the Hamming distance)


