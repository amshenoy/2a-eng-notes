# PN Junction

PN Junction is a **bipolar** device (conduction due to both holes and electrons).

"Abrupt junction" model

* Abrupt junction
* Negligible recombination
* No fields outside junction


## Charge Neutrality 

$ e N_{A} x_{n} + e N_{D} x_{p} = 0 $

$$ \Large N_{A} x_{n} + N_{D} x_{p} = 0 $$


## Contact Potential

Equations for the contact potential in terms of Fermi levels and doping:

$$ 
\begin{align*}
\large eV_{0} &= E_{Fn} - E_{Fp} \\
&= (E_{C} - kT \ln(\dfrac{N_{C}}{N_{D}})) - (\overbrace{E_{V}}^{ \text{Consider} \ 0} + kT \ln(\dfrac{N_{V}}{N_{A}})) \\ \\

\text{From Law of Mass Action: } \quad & n_{i}^{2} = N_{C} N_{V} \enspace e^{\dfrac{-E_{c}}{kT}} \\ \\

eV_{0} &= kT \ln(\dfrac{N_{A}N_{D}}{n_{i}^{2}})
\end{align*}
$$


($ \color{orange}{ kT \approx 0.0259 \ eV } $ at room temperature) 

</br>

## Depletion Region

### Contact Potential
Equation of contact potential in terms of depletion region widths.

$$ \large \dfrac{d^{2}V}{dx^{2}} = \dfrac{-\rho}{\epsilon} \qquad (\text{from Poisson's Equation})$$

(eg. $ \rho = - e N_{A} = e N_{D} $)

$$ E(x) = \dfrac{dV}{dx} = \int \dfrac{d^{2}V}{dx^{2}} dx $$

#### Boundary Conditions

For p-type side: $ E(-x_{p}) = 0 $

For n-type side: $ E(x_{n}) = 0 $

Common: $ V(0) = 0 $

</br>
Find $ V_{n} $ using conditions for n-type side.
Find $ V_{p} $ using conditions for p-type side.

$ \Large V_{0} = V_{n} - V_{p} $

$$ \Large V_{0} = \dfrac{e}{2 \epsilon} (N_{A} x_{p}^{2} + N_{D} x_{n}^{2}) $$




</br>

### Depletion Region Width

$$ \Large w = x_{n} - x_{p} $$

Rearrange **contact potential** $ V_{0} $ to make $ x_{n} $ and $ x_{p} $ the subjects.

Also use **charge neutrality substitution** to get two separate equations for $ x_{n} $ and $ x_{p} $.

$ w = f(N_{A}, N_{D}) $

**Note: For a one-sided junction (denoted for example by $p_{+}n$), the width of one of the depletion regions with the highest concentration is very small in comparison to the other. (ie.$ N_{A} >> N_{D} $ or $ N_{D} >> N_{A}$ )**

$ w = \Big( \dfrac{2 \epsilon V_{0}}{e N_{D}} \Big)^{\dfrac{1}{2}} $ for ($ N_{A} >> N_{D} $)

**Note: The side with a greater dopant concentration has a smaller region. Therefore the depletion region forms in the side with a lower dopant concentration.**


</br>

## Junction Capacitance

Capacitance (per unit area) $ \large C_{A} = \dfrac{C}{A} = \dfrac{\epsilon}{w} $ (Parallel-Plate Analogy)


</br>

## Bias Application

Applying a bias voltage changes the Fermi levels in the semiconductor.



Applying a **positive bias voltage** $ V_{\text{app}} $ to the **positive side**, For all the equations above $ V_{0} $ changes to $ V_{0} - V_{\text{app}} $.

The Fermi level changes in the following way:

<img src="/assets/fermi-bias.png"></img>

</br><hr>

# $ P^{+}N $ Junction

On each side of the depletion region at equilibrium, the mass action law applies.

$ \large n_{n0} \ p_{n0} = n_{i}^{2} $

$ \large n_{p0} \ p_{p0} = n_{i}^{2} $

## Minority Carrier Current Density

**This part involves serious use of second order ODEs! Practice and optimise speed and accuracy!**

</br>

We can use the **continuity equation** to find $ p(x) $ and $ n(x) $ by considering $ \large \Delta p = p - p_{n0} $ and $ \large \Delta n = n - n_{p0} $.  

Using the contact potential equation $ e V_{0} = kT \ln(\dfrac{N_{A}N_{D}}{n_{i}^{2}}) $ alongside the mass-action law $ n p = n_{i}^{2} $, we can find the **boundary condition** for $ p(0) $ and $ n(0) $.  

This gives the following solutions for an applied bias $ V_{a} $:
$$ \color{blue}{ \Large p = p_{n0} \ e^{\frac{eV_{a}}{kT}} e^{-\frac{x}{L_{h}}} = \Big( N_{A} e^{-\frac{eV_{0}}{kT}} \Big) e^{\frac{eV_{a}}{kT}} e^{-\frac{x}{L_{h}}} } $$

$$ \color{blue}{ \Large n = n_{p0} \ e^{\frac{eV_{a}}{kT}} e^{-\frac{x}{L_{e}}} = \Big( N_{D} e^{-\frac{eV_{0}}{kT}} \Big) e^{\frac{eV_{a}}{kT}} e^{-\frac{x}{L_{e}}} } $$

</br>


To find the **minority carrier current density** $ J_{s} $, we need to find $ J_{h} $ and $ J_{e} $ separately where $ J_{e} $ is the **electron current density on the p-type side** and $ J_{h} $ is the **hole current density on the n-type side**:

Ignoring drift:

$ \large J_{h} = -e D_{h} \dfrac{dp}{dx} |_{x=0} $

$ \large J_{e} = -e D_{e} \dfrac{dn}{dx} |_{x=0} $


### Minority Current Density Diagram

* Consider the minority carriers on each side $ P $ and $ N $. 
 
* Minority carrier concentration on both sides must meet at the depletion region at a constant.

* The **lower doped side** has a **higher initial minority carrier concentration** and a **higher value upon reaching the depletion region** than the **higher doped side**.

* In **forward bias**, the **minority carrier concentrations must increase** going towards the depletion region.

* In **reverse bias**, the **minority carrier concentration must decrease to 0** going towards the depletion region. (However the current diagram is the same as before with lower values (only current that flows is due to drift current across the junction).)

</br>

<insert diagram here>


</br>

$ \Large J_{s} = J_{h} + J_{e} $ 

</br>

$ L_{h} $ and $ L_{e} $ are known as **carrier diffusion lengths**.

$ \large L = (D \tau)^{\frac{1}{2}} $ ie. $ \large \dfrac{D}{L} = \dfrac{L}{\tau} $

$$ \color{blue}{ \Large J_{s} = e (\dfrac{D_{h}}{L_{h}} \dfrac{n_{i}^{2}}{ N_{D}} + \dfrac{D_{e}}{L_{e}} \dfrac{n_{i}^{2}}{N_{A}}) } $$

</br>

$$
\large
\begin{align*}
J_{s} &= e (\dfrac{L_{h}}{\tau_{h}} \dfrac{n_{i}^{2}}{ N_{D}} + \dfrac{L_{e}}{\tau_{e}} \dfrac{n_{i}^{2}}{N_{A}}) \\ \\
J_{s} &= e (\dfrac{L_{h}}{\tau_{h}} p_{n0} + \dfrac{L_{e}}{\tau_{e}} n_{p0})
\end{align*}
$$




