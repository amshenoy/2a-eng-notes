# Semiconductor Doping

## Introduction

**Metals** - Overlap of valence and conduction bands

**Semiconductors** - Valence and conduction band gap $ 0.5 < E_{g} < 2eV  \small \text{(non-strict values)} $ - Silicon $ sp^{3} $ hybridisation creating bonding and antibonding electron states.

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

##### Solutions
We can combine the suitable $ \textbf{doping equation} $ with the $ \textbf{mass action law} $ to solve the quadratic for $ n $ or $ p $ given $ N $ and $ n_{i} $.
The following can be easily derived but nonetheless the solutions for $ n $ and $ p $ from the doping equations have been shown below:

$$ n = \dfrac{1}{2} \Big( - (N_{D}^{+} - N_{A}^{-}) + \sqrt{(N_{D}^{+} - N_{A}^{-})^{2} + 4n_{i}^{2}} \Big) $$

$$ p = \dfrac{1}{2} \Big( + (N_{D}^{+} - N_{A}^{-}) + \sqrt{(N_{D}^{+} - N_{A}^{-})^{2} + 4n_{i}^{2}} \Big) $$

</br>

##### Note*: $ n=p=n_{i} $ only for **intrinsic** semiconductors

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

</br>

## Hall Effect

(Insert Diagram)

### Left-Hand Rule
**Y** &emsp; **Z** </br>
|&emsp;/</br>
| /____ **X**</br>

### $ \text{Apply magnetic field } B_{z} \text{ , conventional current density } J_{x} $:
### $ F = q \underline{v} \times \underline{B} $

### $ |F_{y}| = q v_{x} B_{z} = q E_{y} $

### $ J_{x} = p q v_{x} $ ($p$ = hole concentration ) 
$ J_{x} = \dfrac{I}{A} $ where $ A $ is the cross-sectional area of the sample.

### $ V_{H} = E_{y} \Delta y $ (-ve for n-type material)

### Hall's Coefficient &emsp; $ R_{H} = \dfrac{E_{y}}{J_{x} B_{z}} 
 = \dfrac{1}{\underbrace{pq}_{\text{For p-type material}}} = \dfrac{-1}{\underbrace{nq}_{\text{For n-type material}}} $

__Note*: Problems that involve the Hall Effect would be to determine some property to continue solving the problem (ie. $ p $, $ \mu $, $ \sigma $, $B_{z}$). Use in conjunction with other equations (ie. Fermi $ E_{F} $, conductivity $ \sigma $, mobility $\mu$)__

 
