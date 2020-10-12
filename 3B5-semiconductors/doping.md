# Semiconductor Doping

## Introduction

**Metals** - Overlap of valence and conduction bands

**Semiconductors** - Valence and conduction band gap $ 0.5 < E_{g} < 2eV  \small \text{(non-strict values)} $

**Insulators** - Valence and conduction band gap $ E_{g} > 2eV  \small \text{(non-strict values)} $

</br>

Minimum Energy of Conduction Band $ \qquad \qquad - \qquad E_{c} $ </br>
Maximum Energy of Valence Band $ \qquad \qquad \quad - \qquad E_{v} $ </br>
Valence to Conduction Energy Band Gap $ \qquad - \qquad E_{g} = E_{c} - E_{v} $ </br>

</br>

$
n = \small\text{ Electron Concentration in Conduction Band } \qquad E > E_{c} \\
p = \small\text{ Hole Concentration in Valence Band } \qquad E < E_{v} \\
n_{i} = \small\text{ Intrinsic Carrier Concentration } \\
$

(Insert Diagram Here)

</br>

**Semiconductor Conductivity** - Dependent on **Electron/Hole Concentration** and **Drift Velocity**

**Thermal Equilibrium** - Rate of Electron-Hole Pair Formation = Rate of Electron-Hole Pair Recombination

</br>
 
## Lattice Properties

### Intrinsic Carriers
For **intrinsic** (undoped) semiconductors at **thermal equilibrium**, the following is true where $ n_{i} $ is a **temperature-dependent material property**:
$$ \large n = p = n_{i} $$

This essentially means that the "default" number of charge carriers at thermal equilibrium is the number of electrons in the conduction band which is equivalent to the number of holes in the valence band (since the electrons have moved from the valence band to the conduction band). 

### Mass Action Law

$$ \large \text{Law of Mass Action} \qquad np=n_{i}^{2} $$

The product of the number of electrons in the conduction band and the number of holes in the valence band is constant at a fixed temperature and is independent of the amount of donor and acceptor impurity added.
##### Note*: Applies to both intrinsic and extrinsic semiconductors.

</br>

### Semiconductor Doping
Consider silicon lattice:
(Insert Image Here)

We can now consider the overall **charge neutrality condition** to calculate the hole and electron concentrations in an extrinsic (doped) semiconductor.

For a non-degenerately doped p-and-n-type semiconductor:
$$ \large p + N_{D}^{+} = n + N_{A}^{-} $$ 

We can split this into useful dopant equations for one of p-type or n-type doping.

</br>


#### N-Type Dopant (Electron Donor)
- Group 5 Element - Atom contributes an electron to the lattice

$ N_{D}^{+} = \small\text{Number of Ionised Donors} \ (cm^{-3})$
### $$ n = p + N_{D}^{+} $$

##### If $ N_{D}^{+} >> n_{i} $, then $ n \approx N_{D}^{+} $

</br>

#### P-Type Dopant (Electron Acceptor / Hole Donor)
- Group 3 Element - Atom contributes a hole to the lattice

$ N_{A}^{-} = \small\text{Number of Ionised Acceptors} \ (cm^{-3})$
### $$ p = n + N_{A}^{-} $$

##### If $ N_{A}^{-} >> n_{i} $, then $ p \approx N_{A}^{-} $

</br>

##### Note*: We can combine the suitable $ \textbf{doping equation} $ with the $ \textbf{mass action law} $ to solve the quadratic for $ n $ or $ p $ given $ N $ and $ n_{i} $

</br>

### Drift Velocity

Here we assume a proportionality relationship for drift velocity. 

### $$
\underbrace{v_{d}}_{\text{Drift Velocity}} = \underbrace{\mu}_{  \small\text{Const. of Proportionality} \\ \qquad \text{"Mobility"} } \quad \underbrace{\xi}_{\textbf{Low} \ \text{Electric Field}}
$$

##### Note*: The mechanism of transport we are considering is "drift transport" which is different to other mechanisms of transport such as diffusion.
##### Note*: Electric field must be low because at high electric fields, velocity saturation occurs due to optical phonon scattering or the Gunn effect (inter-valley electron transfer).

</br>

