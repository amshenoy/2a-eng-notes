# MOSFETs

Unlike the JFET, which typically works in depletion mode, the MOSFET 
can work in both depletion and enhancement mode.

- In the depletion mode, the transistor is normally ON, and a current flows between the source and drain until a voltage on the gate of the
appropriate polarity and magnitude turns it OFF (like the JFET)

- In the enhancement mode, the transistor is normally OFF, and no current flows between the source and drain until a sufficiently large threshold voltage is applied to the gate. (Energy-saving)

</br>

# MOS Capacitor (Gate Model)

**Metal-Oxide-Semiconductor**

## Accumulation ($ V_{G} = +ve $)
When a **positive bias** is applied to the gate $ V_{G} = +ve $, we get an **accumulation of electrons at the interface between the oxide and the semiconductor**.

This accumulation of electrons causes $ E_{C} $ and $ E_{V} $ lines to bend at the interface by $ e V_{s} $ due to a surface potential $ V_{s} $. 

</br>

## Depletion ($ V_{G} = -ve $)

If a **negative bias** is applied to the gate $ V_{G} = -ve $, then we get a depletion region formed in the semiconductor at the interface with the oxide.

From **Poisson's equation**:
$$ \mathcal{E} = \dfrac{-eN_{D}}{\epsilon} w $$

$$ \large V_{s} = \dfrac{eN_{D}}{\epsilon} \dfrac{w^{2}}{2} $$


$$ \large \color{blue}{ -V_{G} = V_{ox} + V_{s} } \qquad (V_{G} + V_{ox} + V_{s} =0 ) $$

</br>

## Inversion ($ V_{G} = ---ve $)

If we continue to increase the magnitude of the negative voltage applied to the gate then the band bending in the semiconductor will increase.

* $ E_{V} $ moves closer to $ E_{F}$, $ E_{C} $ moves further away from $ E_{F} $.

* **Strong Inversion** - Holes in the valence band increases and electrons in the conduction band decreases until there as many holes at the interface as electrons in the bulk. ($ N_{C} = N_{V} $ at this point)

* Depletion region cannot increase more at this point. Increasing the magnitude of the voltage further, only increases the number of holes at the surface.
 


</br>

(Insert Diagram here)

</br>


## Surface Space Charge

**Gauss' Law of Electrostatics**
$$ \large \nabla \cdot \mathcal{E} = \color{blue}{ \dfrac{d\mathcal{E}}{dx} = \dfrac{\rho}{\epsilon} } $$

$ \color{blue}{ \rho = e (N_{D}^{+} - N_{A}^{-} + p - n ) } $ where $ \color{blue}{ p = p_{0} \exp(\dfrac{-eV}{kT}) } $ and $ \color{blue}{ n = n_{0} \exp(\dfrac{eV}{kT}) } $.

$ \color{blue}{ p_{0} = N_{A}^{-} } \text{ and } \color{blue}{ n_{0} = N_{D}^{+} } \quad (\text{if all carriers due to ionised dopants}) $

$$ \therefore \dfrac{d\mathcal{E}}{dx}  = \dfrac{e}{\epsilon} (N_{D}^{+} - N_{A}^{-} + p_{0} \exp(\dfrac{-eV}{kT}) - n_{0} \exp(\dfrac{eV}{kT}) ) $$

Multiply each side by the respective side of $ \mathcal{E} dx = - dV $.

$$ \mathcal{E} d\mathcal{E} = - \dfrac{e}{\epsilon} (N_{D}^{+} - N_{A}^{-} + p_{0} \exp(\dfrac{-eV}{kT}) - n_{0} \exp(\dfrac{eV}{kT}) ) dV $$

Integrate both sides from $ 0 $ to the variable $ V_{s} $ or $ \mathcal{E}_{s} $ to find $ \mathcal{E}_{s} $ in terms of $ V_{s} $.

$$ \mathcal{E}_{s} = (2 \int_{0}^{V_{s}} - \dfrac{e}{\epsilon} (N_{D}^{+} - N_{A}^{-} + p_{0} \exp(\dfrac{-eV}{kT}) - n_{0} \exp(\dfrac{eV}{kT}) ) dV )^{1/2} $$
From **Gauss' Law of Electrostatics** used before, the surface charge per unit area $ Q_{s} $ is given by the following equation:
$$ \Large \color{blue}{ Q_{s} = - \epsilon \ \mathcal{E}_{s} } $$

</br>

__Note: Surface Potential $ V_{s} $ is analogous to Contact Potential $ V_{0} $__ 

</br>

## Strong Inversion

$$ \large \color{blue}{ V_{s \ \text{Strong Inversion}} \ge 2 V_{F}  = 2 \ \dfrac{kT}{e} \ \ln\dfrac{N_{D}}{n_{i}} } $$

$ \large \color{blue}{ w(V_{s}) = \Big( \dfrac{2\epsilon V_{s}}{e N_{D}}\Big)^{\dfrac{1}{2}} } $

**Max Depletion Width before Strong Inversion** &emsp; $ \Large \color{blue}{ w_{max} = w(2 V_{F})} $

**Deep Depletion** - The depletion region can be extended much further if the voltage applied to the metal is varied more rapidly than the time required to produce the holes (time for strong inversion).

</br>

We can calculate the time required for strong inversion to occur $\tau_{inv}$.

$ t_{inv} $ - Thickness of the inversion layer </br>
$ \tau_{inv} $ - Time for inversion </br>
$ v_{s} $ - Scattering velocity </br>
$$ \large \color{blue}{ J = e p_{0} \ v_{s} } $$
$$ \large \color{blue}{ Q_{s} = e n_{0} \ t_{inv} = J \ \tau_{inv} } $$

$$ \large \therefore \tau_{inv} = \dfrac{n_{0}}{p_{0}} \dfrac{t_{inv}}{v_{s}} $$

</br><hr></br>


# Full Model (Source-Drain added)
