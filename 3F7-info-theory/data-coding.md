# Information Coding

Prefix-free codes


## Shannon-Fano Coding




</br><hr>
## Huffman Coding




</br><hr>
## Interval Coding

Every symbol can be represented as an interval inside $ [0,1] $ with the length of the interval equal to the symbol probability.

</br>

**For a set of symbols:**
1) Map symbols to $ [0, 1] $

**To find the codewords for each symbol:**

2) For each symbol interval $ [a, a+p] $, the aim is to find the largest dyadic interval $ \Bigg[ \dfrac{j}{2^{L}}, \dfrac{j+1}{2^{L}} \Bigg] $ where $ L $ is either $ \Bigg\lceil \log_{2} \dfrac{1}{p} \Bigg\rceil $ or $ \Bigg\lceil \log_{2} \dfrac{1}{p} \Bigg\rceil + 1 $

</br>
$ \rule{14cm}{0.4pt} $

**A more practical way of solving this is as follows (used in arithmetic coding):**

### Given $ [a, a+\color{red} {p}] $ :

$ \color{blue} { L } = \Bigg\lceil \log_{2} \dfrac{1}{\color{red} {p}} \Bigg\rceil \text{ or } \Bigg\lceil \log_{2} \dfrac{1}{\color{red} {p}} \Bigg\rceil + 1 $

#### Check if some $ \color{red} { j } $ and $ \color{red} { j + 1 } $ lies in $ \Big[a \cdot 2^{\color{blue} {L}}, \quad (a+\color{red} {p}) \cdot 2^{\color{blue} {L}} \Big] $

#### Codeword for the symbol is $ \color{blue} { bin(\color{red} {j}) } $

Note*: Possible to have more than one $ j $ and $ j+1 $ pairs and hence more than one codeword per symbol.
$ \rule{14cm}{0.4pt} $

Also note that multiplying by $ 2^{L} $ is to shift the desired bits of the decimal number into the integer part of the number $ j $ or $ j+1 $  which can then be easily converted to binary. Alternatively just consider the first $ L $ bits of the interval probability after the decimal point and then pick a binary number that lies within the truncated binary numbers to get the codeword.
 
</br>

### Average Codeword Length
### $ E(\color{blue} {L}) = \sum_{i} \color{red} {p_{i}} \color{blue} {L_{i}} \quad \le \quad \sum_{i} \color{red} {p_{i}} \Big(\big\lceil \log_{2} \dfrac{1}{\color{red} {p_{i}}} \big\rceil + 1 \Big) \quad \lt \quad H(X) + 2 \text{ bits per symbol} $
### $$ \therefore E(L) \lt H(X) + 2 \text{ bits per symbol} $$


</br><hr>

## Arithmetic Coding

### For a given alphabet $ \underline{a} $ with probability $ \underline{p} $, determine the codeword for the sequence $ \underline{s} $ :

### Overview
#### 1) Determine sequence interval
#### 2) Apply interval coding

</br> 

#### Sequence Interval
For each symbol $ s_{i} $ in sequence $ \underline{s} $:
$ s_{i} \quad [ f(s_{i}), f(s_{i}) + p(s_{i}) ] $


Apply recursive interval finding


</br>

### Average Codeword Length
For a sequence of length $ N $, where each $i$-th sample is picked from a distribution $ X_{i} $.

### $$ E(L) \lt \dfrac{H(X_{1}, ..., X_{N}) + 2}{N} \text{ bits per symbol} $$
### $$ E(L) \lt H(X) + \dfrac{2}{N} \text{ bits per symbol} \quad \text{if X is i.i.d} $$





