# Carrier Density

## Fermi Function

The Fermi function $ f(E) $ is a probability function (not probability density) which outputs the probability of an electron occupying an energy state $ E $ under thermal equilibrium.

$$ \large f(E) = \dfrac{1}{1+e^{\frac{E-E_{F}}{k_{B}T}}} $$

The function is dependent on the Fermi energy level $ E_{F} $ which is in turn dependent on the effective density of energy states $ N_{c} $ (in the conduction band) and $ N_{v} $ (in the valence band).

$$ \small \text{Probability of empty energy state} \qquad \large 1 - f(E)$$


#### Note*: At **absolute zero**, the fermi function is ideal for integration!
$$ f(E) = \begin{cases}
1 \quad E < E_{f} \\
0 \quad E \ge E_{f} \\
\end{cases}
$$



</br>

## Density of States

This section is the derivation of the density of states function for semiconductors.


#### Density of states in a semiconductor = Density per unit volume per unit energy of the number of solutions to Schrödinger's equation

To derive the function, we will be considering the following:

* The semiconductor can be modeled as an infinite quantum well in which electrons with effective mass $ m* $ are free to move with the base of the well being $ E = 0 $.

* Semiconductor is a cube with side $ L $. (This does not actually matter we are calculating the density of states per unit volume) 

* $ \psi = A \text{sin}(k_{x} x) + B \text{cos}(k_{x} x) $ 

* The wavefunction must be zero at the infinite barriers of the well. $ \psi(0) = \psi(L) = 0 \qquad \therefore B = 0 $ and $ k_{x} = \dfrac{2 \pi}{L} n \qquad \text{ for } n \in \mathcal{N} $

* Repeat the analysis in the y and z direction giving $ k_{y} = k_{z} = k_{x} = \dfrac{2 \pi}{L} n $

* The **total number of solutions** $ N $ with a different value for $ k_{x} $, $ k_{y} $ and $ k_{z} $ and with a magnitude of the wavevector less than $ k $ is obtained by calculating the **volume of a sphere with radius $ k $ divided by the volume of the cube corresponding to a single solution $ (\dfrac{2\pi}{L})^{3} $.** A **factor of two** is added to account for the two possible spins of each solution.
$$ N = 2 \cdot \dfrac{ \Big( \dfrac{4}{3} \pi k^{3} \Big) }{ \Big( \dfrac{2\pi}{L} \Big)^{3} } $$

##### Note*: We are essentially trying to calculate the number of cubes that can fit in a sphere where each cube can hold two electrons with opposite spins.

We could also consider an infinitesimal k-space $\delta k$.
$$ \delta E = \dfrac{\hbar^2}{m} k \delta k $$
$$ \delta V = 4 \pi k^2 \delta k $$
$$ 2 \text{ states in volume } (\dfrac{2\pi}{L}) ^3 $$
$$ \delta N = 2 \dfrac{4 \pi k^2 \delta k}{(\dfrac{2 \pi}{L})^3} $$
$$ \delta n = \dfrac{\delta N}{L^3} = \dfrac{k^2}{\pi^2} \delta k $$

</br>

Now we can calculate the **density of states per unit energy** $ g(E) $ by differentiating the density of states $ N $ with respect to energy $ E $:

$ g(E) = \dfrac{dN}{dE} = \dfrac{dN}{dk} \dfrac{dk}{dE}$

From before we know that $ E = \dfrac{(\hbar k)^{2}}{2m^{*}} $ 

$ \therefore \dfrac{dk}{dE} = \dfrac{m^{*}}{\hbar k} \qquad \text{where} \qquad  k = \dfrac{\sqrt{2m^{*}E}}{\hbar} $ 

Expanding and simplifying $ g(E) $ gives the following:
$$ g(E) = \dfrac{\pi k^{2}}{ \Big( \dfrac{\pi}{L} \Big)^{3} } \dfrac{m^{*}}{\hbar k} = \dfrac{ 8 \pi \sqrt{2} }{ h^{3} } (m^{*})^{\frac{3}{2}} \sqrt{E} \qquad (E \geq 0) $$

### $$ \color{blue}{ g(E) = \dfrac{(2m^{*})^\dfrac{3}{2}}{2 \pi^{2} \hbar^{3}} \sqrt{E} } $$
The above is an important result and will help us in understanding semiconductors. 

Note that the density of states $ N $ can be calculated for an energy interval using the following equation:
#### $$ N = \int g(E) dE $$

## States Occupation

Using $ g(E)$, we can derive a function $ g_{c}(E) $ which outputs the density of states in the conduction band and $ g_{v}(E) $ respectively in the valence band.

