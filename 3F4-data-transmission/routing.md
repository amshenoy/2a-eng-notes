# Routing Algorithms


## Dijkstra (Forward DP)

### Formulation

$$
\large
\begin{array}{|c|c|c|}
\hline
  \text{Current Nodes List} \\ N_{k} & D_{A X_{1}} & \cdots & D_{A X_{i}} & D_{A X_{n}} \\ 
\hline
   N_{0} = A & \cdots & ( D_{A X_{i}} )_{0} = D_{ A X_{i} } & (D_{A X_{i}}, A) & \cdots \\
\hline
   N_{1} = \small \arg\min_{X_{i} \notin \text{Nodes List}}{\large D_{A X_{i}}} & \cdots & ( D_{A X_{i}} )_{1} = \min( D_{ A X_{i} }, D_{ A N_{1} X_{i} } ) & (D_{A N_{1} X_{i}} \scriptsize (< D_{A X_{i}}) \large, N_{1}) & \cdots \\
\hline
   N_{2} = \cdots & \cdots & ( D_{A X_{i}} )_{2} = \min( ( D_{ A X_{i} } )_{1} , D_{ A N_{1} N_{2} X_{i} } ) & (D_{A N_{1} N_{2} X_{i}}\scriptsize (< D_{A N_{1} X_{i}}) \large, N_{2}) & \cdots \\ 
\hline
   \cdots = \cdots & \cdots & \cdots = \min( \cdots , \cdots ) & (\cdots, \cdots) & \cdots \\ 
\hline
   N_{k} = \cdots & \cdots & ( D_{A X_{i}} )_{k} = \min( ( D_{ A X_{i} } )_{k-1} , D_{A N_{1} \cdots N_{k}} ) & (D_{A N_{1} \cdots N_{k}}, N_{k}) & \cdots \\ 
\hline
\end{array}
$$

$ D_{A \cdots X_{i}} = \infty $ if no such path exists


</br>

### Process

1) **Pick start node** 
2) For **each neighbour node** of the start, state **minimum total cost from the start node to the neighbour nodes**.
3) **Pick the neighbour node with the min total cost**
4) **For each neighbour node of the picked node**, state **min total cost from the start node to the nodes**.

</br> </br>

## Bellman-Ford





