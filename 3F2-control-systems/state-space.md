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