$$ g_{c}(E) = \dfrac{ 8 \pi \sqrt{2} }{ h^{3} } (m_{n}^{*})^{\frac{3}{2}} \sqrt{E-E_{c}} \qquad (E \geq E_{c}) $$

$$ g_{v}(E) = \dfrac{8 \pi \sqrt{2}}{h^{3}} (m_{p}^{*})^{\frac{3}{2}} \sqrt{E_{v}-E} \qquad (E \leq E_{v}) $$

We can now attain the carrier concentrations by integrating with respect to energy.

$$ \therefore n = \int_{E_{c}}^{\infty} g_{c}(E) f(E) dE $$
$$ \therefore p = \int_{-\infty}^{E_{v}} g_{v}(E) (1-f(E)) dE $$

The above functions have no analytical solutions however by restricting ourselves to non-degenerate semiconductors, we can **approximate the Fermi function with the Boltzmann distribution function** (a simple exponential) which can be analytically solved to find the carrier concentrations:

$$ \large n = \int_{E_{c}}^{\infty} g_{c}(E) e^{-\frac{E-E_{F}}{kT}} dE = N_{c} \ e^{-\frac{E_{c}-E_{F}}{kT}} $$

$$ \large p = \int_{-\infty}^{E_{v}} g_{v}(E) e^{-\frac{E_{F}-E}{kT}} dE = N_{v} \ e^{-\frac{E_{F}-E_{v}}{kT}} $$

where $ N_{c} $ is the effective density of states in the conduction band and $ N_{v} $ is the effective density of states in the valence band:

$$ N_{c} = 2 \Big( \dfrac{ 2 \pi \ m_{n}^{*} \ k T }{h^{2}} \Big) ^ \dfrac{3}{2} = \dfrac{1}{\sqrt{2}} \Big( \dfrac{ \ m_{n}^{*} \ k T }{\pi \hbar^{2}} \Big) ^ \dfrac{3}{2} $$
$$ N_{v} = 2 \Big( \dfrac{ 2 \pi \ m_{p}^{*} \ k T }{h^{2}} \Big) ^ \dfrac{3}{2} = \dfrac{1}{\sqrt{2}} \Big( \dfrac{ \ m_{p}^{*} \ k T }{\pi \hbar^{2}} \Big) ^ \dfrac{3}{2} $$



## Carrier Equations

As derived above, we now have equations for the carrier concentrations that are dependent on the fermi level:

### $$ \color{blue}{ \large n = N_{c} \ e^{-\frac{E_{c}-E_{F}}{kT}} } $$
### $$ \color{blue}{ \large p = N_{v} \ e^{-\frac{E_{F}-E_{v}}{kT}} } $$

Using mass action law:
$$ n_{i}^{2} = N_{c} N_{v} \ e^{-\frac{E_{g}}{kT}} \qquad \small (E_{g} = E_{c} - E_{v}) $$

$$ \large n_{i} = \sqrt{N_{c} N_{v}} \ e^{-\frac{E_{g}}{2kT}} $$


</br>

### Fermi Level

### $$ E_{F} = \dfrac{E_{c} + E_{v}}{2} + \dfrac{1}{2} kT \ln \dfrac{N_{v}}{N_{c}} = \dfrac{E_{c} + E_{v}}{2} + \dfrac{3}{4} kT \ln \dfrac{m_{p}^{*}}{m_{n}^{*}} $$

For an **intrinsic** semiconductor:
### $$ E_{F} \approx \dfrac{E_{c} + E_{v}}{2} = E_{c} - \dfrac{E_{g}}{2} = E_{v} + \dfrac{E_{g}}{2} $$

</br><hr>

### Absolute Zero Simplication
At **absolute zero T = 0 K**, using the **ideal Fermi function** (0 or 1):
### $$ n =  \int_{0}^{\infty} g(E) f(E) dE = \int_{0}^{E_{F}} g(E) dE = \dfrac{(2mE_{F})^\dfrac{2}{3}}{3 \pi^2 \hbar^{3}}$$

$ n $ is the electron carrier concentration, $ c $ is the group number of the element, $ \rho $ is the density, $ m_{a} $ is the atomic mass and $ N_{A} $ is Avo's constant.

### $$ n = c \dfrac{\rho N_{A}}{m_{a}}  $$

#### Fermi Energy
Rearranging the **carrier equation**, we get the **Fermi Energy (Fermi Level at absolute zero)** : 
### $$ E_{F} = \dfrac{\hbar^{2}}{2m} (3 \pi^{2} n)^\dfrac{2}{3} $$


