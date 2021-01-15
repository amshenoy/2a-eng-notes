# MOSFETs

Unlike the JFET, which typically works in depletion mode, the MOSFET 
can work in both depletion and enhancement mode.

- In the depletion mode, the transistor is normally ON, and a current flows between the source and drain until a voltage on the gate of the
appropriate polarity and magnitude turns it OFF (like the JFET)

- In the enhancement mode, the transistor is normally OFF, and no current flows between the source and drain until a sufficiently large threshold voltage is applied to the gate. (Energy-saving)

</br>

# MOS Capacitor (Gate Model)

**Metal-Oxide-Semiconductor**

## Capacitance Calculations

Note that these are capacitaces per unit area.

$$ \Large C_{ox} = \dfrac{\epsilon}{d_{ox}} $$

$$ \Large C_{depletion} = \dfrac{\epsilon}{w} $$


$$ \Large C_{total} = \Big( \dfrac{1}{C_{ox}} + \dfrac{1}{C_{depletion}} \Big)^{-1} $$

Minimum total capacitance $ C_{depletion} $ when $ C_{depletion} $ is minimised meaning the depletion region width $ w $ is maximised.

</br><hr></br>

## Operating Modes

### Accumulation ($ V_{G} = +ve $)
When a **positive bias** is applied to the gate $ V_{G} = +ve $, we get an **accumulation of electrons at the interface between the oxide and the semiconductor**.

This accumulation of electrons causes $ E_{C} $ and $ E_{V} $ lines to bend at the interface by $ e V_{s} $ due to a surface potential $ V_{s} $. 

</br>

### Depletion ($ V_{G} = -ve $)

If a **negative bias** is applied to the gate $ V_{G} = -ve $, then we get a depletion region formed in the semiconductor at the interface with the oxide.

From **Poisson's equation**/**Gauss' Law of Electrostatics**:
$$ \mathcal{E} = \dfrac{-eN_{D}}{\epsilon} w $$

$$ \large V_{s} = \dfrac{eN_{D}}{\epsilon} \dfrac{w^{2}}{2} $$


$$ \large \color{blue}{ -V_{G} = V_{ox} + V_{s} } \qquad (V_{G} + V_{ox} + V_{s} =0 ) $$

</br>

### Inversion ($ V_{G} = ---ve $)

If we continue to increase the magnitude of the negative voltage applied to the gate then the band bending in the semiconductor will increase.

* $ E_{V} $ moves closer to $ E_{F}$, $ E_{C} $ moves further away from $ E_{F} $.

* **Strong Inversion** - Holes in the valence band increases and electrons in the conduction band decreases until there as many holes at the interface as electrons in the bulk. ($ N_{C} = N_{V} $ at this point)

* Depletion region cannot increase more at this point. Increasing the magnitude of the voltage further, only increases the number of holes at the surface.
 


</br>

(Insert Diagram here)

</br><hr></br>


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

$ \Large \color{blue}{ V_{F} = \dfrac{kT}{e} \ \ln\dfrac{N_{D}}{n_{i}} } $

$ \Large \color{blue}{ w(V_{s}) = \Big( \dfrac{2\epsilon V_{s}}{e N_{D}}\Big)^{\dfrac{1}{2}} } $

**Max Depletion Width just at Strong Inversion** &emsp; $ \Large \color{blue}{ w_{max} = w(2 V_{F})} $

**Charge per unit area in Depletion Region at Strong Inversion** &emsp; $ \Large \color{blue}{ Q_{d} = e N_{D} \ w_{max} } $

</br>

### Threshold Voltage

We want to know the threshold voltage $ V_{T} $ which has to be applied to the gate to induce strong inversion.

$ C_{ox} $ - Oxide Capacitance per unit area

$ Q_{d} $ - Charge per unit area in **Depletion Region** at Strong Inversion 

$$ \large V_{T} = V_{\text{Flat Band}} -\dfrac{Q_{d}}{C_{ox}} - 2 V_{F} $$

$ V_{\text{Flat Band}} $ is the voltage needed to flatten the bands between the metal and the semiconductor. If we considered $ V_{\text{Flat Band}} = 0 $, we would be assuming that $ \phi_{m} = \phi_{sc} $. 

Additionally extra charges are introduced into the system due to the oxide, namely the following:

1) Interface Trapped charges $ Q_{it} $

2) Fixed Oxide charges $ Q_{f} $

3) Oxide Trapped charges $ Q_{ot} $

4) Mobile Ionic charges $ Q_{m} $


Putting all these charges under a single term effective charge $ Q_{i} $, we get the following expression for the threshold voltage:

$$ \Large \color{blue}{ V_{T} = \underbrace{ \Big( \dfrac{\phi_{m} - \phi_{sc}}{e} -\dfrac{Q_{i}}{C_{ox}} \Big) }_{V_{FB}} -\dfrac{Q_{d}}{C_{ox}} - 2 V_{F} } $$



</br>



### Deep Depletion
The depletion region can be extended much further if the voltage applied to the metal is varied more rapidly than the time required to produce the holes (time for strong inversion).

We can calculate the time required for strong inversion to occur $\tau_{inv}$.

