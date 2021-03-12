# Controllability & State Feedback

</br>

## Controllability Matrix

$ n $ is the dimension of $ A $ (**the number of states**).

$$ \Large \color{blue}{
M_{C} = \begin{bmatrix}
B & A B & \cdots & A^{n-1} B
\end{bmatrix}
}
$$

If $ M_{C} $ is **full-rank** (**linearly independent columns** | $ det(M_{C}) \ne 0 $ | $ M_{C} \ \underline{x} \ne \underline{0} $ for $ \underline{x} \ne \underline{0} $), then **the system is controllable**.

> **Reachable states of $ M_{C} $** &emsp; $ \large \color{blue}{  Range(M_{C}) } $ </br> </br>
> **Unreachable states of $ M_{C} $** &emsp; $ \large M_{C}^{T} \ \underline{x} = \underline{0} \qquad Range(\underline{x}) $ are the set of **unreachable states**.


#### Note: There can be multiple solutions for unreachable states $ \underline{x} $ in which case the unreachable states are represented by a matrix of vectors where the columns are the linearly independent solutions.

</br>

## Controller Canonical Form

$$ 
A = \begin{bmatrix}
-a_{1} & -a_{2} & -a_{3} & \cdots & -a_{n-1}  & -a_{n} \\
0 & 1 & 0 & \cdots & 0 & 0 \\
0 & 0 & 1 & \cdots & 0 & 0\\
\vdots & \vdots & \vdots & \ddots & \vdots & \vdots \\
0 & 0 & 0 & \cdots & 1 & 0 \\
0 & 0 & 0 & \cdots & 0 & 1\\
\end{bmatrix} \\
$$
$$
B = \begin{bmatrix} 1 \\ 0 \\ \vdots \\ 0 \end{bmatrix}
$$


# Controller (State Feedback)

The response of a system is largely determined by the location of its closed loop poles. We can use state feedback to assign the closed-loop poles.

Given $ \dot{\underline{x}} = A \underline{x} + B \underline{u} $:
 
Let $ \large \color{blue}{ \underline{u} = −K \underline{x} + M \underline{r} } $.

$$ \large \dot{\underline{x}} = (A - BK)\underline{x} + B M \underline{r} $$

#### We can arbitrarily assign the eigenvalues of $ (A − BK) $ by choice of $ K $ if and only if the system is controllable.

##### Note: This is analogous to setting the eigenvalues of $ A - LC $ by selecting $ L $ (provided the system is observable) to create an observer. 

</br>

### Steady-State Gain

Supposing that we want $ \underline{y} \rightarrow \underline{r} $ as $ t \rightarrow \infty $:

In **steady-state** &ensp; $ \large \dot{\underline{x}} = 0 $ ie. $ \underline{x} = (A-BK)^{-1} B M \underline{r} $:

$ \underline{y} = C \underline{x} = C (A-BK)^{-1} B M \underline{r} $


We need to select $ M $ such that the steady-state gain becomes $ I $ so that $ \underline{y} \rightarrow \underline{r} $ as $ t \rightarrow \infty $.



</br> <hr> </br>

## Duality Controllability-Observability

> The pair ($ A $, $ B $) is **controllable** if and only if the pair ($ A^{T} $, $ B^{T} $ ) is **observable** (and vice versa).

</br>

**Possible Statements**:

($ A $, $ B $) is **controllable** if ($ A^{T} $, $ B^{T} $ ) is **observable**.

($ A $, $ C $) is **observable** if ($ A^{T} $, $ C^{T} $ ) is **controllable**.

</br>

### Proof by Gramians

($ A $,$ B $) is **controllable** if $ W_{C}(t) $ is **nonsingular for any t**:

$$ W_{C}(t) = \int_{0}^{t} e^{A \tau} B B^{T} e^{A^{T} \tau} d\tau $$


($ A $,$ C $) is **observable** if $ W_{O}(t) $ is **nonsingular for any t**:

$$ W_{O}(t) = \int_{0}^{t} e^{A^{T} \tau} C^{T} C e^{A \tau} d\tau $$

Substitute $ A = A^{T} $ and $ C = B^{T} $ to show equivalence.




$$ \large \dot{\underline{x}} = (A - BK)\underline{x} + B M \underline{r} $$

#### We can arbitrarily assign the eigenvalues of $ (A − BK) $ by choice of $ K $ if and only if the system is controllable.

##### Note: This is analogous to setting the eigenvalues of $ A - LC $ by selecting $ L $ (provided the system is observable) to create an observer. 

</br>

### Steady-State Gain

Supposing that we want $ \underline{y} \rightarrow \underline{r} $ as $ t \rightarrow \infty $:

In **steady-state** &ensp; $ \large \dot{\underline{x}} = 0 $ ie. $ \underline{x} = (A-BK)^{-1} B M \underline{r} $:

$ \underline{y} = C \underline{x} = C (A-BK)^{-1} B M \underline{r} $


We need to select $ M $ such that the steady-state gain becomes $ I $ so that $ \underline{y} \rightarrow \underline{r} $ as $ t \rightarrow \infty $.



