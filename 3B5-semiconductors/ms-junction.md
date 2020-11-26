# Metal-Semiconductor Interface


For an **Ohmic contact** between a metal and a semiconductor:

$$ \large \phi_{\text{p-type}} \lt \phi_{m} \lt \phi_{\text{n-type}} $$

For a **Schottky contact**, flip the above statement.

</br>

$$ \Large \color{blue}{ \text{Ohmic} = (\phi_{m} > \phi_{sc}) \cdot \text{p-type} } $$

Set the **values of the booleans** to either $ 1 $ (True) or $ -1 $ (False) for easy formula for finding whether **Ohmic or Schottky**.

</br>

### Metal Side

$ E_{F} = E_{C} = E_{V} $

$$ \Large \color{blue}{ \phi_{m} = E_{\text{vac}} - E_{F} } $$

### Semiconductor Side

$ E_{F \ s} $ is the extrinsic Fermi level of the SC.
$ \chi $ is the electron affinity of SC (a material property). Note that at this point even $ \phi_{SC} $ must be explicitly calculated due to the effect of doping.  

$$ \Large \color{blue}{ \phi_{sc} = E_{\text{vac}} - E_{F \ s} } $$ 
$$ \Large \color{blue}{ \chi = E_{\text{vac}} - E_{c} } $$


# M-S Junction

As before for a PN-junction when we create a junction the difference in work functions causes an exchange of electrons creating a contact potential present across the depletion region present entirely within the semiconductor. 

MS-Junction is a **unipolar** device.


## Contact Potential

$$ \Large \color{blue}{ eV_{0} = \phi_{m} - \phi_{sc} } $$


## Depletion Region

### Contact Potential
Equation of contact potential in terms of depletion region widths.

$$ \large \dfrac{d^{2}V}{dx^{2}} = \dfrac{-\rho}{\epsilon} \qquad (\text{from Poisson's Equation})$$

(eg. $ \rho = - e N_{A} = e N_{D} $)

$$ E(x) = \dfrac{dV}{dx} = \int \dfrac{d^{2}V}{dx^{2}} dx $$

#### Boundary Conditions
$ E(w) = 0 $

$ V(w) = V_{0} $


Rearrange to find depletion region width $ w $.
 
</br>

## Junction Capacitance

Capacitance (per unit area) $ \large C_{A} = \dfrac{C}{A} = \dfrac{\epsilon}{w} $ (Parallel-Plate Analogy)

More specifically from $ C = \dfrac{dQ}{dV} = \dfrac{d(\rho w)}{dV} $


</br><hr>



# Schottky Contact

#### Key Points for Diagram

**Lines**
* $ E_{F \ m} $ and $ E_{F \ s} $ Fermi levels are aligned (Anderson's rule)
* $ E_{\text{vac}} $ lines of M and SC are now continuous.

**Changes**
* At interface, $ E_{c} = E_{F \ s} + ( \phi_{m} - \chi ) $
* $ E_{\text{vac}} $ and $ E_{c} $ drops by $ \phi_{m} - \phi_{sc} = e (V_{0} - V_{app}) $ as a plateau after the depletion region

</br>


## Current Flow

### Net Current Flow
$$ I_{net} = I_{F} - I_{R} $$

In equilibrium, $ I_{F} = I_{R} $.

In forward bias, $ I_{F} >> I_{R} $.

In reverse bias, $ I_{R} >> I_{F} $.


</br>

Schottky barrier diode is a uni-polar device (ie. we only need to consider one type of carrier flow).

</br>

## Thermionic Emission Theory

### M to SC

### $ J_{m-sc} $ is independent of applied forward bias $ V_{a} $ (not quite true due to Schottky effect)

$$ \color{blue}{ \large J_{m-sc} =  A^{*} \enspace T^{2} e^{-\dfrac{e \ (\phi_{m} - \phi_{sc})}{kT}} (- 1) } $$ 

where $ A^{*} = A \dfrac{m^{*}}{m} $ and $ A = \dfrac{4\pi e m k^{2}}{h^{3}} $ is Richardson's constant.

</br>

### SC to M

$$ \color{blue}{ \large J_{sc-m} =  A^{*} \enspace T^{2} e^{-\dfrac{e \ (\phi_{m} - \phi_{sc})}{kT}} (e^{\dfrac{e V_{a}}{kT}} - 1) } $$ 

where $ A^{*} = A \dfrac{m^{*}}{m} $ and $ A = \dfrac{4\pi e m k^{2}}{h^{3}} $ is Richardson's constant.


</br><hr>


# Ohmic Contact
For an Ohmic contact, the M and SC are essentially separate. Diagram is dependent on properties defined in introduction.








