# Z-Transform

Z-transform is the discrete version of the Laplace Transform.

$$ \large \mathcal{Z}\{x_{k}\} = \sum_{k=-\infty}^{\infty} x_{k}[k] z^{-k} $$

## Derivation

Consider a continuous time signal $ x(t) $ sampled at rate $ T $ to be $ x_{\delta}(t)$ :
$$ 
\begin{align*}
x_{\delta}(t) &= \sum_{n=-\infty}^{\infty} x(t) \delta(t-nT) \\
&= \sum_{n=-\infty}^{\infty} x(nT) \delta(t-nT) \\
\end{align*}
$$

Taking the Laplace transform of the sampled signal:
$$
\begin{align*}
X_{\delta}(s) & = \mathcal{L}\{x_{\delta}(t)\} \\
& = \int_{t=-\infty}^{\infty} x_{\delta}(t) e^{-st} dt \\
& = \int_{t=-\infty}^{\infty} \Big( \sum_{n=-\infty}^{\infty} x(kT) \delta(t-nT) \ \Big) \ e^{-st} dt \\
& = \sum_{n=-\infty}^{\infty} x(kT) \underbrace{\Big( \int_{t=-\infty}^{\infty} \delta(t-nT) \ e^{-st} dt \Big)}_{\large e^{-snT}} \\
& = \sum_{n=-\infty}^{\infty} x(nT) \ e^{-snT} \\
\end{align*}
$$

As $ T $ is a constant determined by the sampling rate and the integral is of the range $[-\infty,\infty]$, we can replace $ nT $ with the index $ k $:

$$ \therefore X_{\delta}(s) = \sum_{k=-\infty}^{\infty} x(k) \ e^{-sk} $$

We have now discretised the Laplace transform however the signal is still dependent on the signal function $ x(t) $. We can remove this dependency by considering the function $ x(k) $ to be an array $ x_{k} $ indexed by $ k $. 
$$ \therefore X_{\delta}(s) = \sum_{k=-\infty}^{\infty} x_{k}[k] \ e^{-sk} $$

We can rewrite the above as the Z-transform by substituting $ z = e^{s} $:
$$ \therefore X_{\delta}(z) = \sum_{k=-\infty}^{\infty} x_{k}[k] \ z^{-k} $$

Therefore instead of considering the transform applied to a function of time $ x_{d}(t) $, we can also consider it as a transform applied to the array $ x_{k} $ giving us the Z-transform:
$$ \large \mathcal{Z}\{x_{k}\} = \sum_{k=-\infty}^{\infty} x_{k}[k] z^{-k} $$

## Properties
We can denote the Z-transform of $ x_{k} $ as either $ \overline{x}(z), X(z) $ or $ \mathcal{Z}\{ x_{k} \} $.

### Linearity
### $$ \color{blue} { \mathcal{Z}\{ a x_{k} + b y_{k} \} = a \mathcal{Z}\{ x_{k} \} + b \mathcal{Z}\{ y_{k} \}  } $$

$ \color{red}{ \text{Note*: } \textbf{ Differentiation} \text{ and } \textbf{Integration} \text{ are both linear operators and hence can be substituted for the constants a and b.} } $

### Time-Delay
### $$ \color{green} {  \mathcal{Z}\{ x_{k-1} \} = z^{-1} \mathcal{Z}\{ x_{k} \}  } $$

More specifically:
$  \mathcal{Z}\{ x_{k-1} \} = x_{-1} + z^{-1} \mathcal{Z}\{ x_{k} \} \quad \text{ as } x_{-1} = 0  $
### Time-Advance
### $$ \color{green} {  \mathcal{Z}\{ x_{k+1} \} = -zx_{0} + z \mathcal{Z}\{ x_{k} \}  } $$

### Scaling
### $$ \color{green} {  \mathcal{Z}\{ r^{k} x_{k} \} = \overline{x}(r^{-1} z)  } $$

### Initial-Value Theorem
### $$ \color{green} {  \lim_{z \rightarrow \infty} \overline{x}(z) = \lim_{z \rightarrow \infty} \mathcal{Z}\{ x_{k} \} = x_{0}  } $$

