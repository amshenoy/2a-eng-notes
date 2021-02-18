# State-Space Systems

</br>

The essence of a **causal dynamical system** is its **memory**: </br>
The **present output** $ y(t_{1})$ depends on **past inputs** $ u(t) \quad t \le t_{1} $.

The **states** are a **set of system variables** that represent this **memory**.

### State Property
$ \underline{x}(t_{1}) $ can always be determined from $ \underline{x}(t_{0}) $ and $ \{ \underline{u}(t),  t_{0} \le t \le t_{1} \}$.

</br>

# State-Space Model

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


## Equilibrium Points

**All derivatives equal 0. Solve for the state variables to find the equilibrium points.**

</br>

## State-Space Trajectories

For $ \underline{\dot{x}}(t) = A \underline{x}(t) $ the eigenvalues of $ A $ give the eigenvectors of the state-space system.

$ |\lambda|_{max} = \text{"Fast Eigenvector"} \\
 |\lambda|_{min} = \text{"Slow Eigenvector"} $

$ \large \lambda < 0 (-ve) $ - (**Converges**) Eigenvector goes towards equilibrium  </br>
$ \large \lambda > 0 (+ve) $ - (**Diverges**)
Eigenvector goes away from equilibrium 

$ \large \lambda \in \mathbb{C} $ - (**Rotational motion towards eqlibrium**) Eigenvalue is a complex number (imaginary component gives the rotational motion)

#### Note: 2-state non-linear system can have a limit cycle and an equilibrium point. (Van der Pol Oscillator)

</br>

## Linearisation (around eqlb)

Suppose we have **some differential equation that we cannot explicitly convert** to state-space form. We can instead **linearise about the equilibrium to get the state-space form**:

$ \Large \underline{\dot{x}} = \underline{f}(\underline{x}, \underline{u}) \\ \Large \underline{y} = \underline{g}(\underline{x}) $

</br>

Linearises to:

$ \Large \delta \underline{\dot{x}} = A \delta\underline{x} + B \delta \underline{u} $

$ \Large \delta \underline{y} = C \delta \underline{x} $

where $ \large A = \dfrac{\partial \underline{f}}{ \partial \underline{x}} \ , \  B = \dfrac{\partial \underline{f}}{ \partial \underline{u}} \ , \ C = \dfrac{\partial \underline{g}}{ \partial \underline{x}} $



</br><hr></br>


# Solutions of Linear State Equations

$$ 
\large \color{blue}{
\mathcal{S} = \begin{cases}
\underline{\dot{x}}(t) = A\underline{x}(t) + B \underline{u}(t); \quad \underline{x}(0) = \underline{x}_{0} \\
\underline{y}(t) = C\underline{x}(t) + D\underline{u}(t)
\end{cases}
}
$$

## Laplace Domain Solutions

Taking the **Laplace transform**:
$$ \large
\begin{align*}
s\underline{X}(s) - \underline{x}_{0} &= A \underline{X}(s) + B \underline{U}(s) \\
\therefore \underline{X}(s) &= (sI-A)^{-1} (\underline{x}_{0} + B \underline{U}(s) ) \\ \\
\underline{Y}(s) &= C \underline{X}(s) + D \underline{U}(s) \\
&= C (sI-A)^{-1} (\underline{x}_{0} + B \underline{U}(s) )  + D \underline{U}(s) \\
\end{align*}
$$
$$ \large \color{blue}{ \underline{Y}(s) = \underbrace{ C (sI-A)^{-1} \underline{x}_{0} }_{\text{Initial Condition Response}} + \underbrace{ ( C(sI-A)^{-1} B + D) \underline{U}(s) }_{\text{Input Response} \ G(s) \underline{U}(s)} } $$

#### Note: We can create composite systems from this model as well as find the frequency response.

</br>

### Transfer Function

For $ \underline{x}_{0} = \underline{0} $, $ \underline{Y}(s) = G(s) \underline{U}(s) $:

$$ \large \color{purple}{ G(s) = C(sI-A)^{-1} B + D } $$

**Poles of G(s)** &emsp; $ \large \color{blue}{ det(sI-A) = 0 } \qquad \small (|G(p)| \rightarrow \infty) $

The **poles of $ G(s) $  are a subset of the eigenvalues of $ A $** meaning that not all the eigenvalues of $ A $ are poles of $ G(s) $:

$$ \large \text{Poles of } G(s) \subseteq \text{Eigenvalues of } A   \qquad ( \ G(s) \text{ is minimal } ) $$

</br>

## Time Domain Solutions

##### Multiplication in Laplace domain is convolution in time domain and vice versa.