$ t_{inv} $ - Thickness of the inversion layer </br>
$ \tau_{inv} $ - Time for inversion </br>
$ v_{s} $ - Scattering velocity </br>
$$ \large \color{blue}{ J = e p_{0} \ v_{s} } $$
$$ \large \color{blue}{ Q_{s} = e n_{0} \ t_{inv} = J \ \tau_{inv} } $$

$$ \large \therefore \tau_{inv} = \dfrac{n_{0}}{p_{0}} \dfrac{t_{inv}}{v_{s}} $$


</br><hr></br>


# Full Model (Source-Drain added)

We are now in a position to determine how the drain source current $ I_{DS} $ in a MOSFET depends on the voltages applied to the gate
and drain. We will continue to use the PMOS device working in an inversion regime as our example.

### 5 Operating Situations
1) **Flat band** condition with **no net space charge in the source drain channel**

2) **Accumulation** with **additional majority carriers in the channel**

3) **Depletion** with **no free carriers in the channel**

4) **Inversion** with a **layer of minority carriers in the channel above a depletion region**

5) **Strong inversion** where there are **as many minority carriers in the channel as majority carriers in the bulk**



</br>

## Inversion Region Charge

If we apply a gate-source voltage $ V_{GS} $, then $ V_{GS} - V_{\text{Flat Band}} $ will be dropped across the oxide $ \dfrac{Q_{s}}{C_{ox}} $ and a surface potential $ V_{s} $ in the semiconductor:

$$ \Large \color{blue}{ V_{GS} - V_{FB} = - \dfrac{Q_{s}}{C_{ox}} - V_{s} } $$


$ \large \color{blue}{ Q_{s} = Q_{d} + Q_{inv} } $ The total charge in the semiconductor is the charge in the depletion region plus the charge in the inversion region.

Rearranging for $ Q_{inv} $ and substituting $ V_{T} = V_{FB} -\dfrac{Q_{d}}{C_{ox}} - 2 V_{F} $:

$$ \Large Q_{inv} = - C_{ox} (V_{GS} - (V_{T} + 2V_{F} - V_{s})) $$ 

If we now apply a voltage $V_{DS}$ to the drain, then this will induce a voltage $V(x)$ in the channel at the interface between the semiconductor and the oxide with respect to the source.

$ \large V_{s} = 2 V_{F} - V(x) $

$$ \Large \therefore Q_{inv} = - C_{ox} (V_{GS} - V_{T} -V(x)) $$

</br>

## Drain-Source Current

Using the resistivity law $ R = \dfrac{\rho L }{A}$ (Note $ \rho $ is resitivity not charge density ):

$ \mu_{hFE} $ is the **field effect mobility**, ie. the measured electron mobility $ \mu_{e} $.

$$ \large
\begin{align*}
\delta R &= \dfrac{\rho \delta x}{ t_{inv} \ W} \\
&= \dfrac{\delta x}{ e \ p_{inv} \ t_{inv} \ \mu_{hFE} \ W} \\
\delta R &= \dfrac{\delta x}{ Q_{inv} \ \mu_{hFE} \ W} \\
\end{align*}
$$

$ \large dV(x) = I_{DS} \ dR $

Substitute for $ dR $ and rearrange for $ I_{DS} $:
$ \large \therefore  Q_{inv} \ \mu_{hFE} \ W \ dV(x) = I_{DS} dx $

Integrate for appropriate conditions, $ W = \text{Gate Width} $, $ L = \text{Drain-Source Length}$:
$$ 
\large 
\begin{align*}
\int_{0}^{L} I_{DS} dx &= \int_{0}^{V_{DS}} Q_{inv} \ \mu_{hFE} \ W \ dV(x) \\
I_{DS} &= \dfrac{ \mu_{hFE} \ W }{L} \int_{0}^{V_{DS}} Q_{inv} \ dV(x) \\
I_{DS} &= \dfrac{ \mu_{hFE} \ W }{L} \int_{0}^{V_{DS}} - C_{ox} (V_{GS} - V_{T} -V) \ dV \\
I_{DS} &= - \dfrac{ C_{ox} \ \mu_{hFE} \ W }{L} \ \Big( (V_{GS} - V_{T}) V_{DS} - \dfrac{V_{DS}^2}{2} \Big)\\
\end{align*}
$$

</br>

## Drain-Source Current Saturation

This expression for $ I_{DS} $ is valid up to a saturation current $ I_{DS sat} $ (up to the saturation region).

Saturation occurs at $ V_{DS} = V_{GS} – V_{T} $:

$$ \therefore I_{DS sat} = - \dfrac{ C_{ox} \ \mu_{hFE} \ W }{L} \ \dfrac{V_{DS}^{2}}{2} = - \dfrac{ C_{ox} \ \mu_{hFE} \ W }{L} \ \dfrac{(V_{GS} – V_{T})^{2}}{2} $$

</br>

As discussed for the JFET, for short channel lengths the carrier velocity saturates:
$ \large I_{DS sat} = - W C_{ox} V_{DS} v_{s} = - W C_{ox} (V_{GS} - V_{T}) v_{s} $

</br>

## Model Conductances

### Small Signal Channel Conductance
$$ \large g_{s} = \dfrac{\partial I_{DS}}{\partial V_{DS}} $$

### Mutual Transconductance
$$ \large g_{m} = \dfrac{\partial I_{DS}}{\partial V_{GS}} $$

## Applications

#### DRAM - 1-Bit Capacitor

#### Flash Memory - Floating Gate


