# Free-Electron Model

## Fermi Function

The Fermi function $ f(E) $ is a probability function (not probability density) which outputs the probability of an electron occupying an energy state $ E $ under thermal equilibrium. $ k $ is the Boltzmann constant and $ T $ is the temperature. This will be useful for finding the probability of an electron being in the valence or the conduction band.

$$ \large f(E) = \dfrac{1}{1+e^{\frac{E-E_{f}}{kT}}} $$

The function is dependent on the Fermi energy level $ E_{f} $ which is in turn dependent on the effective density of energy states $ N_{c} $ (in the conduction band) and $ N_{v} $ (in the valence band).

#### Properties
$$ 0 \leq f(E) \leq 1 $$
$$ f(E_{f}) = \frac{1}{2} $$
$$ \small \text{Probability of empty energy state} \qquad \large 1 - f(E)$$

## Density of States

This section is the derivation of the density of states function for semiconductors.


#### Density of states in a semiconductor = Density per unit volume per unit energy of the number of solutions to Schrödinger's equation

To derive the function, we will be considering the following:

* The semiconductor can be modeled as an infinite quantum well in which electrons with effective mass $ m* $ are free to move with the base of the well being $ E = 0 $.

* Semiconductor is a cube with side $ L $. (This does not actually matter we are calculating the density of states per unit volume) 

* $ \psi = A \text{sin}(k_{x} x) + B \text{cos}(k_{x} x) $ 

* The wavefunction must be zero at the infinite barriers of the well. $ \psi(0) = \psi(L) = 0 \qquad \therefore B = 0 $ and $ k_{x} = \dfrac{n \pi}{L} \qquad \text{ for } n \in \mathcal{N} $

* Repeat the analysis in the y and z direction giving $ k_{y} = k_{z} = k_{x} = \dfrac{n \pi}{L} $

* The **total number of solutions** $ N $ with a different value for $ k_{x} $, $ k_{y} $ and $ k_{z} $ and with a magnitude of the wavevector less than $ k $ is obtained by calculating the **volume of $ \dfrac{1}{8} $ of a sphere with radius $ k $ divided by the volume of the cube corresponding to a single solution $ (\dfrac{\pi}{L})^{3} $.** A **factor of two** is added to account for the two possible spins of each solution.
$$ N = 2 \cdot \dfrac{ \Big( \dfrac{1}{8} \cdot \dfrac{4}{3} \pi k^{3} \Big) }{ \Big( \dfrac{\pi}{L} \Big)^{3} } $$

##### Note*: We are essentially trying to calculate the number of cubes that can fit in an eighth of a sphere where each cube can hold two electrons with opposite spins.

Now we can calculate the density of states per unit volume per unit energy $ g(E) $ by differentiating density of states per unit volume $ N $ with respect to energy $ E $:
 
$ g(E) = \dfrac{dN}{dE} = \dfrac{dN}{dk} \dfrac{dk}{dE}$

From before we know that $ E = \dfrac{\hbar k^{2}}{2m^{*}} $ 

$ \therefore \dfrac{dk}{dE} = \dfrac{m^{*}}{\hbar k} \qquad \text{where} \qquad  k = \dfrac{\sqrt{2m^{*}E}}{\hbar} $ 

Expanding and simplifying $ g(E) $ gives the following:
$$ g(E) = \dfrac{\pi k^{2}}{ \Big( \dfrac{\pi}{L} \Big)^{3} } \dfrac{m^{*}}{\hbar k} = \dfrac{ 8 \pi \sqrt{2} }{ h^{3} } (m^{*})^{\frac{3}{2}} \sqrt{E} \qquad (E \geq 0) $$

The above is an important result and will help us in understanding semiconductors. Stated below are the functions for the conduction and valence density of states per unit energy:

$$ \therefore g_{c}(E) = \dfrac{ 8 \pi \sqrt{2} }{ h^{3} } (m_{n}^{*})^{\frac{3}{2}} \sqrt{E-E_{c}} \qquad (E \geq E_{c}) $$

$$ \therefore g_{v}(E) = \dfrac{8 \pi \sqrt{2}}{h^{3}} (m_{p}^{*})^{\frac{3}{2}} \sqrt{E_{v}-E} \qquad (E \leq E_{v}) $$

### Density of States

For the scope of this topic, we will assume that we have some function $ g_{c}(E) $ which outputs the density of states in the conduction band and $ g_{v}(E) $ respectively in the valence band although this can be derived from the Schrodinger's equation. 

$$ g_{c}(E) = \dfrac{ 8 \pi \sqrt{2} }{ h^{3} } (m_{n}^{*})^{\frac{3}{2}} \sqrt{E-E_{c}} \qquad (E \geq E_{c}) $$