$$ \large \color{blue}{ \underline{x}(t) = e^{At} \underline{x}_{0} + \int_{0}^{t} e^{A(t- \tau)} B \underline{u}(\tau) d\tau } $$

$$ \large \color{blue}{ \underline{y}(t) = C \Big( e^{At} \underline{x}_{0} + \int_{0}^{t} e^{A(t- \tau)} B \underline{u}(\tau) d\tau \Big) \ + D \underline{u}(t) } $$

</br>

### Impulse Response Matrix

$$ \large \color{purple}{ H(t) = \mathcal{L}^{-1}(G(s)) = C e^{At} B + D \delta(t) \qquad t\ge 0 } $$


</br><hr></br>


## Initial Condition Response

### State Transition Matrix
$$ \large \color{red}{ \mathcal{L}^{-1}\{(sI-A)^{-1}\} = e^{At} = T e^{\Lambda t} T^{-1} } $$

</br>

For $\underline{u}(t) = \underline{0} $:

#### Method 1

$$ \large
\begin{align*}
\underline{X}(s) &= (sI-A)^{-1} \underline{x}_{0} \\
\underline{x}(t) &= \mathcal{L}^{-1}\{ (sI-A)^{-1} \} \ \underline{x}_{0}
\end{align*}
$$

$$ \Large \color{blue}{ \underline{x}(t) = \mathcal{L}^{-1}\{ (sI-A)^{-1} \} \ \underline{x}_{0} } $$

##### Note: If we have calculated $ (sI-A)^{-1} $, it will most likely be easier to compute $ \mathcal{L}^{-1}\{ (sI-A)^{-1} \} $, therefore use this method.

</br></br>

#### Method 2

$$
\large
\begin{align*}
\underline{x}(t) &= \mathcal{L}^{-1}\{ \sum_{k \ge 0} A^{k} s^{-(k+1)} \} \ \underline{x}_{0} \\
\underline{x}(t) &= e^{A t} \underline{x}_{0} 
\end{align*}
$$

$$
\Large \color{blue}{ \underline{x}(t) = e^{A t} \underline{x}_{0} }
$$

##### Change of State Coordinates

Let $ \large A = T \Lambda T^{-1} $, then $ \large A^{k} = T \Lambda^{k} T^{-1} $ :

$ T $ - Matrix of eigenvectors of $ A $ as columns (does not have to be normalised)

$$ \begin{align*}
e^{At} &= \sum_{k=0}^{\infty} A^{k} \dfrac{t^{k}}{k!} \\
&= \sum_{k=0}^{\infty} T \Lambda^{k} T^{-1} \dfrac{t^{k}}{k!} \\
&= T ( \sum_{k=0}^{\infty}  \hat{A}^{k} \dfrac{t^{k}}{k!} ) T^{-1} 
\end{align*}
$$

$$ \Large \color{green}{ e^{At} = T e^{\Lambda t} T^{-1} } $$


##### Note: $ e^{At} $ is not just the exponential of every term! The diagonal elements are the only elements for which this works! Hence the exponential of a diagonal matrix is indeed a diagonal matrix with the exponential of the diagonal terms. This is why we need to use the above method to compute.

</br>

#### Matrix Exponent Rules
$ e^{A+B} = e^{A} e^{B} $ only when $ AB = BA $. Since $ t $ is a scalar, we can split $ e^{A(t_{1} + t_{2})} = e^{A t_{1}} e^{A t_{2}} = e^{A t_{2}} e^{A t_{1}} $

$ (e^{A t})^{-1} = e^{-At} $

$ \dfrac{d}{dt}(e^{At}) = A e^{At} = e^{At} A $

$ \int (e^{At}) dt = A^{-1} ( e^{At} - 1) = A^{-1} e^{At} - A^{-1} $

</br><hr></br>

## Change of State Variables

Consider the transformation $ \large \underline{z} = T^{-1} \underline{x} $ and a system equation $ \underline{\dot{x}} = A \underline{x} + B \underline{u} $ where $ T $ is the matrix of eigenvectors of $ A $.

$$ \large \begin{align*}
\underline{\dot{x}} &= A \underline{x} + B \underline{u} \\ \\
T^{-1} \underline{\dot{x}} &= T^{-1} A \underline{x} + T^{-1} B \underline{u} \\ \\
\underline{\dot{z}} &= T^{-1} A (T \underline{z}) + T^{-1} B \underline{u} \\
\underline{\dot{z}} &= (T^{-1} A T) \underline{z} + T^{-1} B \underline{u} \\ \\
\underline{\dot{z}} &= \Lambda \underline{z} + T^{-1} B \underline{u} \\
\end{align*}
$$


