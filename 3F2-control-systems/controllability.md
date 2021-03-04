# Controllability & State Feedback

$$ M_{C} = \begin{bmatrix}
B & A B \hdots A^{n-1} B
\end{bmatrix}
$$

# Controllability & State Feedback

</br>

## Controllability Matrix

$ n $ is the dimension of $ A $ (**the number of states**).

$$ M_{C} = \begin{bmatrix}
B & A B & \cdots & A^{n-1} B
\end{bmatrix}
$$

If $ M_{C} $ is **full-rank** (**linearly independent columns** | $ det(M_{C}) \ne 0 $ | $ M_{C} \ \underline{x} \ne \underline{0} $ for $ \underline{x} \ne \underline{0} $), then **the system is controllable**.

</br>

## Controller Canonical Form

$$ 
A = \begin{bmatrix}
-a_{1} & -a_{2} & -a_{3} & \cdots & -a_{n-1}  & -a_{n} \\
1 & 0 & 1 & \cdots & 0 & 0 \\
0 & 1 & \vdots & \ddots & 0 & 0\\
0 & 0 & 0 & \cdots & 1 & 0 \\
0 & 0 & 0 & \cdots & 0 & 1\\
\end{bmatrix} \\
$$
$$
B = \begin{bmatrix} 1 \\ 0 \\ \vdots \\ 0 \end{bmatrix}
$$


# State Feedback

The response of a system is largely determined by the location of its closed loop poles. We can use state feedback to assign the closed-loop poles.

Given $ \dot{\underline{x}} = A \underline{x} + B \underline{u} $, we can let $ \underline{u} = −K \underline{x} + M \underline{r} $:

$$ \dot{\underline{x}} = (A - BK)\underline{x} + B M \underline{r} $$

#### We can arbitrarily assign the eigenvalues of $ (A − BK) $ by choice of $ K $ if and only if the system is controllable.

##### Note: This is analogous to setting the eigenvalues of $ A - LC $ by selecting $ L $ (provided the system is observable) to create an observer. 

</br>

### Steady-State Gain

Supposing that we want $ \underline{y} \rightarrow \underline{r} $ as $ t \rightarrow \infty $:

In steady-state $ \dot{\underline{x}} = 0 $ ie. $ \underline{x} = (A-BK)^{-1} B M \underline{r} $:

$ \underline{y} = C \underline{x} = C (A-BK)^{-1} B M \underline{r} $


We need to select $ M $ such that the steady-state gain becomes $ I $ so that $ \underline{y} \rightarrow \underline{r} $ as $ t \rightarrow \infty $.