$$ g_{v}(E) = \dfrac{8 \pi \sqrt{2}}{h^{3}} (m_{p}^{*})^{\frac{3}{2}} \sqrt{E_{v}-E} \qquad (E \leq E_{v}) $$

Therefore we can now write an equation for the density of occupied energy states per unit volume and per unit energy $ n(E) $ and $ p(E) $ as the following:

$$ n(E) = g_{c}(E) \cdot f(E) \qquad \text{and} \qquad p(E) = g_{v}(E) \cdot (1 - f(E)) $$

We can now attain the carrier concentrations by integrating with respect to energy.

$$ \therefore n = \int_{E_{c}}^{\infty} g_{c}(E) f(E) dE $$
$$ \therefore p = \int_{-\infty}^{E_{f}} g_{v}(E) (1-f(E)) dE $$

The above functions have no analytical solutions however by restricting ourselves to non-degenerate semiconductors, we can replace the Fermi function with the Boltzmann distribution function (a simple exponential) which can be analytically solved to find the carrier concentrations:

$$ \large n = \int_{E_{c}}^{\infty} g_{c}(E) e^{-\frac{E-E_{f}}{kT}} dE = N_{c} \ e^{-\frac{E_{c}-E_{f}}{kT}} $$

$$ \large p = \int_{-\infty}^{E_{v}} g_{v}(E) e^{-\frac{E_{f}-E}{kT}} dE = N_{v} \ e^{-\frac{E_{f}-E_{v}}{kT}} $$

where $ N_{c} $ is the effective density of states in the conduction band and $ N_{v} $ is the effective density of states in the valence band:

$$ N_{c} = 2 \Big( \dfrac{ 2 \pi \ m_{n}^{*} \ k T }{h^{2}} \Big) ^ \dfrac{3}{2} $$
$$ N_{v} = 2 \Big( \dfrac{ 2 \pi \ m_{p}^{*} \ k T }{h^{2}} \Big) ^ \dfrac{3}{2} $$


</br>

### Fermi Energy Level
The energy of the highest filled state is called the Fermi energy (E_{F}).

#### Intrinsic Fermi Level
Consider the Fermi energy level of an intrinsic semconductor at thermal equilibrium to be $ E_{i} $ . This is roughly the midpoint of $ E_{v} $ and $ E_{c} $:

$$ E_{i} \approx \dfrac{E_{c} + E_{v}}{2} $$

But more explicitly:

$$ E_{i} = \dfrac{E_{c} + E_{v}}{2} + \dfrac{1}{2} kT \ln \dfrac{N_{v}}{N_{c}} = \dfrac{E_{c} + E_{v}}{2} + \dfrac{3}{4} kT \ln \dfrac{m_{p}^{*}}{m_{n}^{*}} $$

#### Extrinsic Fermi Level (Non-Degenerate)
Consider the Fermi energy level $ E_{f} $ of an extrinsic semconductor at thermal equilibrium to be $ E_{e} $ . By rearranging the equations for the carrier concentrations, we get the following equations:

##### N-Type
$$ E_{e} = E_{i} + kT \ln \dfrac{n}{n_{i}} $$

##### P-Type
$$ E_{e} = E_{i} - kT \ln \dfrac{p}{n_{i}} $$

$ n $ and $ p $ can be found by solving the quadratic doping equations which can in turn be used to calculate the Fermi energy level for an extrinsic semiconductor.

##### Solutions
The following can be easily derived but nonetheless the solutions for $ n $ and $ p $ from the doping equations have been shown below:

$$ n = \dfrac{1}{2} \Big( - (N_{D}^{+} - N_{A}^{-}) + \sqrt{(N_{D}^{+} - N_{A}^{-})^{2} + 4n_{i}^{2}} \Big) $$

$$ p = \dfrac{1}{2} \Big( + (N_{D}^{+} - N_{A}^{-}) + \sqrt{(N_{D}^{+} - N_{A}^{-})^{2} + 4n_{i}^{2}} \Big) $$

</br>

### Intrinsic Carriers

As derived above, we now have equations for the carrier concentrations that are dependent on the fermi level:

$$ \large n_{| \small E_{f} = E_{i}} = N_{c} \ e^{-\frac{E_{c}-E_{i}}{kT}} $$
$$ \large p_{| \small E_{f} = E_{i}} = N_{v} \ e^{-\frac{E_{i}-E_{v}}{kT}} $$

Using mass action law:
$$ n_{i}^{2} = N_{c} N_{v} \ e^{-\frac{E_{g}}{kT}} \qquad \small (E_{g} = E_{c} - E_{v}) $$

$$ \large n_{i} = \sqrt{N_{c} N_{v}} \ e^{-\frac{E_{g}}{2kT}} $$

##### Note*: $ n=p=n_{i} $ for intrinsic semiconductors so each of the above equations is also equal to $ n_{i} $
