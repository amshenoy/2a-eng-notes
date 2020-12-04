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


$$ \large V_{G} + V_{ox} + V_{s} = 0 $$

</br>

## Inversion ($ V_{G} = ---ve $)

If we continue to increase the magnitude of the negative voltage applied to the gate then the band bending in the semiconductor will increase.

* $ E_{V} $ moves closer to $ E_{F}$, $ E_{C} $ moves further away from $ E_{F} $.

* **Strong Inversion** - Holes in the valence band increases and electrons in the conduction band decreases until there as many holes at the interface as electrons in the bulk. ($ N_{C} = N_{V} $ at this point)

* Depletion region cannot increase more at this point. Increasing the magnitude of the voltage further, only increases the number of holes at the surface.
 

</br>


## Surface Space Charge



</br><hr></br>


# Full Model (Source-Drain added)
