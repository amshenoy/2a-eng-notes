# Electron Models

</br> <hr>

### Free Electron Model (Metals)

Constant potential throughout lattice

$$ E = \dfrac{\hbar^{2}}{2m} k^{2} $$

</br><hr>

# Nearly Free Electron Model (Semiconductors)

**Forbidden energy (energy gaps)** in E-k curve

**Periodicity** in E-k curve

</br>

## Schrodinger Solutions

Travelling Wave   $ \psi = Ae^{j(k x - \omega t)} = Ae^{j(k x)} \quad (TISE) $ &emsp; (If not Bragg reflected)

Standing Wave   $ \psi = A \cos(kx) e^{j( - \omega t)} = A \cos(kx) \quad (TISE)$ &emsp; (If Bragg reflected)


## Bragg Reflection

#### Bragg Reflection occurs when $ k = \pm \dfrac{n\pi}{a} $

(Derived from Bragg's Law $ a = \dfrac{n \lambda}{2} $ and $ \lambda = \dfrac{2 \pi}{k} $)


</br>

## Brioullin Zones

#### $ \text{ Band gaps in E-k graph due to periodic potential of atoms } $


### N-th Brioullin Zone: $ \dfrac{(n-1) \pi}{a} < |k| < \dfrac{n \pi}{a} $


</br>

## Bloch's Theorem

__“The wavefunction of an electron in a periodic potential is a plane wave times a function with the periodicity of the lattice.”__


## $$ \psi = Ae^{j \Big((k \pm \frac{2n\pi}{a}) x \Big)} \cdot \underbrace{u(x)}_{\text{Function with the same } \\ \text{ periodicity as the lattice}} $$

$ \text{Potential of lattice (Periodic boundary condition) } \quad V(x) = V(x - n a) $


</br>

## Direct/Indirect Band Gaps

**Direct** Band Gaps (**1D Transition**) - Band gaps that only differ in **energy** $ E $

**Indirect** Band Gaps (**2D Transition**) - Band gaps that differ in **energy** $ E $ and **wavenumber** $ k $ </br>
(ie. requires addition of energy $ E $ and momentum $ p = \hbar k $ to move an electron from VB to CB )


</br>

## Electron Effective Mass ($m*$)

### Consider as a **wave**:

#### $ \text{Group Velocity} \quad v = \dfrac{\partial \omega}{ \partial k} $

#### $ \text{Energy} \quad E = h f = \hbar \omega $

## $ \color{blue}{ v = \dfrac{1}{\hbar} \dfrac{\partial E}{\partial k} } $ &emsp; (1)


### Consider as a **particle**:

#### $ F = \dfrac{d(\hbar k)}{dt} = \hbar \dfrac{dk}{dt} $ &emsp; (2) 

#### $ F = m^{*} \dfrac{dv}{dt}$ &emsp; (3)


**Sub (1) into (3) and then (2) into the same simplified equation.**
## $$ \therefore \color{blue}{ \dfrac{\hbar^{2}}{m^{*}} =  \dfrac{d^{2}E}{dk^{2}} } $$