### Final-Value Theorem
### $$ \color{green} {  \lim_{z \rightarrow 1} (z-1) Y(z) = \lim_{z \rightarrow \infty} \mathcal{Z}\{ x_{k} \} = x_{0}  } $$

### Convolution

$$ \color{green} { \{x_{k}\}*\{y_{k}\} = \sum^{k}_{i=0} x_{i} y_{k-i} = \sum^{k}_{i=0} x_{k-i} y_{i} } $$

### $$ \color{green} {  \mathcal{Z}\{ x_{k} * y_{k} \} = \mathcal{Z}\{ x_{k} \} \mathcal{Z}\{ y_{k} \} = \overline{x}(z) \overline{y}(z)  } $$

</br>

## Standard Transforms

### $$ \color{blue} { \mathcal{Z}\{ p^{k} \} = \dfrac{1}{1-pz^{-1}} } $$
Example:
#### $$ \color{blue} { \mathcal{Z}\{ k p^{k} \} } = \color{red}{?} $$

$$ \color{blue} { \mathcal{Z}\{ k p^{k} \} } 
\\ = \color{blue} { \mathcal{Z}\{ p \cdot k p^{k-1} \} } 
\\ = \color{blue} { p \cdot \mathcal{Z}\{ k p^{k-1} \} } 
\\ = \color{blue} { p \cdot \mathcal{Z}\{ \dfrac{d}{dp} \Big( p^{k} \Big) \} } 
\\ = \color{blue} { p \cdot \dfrac{d}{dp} \Big( \mathcal{Z}\{ p^{k} \} \Big) } 
\\ = \color{blue} { p \cdot \dfrac{d}{dp} \Big( \dfrac{1}{1-pz^{-1}} \Big) } 
\\ = \color{blue} { p \cdot \Big( \dfrac{z^{-1}}{(1-pz^{-1})^{2}} \Big) } 
$$
</br>
### $$
\therefore \color{blue} { \mathcal{Z}\{ k p^{k} \}  = \dfrac{p z^{-1}}{(1-pz^{-1})^{2}} }
$$
Letting **p = 1**,
### $$
\therefore \color{blue} { \mathcal{Z}\{ k \}  = \dfrac{z^{-1}}{(1-z^{-1})^{2}} }
$$

### Step Response
### $$
\color{blue} { \mathcal{Z}\{ h_{k} \}  = H(z) = \dfrac{1}{1-z^{-1}} }
$$
$$ Y(z) = G(z) H(z) $$

#### Steady-State Value
Using the final-value theorem:
$$ \color{purple}{ \lim_{k \rightarrow \infty} y(k) = G(1) } $$

### Harmonic Response
### $$
\text{If } \quad u_{k} = \cos(\omega kT) \\
\color{blue} { y_{k} = |G(e^{j \omega T})| \cos(\omega k T + \angle G(e^{j \omega T})) }
$$
#### Note*: The function in the output is the same as the function in the input. (ie. $\sin \rightarrow \sin$)
</br>

## Inverting a Z-domain Signal
Always **convert top-heavy z-fraction into a proper fraction + constant**. Constant in z-domain adds to the initial term in k-domain (ie. if $ X(z) = C + f(z) $ then $ \mathcal{Z^{-1}}\{ X(z) \} = \{x_{k}\} = \{f_{0}+C, f_{1}, ..., f_{n} \} $ ).

$ \small \text{Note*: Derivable using the fact that } \mathcal{Z^{-1}}\{ 1 \} = \delta(k) $

#### Analytical Inversion
Using **partial fractions** to break-down a system function into **standard transforms**.

#### Numeric Inversion
Using **long division** to generate first-few terms to hopefully **extrapolate pattern**.

</br><hr>

## Solving LDEs

### $ \color{red} { \text{LDE} \enspace y_{k} \overbrace{\longrightarrow}^{\text{Z-Transform}} Y(z) \overbrace{\longrightarrow}^{\text{Inverse Z-Transform}} y(k) \text{ or } \{y_{k}\} } $ 

## Laplace to Z Transform

### $ \color{green} { F(s) \overbrace{\longrightarrow}^{\text{Tables}} f(t) \rightarrow f(kT) \text{ exponentials } \overbrace{\longrightarrow}^{\text{Z-Transform}} F(z) } $ 
