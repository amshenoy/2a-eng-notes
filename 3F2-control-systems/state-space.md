# State-Space Systems

The essence of a **causal dynamical system** is its **memory**: </br>
The **present output** $ y(t_{1})$ depends on **past inputs** $ u(t) \quad t \le t_{1} $.

The **states** are a **set of system variables** that represent this **memory**.

#### State Property
$ \underline{x}(t_{1}) $ can always be determined from $ \underline{x}(t_{0}) $ and $ \{ \underline{u}(t),  t_{0} \le t \le t_{1} \}$.

</br>

## State-Space Model

$ \mathcal{S} $ is the standard form for a **state-space dynamical system model**:

$$ 
\large
\mathcal{S} = \begin{cases}
\underline{\dot{x}}(t) = \underline{f}( \ \underline{x}(t), \ \underline{u}(t), \ t \ ) \\
\underline{y}(t) = \underline{g}( \ \underline{x}(t), \ \underline{u}(t), \ t \ )
\end{cases}
$$

For **linear time-invariant dynamical systems** we simply use the standard form:
$$ 
\large
\mathcal{S} = \begin{cases}
\underline{\dot{x}}(t) = \overbrace{A}^{n \times n}\underline{x}(t) + \overbrace{B}^{n \times m} \underline{u}(t) \\
\underline{y}(t) = \underbrace{C}_{p \times n} \underline{x}(t) + \underbrace{D}_{p \times m} \underline{u}(t)
\end{cases}
$$


## State-Space Trajectories

For $ \underline{\dot{x}}(t) = A \underline{x}(t) $ where $ \underline{x} $ consists of 2 states (ie. 2D), the eigenvalues of $ A $ give the eigenvectors of the state-space system.

$ |\lambda|_{max} = \text{"Fast Eigenvector"} \\
 |\lambda|_{min} = \text{"Slow Eigenvector"} $

$ \lambda < 0 (-ve) $ - Eigenvector goes towards equilibrium (**Converges**) </br>
$ \lambda > 0 (+ve) $ - Eigenvector goes away from equilibrium (**Diverges**)

#### Note: 2-state non-linear system can have a limit cycle and an equilibrium point. (Van der Pol Oscillator)

</br>

## Solutions of Linear State Equations

$$ 
\large
\mathcal{S} = \begin{cases}
\underline{\dot{x}}(t) = A\underline{x}(t) + B \underline{u}(t); \quad \underline{x}(0) = \underline{x}_{0} \\
\underline{y}(t) = C\underline{x}(t) + D\underline{u}(t)
\end{cases}
$$

Taking the **Laplace transform**:
$$ \large
\begin{align*}
s\underline{X}(s) - \underline{x}_{0} &= A \underline{X}(s) + B \underline{U}(s) \\
\therefore \underline{X}(s) &= (sI-A)^{-1} (\underline{x}_{0} + B \underline{U}(s) ) \\ \\
\underline{Y}(s) &= C \underline{X}(s) + D \underline{U}(s) \\
&= C (sI-A)^{-1} (\underline{x}_{0} + B \underline{U}(s) )  + D \underline{U}(s) \\
\therefore \underline{Y}(s) &= \underbrace{ C (sI-A)^{-1} \underline{x}_{0} }_{\text{Initial Condition Response}} + \underbrace{ ( C(sI-A)^{-1} B + D) \underline{U}(s) }_{\text{Input Response}}
\end{align*}
$$

For $ \underline{x}_{0} = \underline{0} $, $ \underline{Y}(s) = G(s) \underline{U}(s) $:

$$ G(s) = C(sI-A)^{-1} B + D $$

### Poles of G(s)

$ |G(p)| \rightarrow \infty $

$ \Large det(sI-A) = 0 $

However the **poles of $ G(s) $  can be a subset of the eigenvalues of $ A $** meaning that not all the eigenvalues of $ A $ are poles of $ G(s) $:

$$ \large \text{Poles of } G(s) \subseteq \text{Eigenvalues of } A   \qquad ( \ G(s) \text{ is minimal } ) $$

</br>

### Initial Condition Response
For $\underline{u}(t) = \underline{0} $:

$$ \large
\begin{align*}
\underline{X}(s) &= (sI-A)^{-1} \underline{x}_{0} \\
\underline{x}(t) &= \mathcal{L}^{-1}\{ (sI-A)^{-1} \} \ \underline{x}_{0} \\ \\
&= \mathcal{L}^{-1}\{ \sum_{k \ge 0} A^{k} s^{-(k+1)} \} \ \underline{x}_{0} \\
\underline{x}(t) &= e^{A t}
\end{align*}
$$

### Change of State Coordinates

If $ A = T^{-1} \hat{A} T $, then $ A^{k} = T^{-1} \hat{A}^{k} T $ :

$$ \begin{align*}
e^{At} &= \sum_{k=0}^{\infty} A^{k} \dfrac{t^{k}}{k!} \\
&= \sum_{k=0}^{\infty} T^{-1} \hat{A}^{k} T \dfrac{t^{k}}{k!} \\
&= T^{-1} ( \sum_{k=0}^{\infty}  \hat{A}^{k} \dfrac{t^{k}}{k!} ) T \\
e^{At} &= T^{-1} e^{\hat{A}t} T \\
\end{align*}
$$


