# Observability
> Typically the state is not available for measurement, but we can estimate $ \underline{x}(t) $ from $ \underline{y} $ and $ \underline{u} $

## Observability Matrix

$ n $ is the dimension of $ A $ (**the number of states**).

$$ \Large \color{blue}{
M_{O} = \begin{bmatrix}
C \\
C A \\
\vdots \\
C A^{n-1}
\end{bmatrix}
}
$$

If $ M_{O} $ is **full-rank** (**linearly independent columns** | $ det(M_{O}) \ne 0 $ | $ M_{O} \ \underline{x} \ne \underline{0} $ for $ \underline{x} \ne \underline{0} $), then **the system is observable**.

</br>

> **Initial Condition that does not affect the output for an unobservable $ M_{O}$**
$$ \Large M_{O} \ \underline{x}_{0} = \underline{0} $$ 
$ Range(\underline{x}_{0}) $ are the set of **unobservable states**.
##### Note: $ Range(A) $ is all possible linear combinations from the given columns of $ A $.

</br>

## Observer Canonical Form

$$ 
A = \begin{bmatrix}
-a_{1} & 1 & 0 & \cdots & 0 & 0 \\
-a_{2} & 0 & 1 & \cdots & 0 & 0 \\
\vdots & \vdots & \vdots & \ddots & 0 & 0\\
-a_{n-1} & 0 & 0 & \cdots & 1 & 0 \\
-a_{n} & 0 & 0 & \cdots & 0 & 1\\
\end{bmatrix} \\
$$
$$
C = \begin{bmatrix} 1 & 0 & \cdots & 0 \end{bmatrix}
$$


# Observers

Instead of differentiating signals (bad since amplified noise) we will use a **state observer** (**Luenberger Observer**) which contains **a dynamic model of the system** and whose state $ \hat{x}(t)$ approaches $ x(t) $ as $ t \rightarrow \infty $.


$$ \large
\mathcal{O} = 
\begin{cases}
\dot{\hat{\underline{x}}} = A \hat{\underline{x}} + B \underline{u} + L(\underline{y} - \hat{\underline{y}}) \\
\hat{\underline{y}} = C \hat{\underline{x}}
\end{cases}
$$

Now we will consider $ \large \underline{\epsilon}(t) = \underline{x}(t) − \hat{\underline{x}}(t) $:

This simplifies to $ \large \dot{\underline{\epsilon}} = (A − LC)\underline{\epsilon} $, the solution to this differential equation is $ \underline{\epsilon}(t) = e^{(A-LC)t} \underline{\epsilon}_{0} $.

Therefore we need  $ e^{(A-LC)t} \rightarrow 0 $ as $ t \rightarrow \infty $.

This is achieved if the eigenvalues of $ (A − LC) $ are **large and negative**.

#### We can arbitrarily assign the eigenvalues of $ (A − LC) $ by choice of $ L $ if and only if the system is observable.





