# Bipolar Junction Transistor (BJT)

BJTs are **bipolar** devices (involves both types of charge carriers).

$ P^{++} N P $ (or $ N^{--} P N $)


We focus on $ P^{++} N P \quad (EBC) $ junction:

\[
\begin{array}{c|cc|cc|cc|c}
\qquad \qquad & \qquad & \qquad & \qquad & \qquad & \qquad & \qquad & \qquad \\
              &   &   &   & I_{B}  &   &  & \\
              &   &   &   &  \uparrow  &   &  & \\ \hline
              &   &   & I_{En} &    &   &  & \\
              &   &   & \uparrow & &   &  & \\
I_{E}         & \text{Emitter} (E) &   & \text{Base} (B) &   & \text{Collector} (C) &  & I_{C}          \\
\longrightarrow   &   &   &   &   &   &  & \longrightarrow   \\ \hline
              &   &  I_{Ep} &   & I_{C}  & \\ 
              &   &   \longrightarrow &   & \longrightarrow  &  \\
              &   &   &   &   &   &  & \\
\end{array}
\]


**Base Transport** Factor &emsp; $ \large B = \dfrac{I_{C}}{I_{E_{p}}} $

**Emitter Injection** Efficiency &emsp; $ \large \gamma = \dfrac{I_{Ep}}{I_{E}} = \dfrac{I_{Ep}}{I_{Ep} + I_{En}} $

Current Transfer Ratio (**Overall** Gain) &emsp; $ \large \alpha = \dfrac{I_{C}}{I_{E}} = B \gamma $

**Base Current** 

$ \begin{align*}
\large I_{B} &= I_{E} - I_{C} \\ &= I_{En} + (I_{Ep} - I_{C}) \\ &= I_{En} + (1-B) I_{Ep} \end{align*}
$

**Base-Collector** Current Gain &emsp; $ \beta = \dfrac{I_{C}}{I_{B}} = \dfrac{\alpha}{1-\alpha} $

</br>

## Carrier Current Density
$ x $ is the distance into the base.

We can use the same definitions as from the PN-junction:

These are derived from the mass action law: &emsp;
$ p_{n0} = \dfrac{n_{i}^{2}}{N_{D}} \qquad n_{p0} = \dfrac{n_{i}^{2}}{N_{A}} $


### Base Diffusion (Boundary Conditions)

$$ \large \Delta p_{n}(0) = p_{n0} (e^{\frac{eV_{EB}}{kT}} - 1) \approx p_{n0} e^{\frac{eV_{EB}}{kT}} $$

$$ \large \Delta p_{n}(W_{b}) = p_{n0} (e^{\frac{eV_{CB}}{kT}} - 1) \approx -p_{n0} $$


### Continuity Solution

$$ \Delta p_{n}(x) = C e^{\dfrac{-x}{L_{h}}} + D e^{\dfrac{x}{L_{e}}}$$

### Current Densities

$$ \large \color{blue}{ J_{Ep} = e \dfrac{D_{h}}{L_{h}} \Delta p_{n}(0) \enspace \coth(\dfrac{W_{b}}{L_{h}}) = e \dfrac{D_{h}}{L_{h}} p_{n0} (e^{\frac{eV_{EB}}{kT}} - 1) \enspace \coth(\dfrac{W_{b}}{L_{h}}) } $$

$$ \large \color{blue}{ J_{C} = e \dfrac{D_{h}}{L_{h}} \Delta p_{n}(0) \enspace \text{cosech}(\dfrac{W_{b}}{L_{h}}) = e \dfrac{D_{h}}{L_{h}} p_{n0} (e^{\frac{eV_{EB}}{kT}} - 1) \enspace \text{cosech}(\dfrac{W_{b}}{L_{h}}) } $$

$$ \large J_{B} \approx e \dfrac{D_{h}}{L_{h}} \Delta p_{n}(0) \tanh(\dfrac{W_{b}}{2L_{h}}) = e \dfrac{D_{h}}{L_{h}} p_{n0} (e^{\frac{eV_{EB}}{kT}} - 1) \tanh(\dfrac{W_{b}}{2L_{h}}) $$


$$ \large J_{En} = e \dfrac{D_{e}}{L_{e}} \Delta n_{p}(0) = e \dfrac{D_{e}}{L_{e}} n_{p0} (e^{\frac{eV_{EB}}{kT}} - 1) $$

</br>

#### $ J_{Ep} $ is required to be large and hence $ W_{b} << L_{h} $ is required.

</br>

$ \large B = \dfrac{J_{C}}{J_{Ep}} = \text{sech}(\dfrac{W_{b}}{L_{h}}) \approx 1 - \dfrac{1}{2} \dfrac{W_{b}^{2}}{L_{h}^{2}} $

</br>

$
\begin{align*}
\small \gamma = \dfrac{J_{Ep}}{J_{Ep} + J_{En}} 
= \dfrac{1}{1 + \dfrac{ \dfrac{D_{e}}{L_{e}} n_{p0} }{ \dfrac{D_{h}}{L_{h}} p_{n0} \coth(\dfrac{W_{b}}{L_{h}}) } } 
= \dfrac{1}{1 + \dfrac{ \dfrac{D_{e}}{L_{e}} \dfrac{n_{i}^{2}}{N_{A}} }{ \dfrac{D_{h}}{L_{h}} \dfrac{n_{i}^{2}}{N_{D}} \coth(\dfrac{W_{b}}{L_{h}}) } }
= \Big( 1 + \dfrac{D_{e}}{D_{h}} \dfrac{L_{h}}{L_{e}} \dfrac{N_{D}}{N_{A}} \tanh(\dfrac{W_{b}}{L_{h}}) \Big)^{-1}
\end{align*}
$

($ L_{h} \tanh(\dfrac{W_{b}}{L_{h}}) \approx W_{b} $ for $ W_{b} << L_{h} $)

$ \therefore \Large \gamma \approx \dfrac{1}{1 + \dfrac{D_{e}}{D_{h}} \dfrac{W_{b}}{L_{e}} \dfrac{N_{D}}{N_{A}}} = \dfrac{1}{1 + \dfrac{ \dfrac{D_{e}}{L_{e}} \dfrac{n_{i}^{2}}{N_{A}} }{ \dfrac{D_{h}}{L_{h}} \dfrac{n_{i}^{2}}{N_{D}} } } $


</br>

### BJT Improvements

* **Reduce** $ W_{b} $ (width of Base) for easy diffusion but not too much as to cause current crowding.

* **n-doping negative concentration gradient across Base** (improved $ E_{p} $ hole current and frequency response)

</br>


# Heterojunction Bipolar Transistor (HBT)






