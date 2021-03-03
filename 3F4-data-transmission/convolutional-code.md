# Convolutional Code

> Given a string $ \underline{s} $ of $ K $ bits, every $ k $ bits (**starting from the MSB (our convention)**) is fed into a $ S $-stage shift register of length $ L = Sk $ and transformed into $ n $ bits from the contents of the register. Hence the output code has length $ N = K \times \dfrac{n}{k} $.

##### Note: Dependence between code bits is created via the shift register. Instead of having a single generator matrix (as in 3F7), the convolution means that there is equivalently $ n $ generator matrices (or vectors). This means that convolutional codes are linear codes.

##### Note: For simplicity we assume $ k = 1 $ and $ S $ is of arbitrary size so that the conversion to arbitrary $ k $ bits is doable and theoretically not neccessary (has practical purposes).

##### Note: Although a convolutional code can be thought of as a block code, the blocklength is not fixed.

</br>

## Finite-State Machine

**Convolutional codes can be represented as FSMs**:

**States** (**Nodes**) - **Contents of the first** $ \large S-1 $ stages of the shift register. ($ \large 2^{S-1} $ states)

**Transitions** (**Edges**) - Input ( $ \large k $ bits ), Output ( $ \large n $ bits )

</br>

## Trellis Diagram


</br>

## Viterbi Algorithm


