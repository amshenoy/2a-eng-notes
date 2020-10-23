# Discrete Memoryless Channels (DMC)

"The current output only depends on the current input."

## Channel Capacity
### $$ \color{blue}{ \mathcal{C} = \max_{P_{X}} I(X; Y) } $$

### $$ \text{The channel capacity } \mathcal{C} \text{ is the maximum transmission rate over the DMC } $$


## Noiseless Binary Channel

$$ X \longrightarrow Y $$

$$ I(X; Y) = H(X) - H(X|Y) = H(X) \quad ( H(X|Y) = 0 \text{ as } Y \text{  is fully dependent on } X) $$

The $P_{X}$ that maximises $ H(X) $ is $P_{X} = (\dfrac{1}{2}, \dfrac{1}{2})$:
$$  \mathcal{C} = \max_{P_{X}} I(X; Y) = \max_{P_{X}} H(X) = 1 \text{ bit/transmission } $$



## Binary Symmetric Channel



### Repetition Code



## Binary Erasure Channel

##
