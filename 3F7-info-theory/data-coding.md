# Information Coding

## Compression
Typical set is a small subset of the state space but contains majority of the probability. Hence we can focus on trying to optimise the coding for the typical set.

### Fundamental Limit
### $ E(\color{blue} {L}) = \sum_{i} \color{red} {p_{i}} \color{blue} {L_{i}} \quad \text{Average Codeword 
Length per Sequence} $

### $ \dfrac{E(\color{blue} {L})}{N} \quad \text{Average Codeword 
Length per Symbol} $
 
**Shannon's Lossless Source Coding Theorem &emsp; - &emsp; Expected codeword length per symbol must be greater than or equal to the entropy of the source.**
### $$ \dfrac{E(L)}{N} \ge H(X) $$


Note*: A uniform distribution source cannot be compressed at all!


</br><hr>

## Prefix-Free Codes
 
**A codeset is prefix-free if no codeword in the codeset is a prefix of another codeword in the same codeset.**

**Prefix-free** codewords must be the **leaves** of the binary tree.

### Unique Decodability
A codeset is uniquely decodable if each codeword in the codeset can only be produced by the corresponding symbol and not by a combination of symbols.

All **prefix-free codesets are uniquely decodable** however all uniquely decodable codesets are not prefix-free.

### Kraft's Inequality

Given a set of required lengths for each codeword, we can check if a prefix-free codeset is possible by pruning the binary tree.

#### A binary prefix-free (including uniquely decodable) codeset with lengths $ l_{1}, ..., l_{n} $ exists only if:
## $$ \sum^{n}_{i} 2^{-l_{i}} \le 1 $$


</br><hr>

## Shannon-Fano Coding

1) Arrange symbols in order of probability $p_{i}$ from highest to lowest.
2) Calculate the cumulative probability $f_{i-1}$ for each symbol.
3) Calculate the length of the codeword $ L_{i} = \Big\lceil \log_{2}\dfrac{1}{p_{i}} \Big\rceil = \Big\lceil -\log_{2}p_{i} \Big\rceil $ for each symbol.
4) The codeword is $c_{i} = bin(int(f_{i-1} \cdot 2^{L_{i}})) $

### $ \color{blue}{c_{i} = bin(int(f_{i-1} \cdot 2^{L_{i}})) } $


</br><hr>
## Huffman Coding

1) Arrange symbols in order of probability $p_{i}$ from **highest to lowest** (or lowest to highest).

2) Combine lowest two probabilities and re-insert into list at correct position. $(\color{blue}{\textbf{Draw cumulation branch diagram}}) $

3) **Repeat until only one node in list.**

4) **Note codeword for each symbol** by allocating 0 and 1 to up and down (or vice versa) branches respectively and **following from root node to symbol**.
 
Example:
(Insert Diagram Here)

</br><hr>
## Interval Coding

Every symbol can be represented as an interval inside $ [0,1] $ with the length of the interval equal to the symbol probability.

</br>

**For a set of symbols:**
1) Map symbols to intervals $ [a, a+p] $ between $ [0, 1] $ in any order.

**To find the codewords for each symbol:**

2) For each symbol interval $ [a, a+p] $, the aim is to find the largest dyadic interval $ \Bigg[ \dfrac{j}{2^{L}}, \dfrac{j+1}{2^{L}} \Bigg] $ where $ L $ is either $ \Bigg\lceil \log_{2} \dfrac{1}{p} \Bigg\rceil $ or $ \Bigg\lceil \log_{2} \dfrac{1}{p} \Bigg\rceil + 1 $

</br>
$ \rule{14cm}{0.4pt} $

**PRACTICALLY as follows (used in arithmetic coding):**

### Given $ [a, a+\color{red} {p}] $ :

#### $ \color{blue} { L } = \Big\lceil \log_{2} \dfrac{1}{\color{red} {p}} \Big\rceil \text{ or } \Big\lceil \log_{2} \dfrac{1}{\color{red} {p}} \Big\rceil + 1 $

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

### For a given alphabet set $ \underline{a} $ with probability set $ \underline{p} $, determine the codeword for the sequence $ \underline{s} $ :

### Overview
#### 1) Determine sequence interval
#### 2) Apply interval coding

</br> 

### Sequence Interval

**INTUITIVELY as follows:**

Nested Subset Diagram

</br>

**PRACTICALLY as follows:**
#### 1) Calculate cumulative probabilities $ \underline{f} $ for each symbol starting with $ 0 $.

#### 2) For each symbol $ s_{i} $ in sequence $ \underline{s} $, calculate the alphabet interval $ A_{i} $ :

$ A_{1} = [0, p_{1}] $

$ A_{i} \quad = \quad \Big[ f(s_{i}), \quad f(s_{i}) + p(s_{i}) \Big] $

#### 3) Apply recursive interval finding from $ i = 2 $ to $ i = N $ to find the sequence interval $ S_{N} $ :
$ S_{i} = \Big[ f(s_{i-1}), \quad f(s_{i-1}) \Big] + p(s_{i-1})  \Big[ f(s_{i}), \quad f(s_{i}) + p(s_{i}) \Big] $ 

#### 4) $ \text{Codeword} = bin(S_{N}[0] \cdot 2^{L}) $

</br>

### Average Codeword Length
For a sequence of length $ N $, where each $i$-th sample is picked from a distribution $ X_{i} $.

### $$ \dfrac{E(L)}{N} \lt \dfrac{H(X_{1}, ..., X_{N}) + 2}{N} \text{ bits per symbol} $$
### $$ \dfrac{E(L)}{N} \lt H(X) + \dfrac{2}{N} \text{ bits per symbol} \quad \text{if X is i.i.d} $$