Now we need another equation that connects drift velocity to the electric field so that we can find some value for mobility. F=ma is not directly applicable as electrons collide with atoms in the lattice. However we can consider the electron to have effective mass $ m^{*} $, the mean collision time to be $ t_{col} $ with velocity $ v $ moving in an electric field with electric field strength $ \xi $:

$$ \large \dfrac{m_{n}^{*} \ v_{d}}{t_{col}} = q \ \xi $$ 

We can now rearrange for the mobility:
$$ \therefore \mu_{n} = \dfrac{q \ t_{col}}{m_{n}^{*}} $$

##### Note*: This is also applicable to holes and we can derive the same equations for holes. You must consider holes to be the movement of positive charge in the opposite direction to the direction of the electrons.

##### Note*: We avoid the use of E for electric field (electric field strength) as E also represents energy

</br>

### Current Flow

Upon the application of a potential difference to a material, the gradient of the energy bands increases (imagine the slanting of the energy band downwards towards the +ve terminal).

The electrons in both the conduction and the valence band are attracted towards the positive terminal.

The electrons in the conduction band can freely move hence causing current flow.
However the electrons in the valence band are confined to fill the available holes in the valence band and hence fill vacant holes moving towards the positive terminal. Relatively, this also looks like the holes are moving towards the negative terminal and therefore holes are positive charge carriers.

$$ J_{\small\text{Drift}} = q \cdot (v_{d} \cdot n_{T}) $$

$$ \large J_{\small\text{Drift}} = q \cdot (n \mu_{n} + p \mu_{p}) \xi = q \cdot (n \mu_{n} + p \mu_{p}) \dfrac{dV}{dx} $$

$$ I_{\small\text{Drift}} = J_{\small\text{Drift}} A $$
By integration and knowing that no terms are dependent on the applied potential difference $ V $ :
$$ \int_{0}^{L} I_{\small\text{Drift}} \ dx = \int_{0}^{V} q \cdot (n \mu_{n} + p \mu_{p}) \ dV \ \cdot \ A $$

$$ I_{\small\text{Drift}} L = A \cdot q \cdot (n \mu_{n} + p \mu_{p}) \cdot V $$

Rearranging the equation into **Ohm's law**:

$$ \large \dfrac{V}{I_{\small\text{Drift}}} = \dfrac{1}{ q \cdot (n \mu_{n} + p \mu_{p}) } \dfrac{L}{A} $$

We can actually see that this also links to the **resistivity** law $ R = \rho \dfrac{L}{A}$ where:
$$ \rho = \dfrac{1}{ q \cdot (n \mu_{n} + p \mu_{p}) } $$

Therefore the equation for **conductivity** is as follows:
$$ \sigma = q \cdot (n \mu_{n} + p \mu_{p}) $$

</br>

### Electric Potential

#### 1D Poisson's Equation
$$ - \dfrac{d^{2}V}{dx^{2}} = \dfrac{d\xi}{dx} = \dfrac{\rho}{\epsilon} $$

Substitute charge concentration $ \rho $ with the respective amount of charge concentration in the semiconductor. 
$$ \large - \dfrac{d^{2}V}{dx^{2}} = \dfrac{d\xi}{dx} = \dfrac{q( (p + N_{D}^{+}) - (n + N_{A}^{-}) )}{\epsilon} $$

Solve for the potential by integration and applying boundary conditions.

</br><hr></br>

## Fermi Function

The Fermi function $ f(E) $ is a probability function (not probability density) which outputs the probability of an electron occupying an energy state $ E $ under thermal equilibrium. $ k $ is the Boltzmann constant and $ T $ is the temperature. This will be useful for finding the probability of an electron being in the valence or the conduction band.

$$ \large f(E) = \dfrac{1}{1+e^{\frac{E-E_{f}}{kT}}} $$

The function is dependent on the Fermi energy level $ E_{f} $ which is in turn dependent on the effective density of energy states $ N_{c} $ (in the conduction band) and $ N_{v} $ (in the valence band).

#### Properties
$$ 0 \leq f(E) \leq 1 $$
$$ f(E_{f}) = \frac{1}{2} $$
$$ \small \text{Probability of empty energy state} \qquad \large 1 - f(E)$$


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


## Hall Effect


