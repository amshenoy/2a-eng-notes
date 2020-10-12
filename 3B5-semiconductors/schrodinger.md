# Schrodinger

## Wave Function
Consider the wave function of a particle to be $ \psi $ containing information of all the measurable properties of the particle.

For simplification of analysis, it is best to consider the 1D case: </br>
1D - $ \psi(x, t) $ &emsp;
2D - $ \psi(x, y, t) $ &emsp;
3D - $ \psi(x, y, z, t) $ &emsp;

Probability Density (of finding particle between $ x  $ and $ x + \delta x$) = $ \psi \psi^{*} $ 

$ \therefore $ If $ \psi(x, t) $ is real, $$ P(a < p_{x} < b) = \int_{x=a}^{x=b} |\psi^{2}| dx $$

### Wave Types
Travelling Wave &emsp; $ \psi = Ae^{j(k x - \omega t)}$

Standing Wave &emsp; $ \psi = A \cos(kx) e^{j( - \omega t)}$

Wave Packet &emsp; $ \psi = \sum_{i} A_{i}e^{j(k_{i} x - \omega_{i} t)}$

</br>

### Wave Operators
We can operate on the wave-function $ \psi(x, t) $ to determine the attributes of the wave-particle.

#### Momentum
$$ \hat{p_{x}} = \dfrac{\hbar}{i} \dfrac{\partial}{\partial x} $$
In the 2D $ \psi(x, y, t) $ or 3D $ \psi(x, y, z, t) $ case, the operator is a vector operator (using the grad operator $ \nabla $ ):
$$ \underline{\hat{p}} = \begin{bmatrix} \hat{p_{x}} \\
           \hat{p_{y}} \\
           \hat{p_{z}}
         \end{bmatrix}
= \dfrac{\hbar}{i} \nabla $$

#### Energy
$$ \hat{E} = - \dfrac{\hbar}{i} \dfrac{\partial}{\partial t} $$

In each case, applying the operator $ \hat{\Theta} $ returns the attribute $ \Theta $ itself multiplied by the wave-function $ \psi $:
$$ \hat{\Theta} ( \psi ) = \Theta \psi $$

#### Example:
Let $ \psi $ be a plane wave $ \psi = Ae^{i(k x - \omega t)}$:
$$ \therefore \hat{p_{x}} ( \psi ) = \dfrac{\hbar}{i} \dfrac{\partial \psi}{\partial x} = ik \dfrac{\hbar}{i} Ae^{i(k x - \omega t)} = k \hbar \ \psi \qquad \therefore p_{x} = k \hbar $$
$$ \therefore \hat{E} ( \psi ) = - \dfrac{\hbar}{i} \dfrac{\partial \psi}{\partial t} = -i\omega \dfrac{\hbar}{i} Ae^{i(k x - \omega t)} = \omega \hbar \ \psi \qquad \therefore E = \omega \hbar $$

</br><hr></br>

## Schrodinger's Equation

### Introduction
Schrodinger's equation is essentially the application of the Hamiltonian $ \hat{H} $ (ie. Total Energy $ \hat{E} $) operator on a wave function.

As we saw previously, the **time-dependent** energy operator is as follows:
$$ \hat{E} = - \dfrac{\hbar}{i} \dfrac{\partial}{\partial t} $$

However we can also calculate the energy operator as follows:
$$ \text{Total Energy} = \text{Kinetic Energy} + \text{Potential Energy} $$

$$ \text{Kinetic Energy Operator} \qquad \hat{T} = \Bigg(\dfrac{|\underline{\hat{p}}|^{2}}{2m} = -\dfrac{\hbar^{2}}{2m} \nabla^{2} \Bigg)= \dfrac{\hat{p_{x}}^{2}}{2m} = - \dfrac{\hbar^{2}}{2m} \dfrac{\partial^{2}}{\partial x^{2}} $$

$$ \text{Potential Energy Operator} \qquad \hat{V} \qquad \small \text{(Dependent on Potential terrain)} $$

$$ \text{Energy Operator (Hamiltonian)} \qquad \hat{H} = \hat{T} + \hat{V} = \dfrac{\hat{p_{x}}^{2}}{2m} + \hat{V} $$

Therefore we can now equate the **time-dependent** energy operator with the hamiltonian operator giving the following:
$$ \Big(\hat{H} =\Big) \qquad \hat{T} + \hat{V} = \hat{E}$$ 

This is the full "Schrodinger operator":
$$ \dfrac{\hat{p_{x}}^{2}}{2m} + \hat{V} = - \dfrac{\hbar}{i} \dfrac{\partial}{\partial t} $$
$$ - \dfrac{\hbar^{2}}{2m} \dfrac{\partial^{2}}{\partial x^{2}} + \hat{V} = - \dfrac{\hbar}{i} \dfrac{\partial}{\partial t} $$

### Full Equation
Applying this to our wave function $ \psi $ gives us the famous Schrodinger equation:
$$ - \dfrac{\hbar^{2}}{2m} \dfrac{\partial^{2} (\psi)}{\partial x^{2}} + \hat{V}(\psi) = - \dfrac{\hbar}{i} \dfrac{\partial(\psi)}{\partial t} $$
$$ - \dfrac{\hbar^{2}}{2m} \dfrac{\partial^{2} \psi}{\partial x^{2}} + V \psi = - \dfrac{\hbar}{i} \dfrac{\partial \psi}{\partial t} $$

However we will be looking at the **time-independent** Schrodinger equation (ie. $\hat{E} (\psi) = \text{Constant} = E \psi $):
$$ - \dfrac{\hbar^{2}}{2m} \dfrac{\partial^{2} \psi}{\partial x^{2}} + V \psi = E \psi $$

### $$ \color{blue}{ - \dfrac{\hbar^{2}}{2m} \dfrac{\partial^{2} \psi}{\partial x^{2}} = (E - V ) \psi } $$

### Solutions

We can rearrange the Schrodinger's equation to simplify the linear PDE.  
$$ \dfrac{\partial^{2} \psi}{\partial x^{2}} = - \dfrac{2m}{\hbar^{2}}  (E-V) \psi \qquad \Big(= - \alpha^{2} \psi \Big) $$

#### (Revision: General Solution to $ \dfrac{\partial^{2} \psi}{\partial x^{2}} = - \alpha^{2} \psi \Longrightarrow \psi = Ae^{i \alpha x} + Be^{-i \alpha x} $ )
### $$ \color{red}{ \psi = Ae^{i \alpha x} + Be^{-i \alpha x} \text{ where } \alpha = \sqrt{ \dfrac{2m}{\hbar^{2}}  (E-V) } } $$

To find the coefficients of the general solution, we need to consider the following while considering boundary conditions:
* $ \psi $ is continuous
* $ \dfrac{\partial \psi}{\partial x} $ is continuous
* $ \int_{-\infty}^{\infty} |\psi|^{2} dx = 1 $

</br>

#### Problem Scenarios
We are usually given a potential function (consider a piecewise constant function) and we have to compute the wave function in the given regions.

__Note*: Particles cannot exist in regions with infinite potential!__

</br>

**Example (Finite Potential Well):**

$$ V = \begin{array}{cc}
  \Bigg\{ & 
    \begin{array}{cc}
      V_{0} & x \leq 0 \\
      0 & 0 \leq x \leq L \\
      V_{0} & x \geq L
    \end{array}
\end{array} $$

$ \text{For} \quad 0 \leq x \leq L : $
</br>
If $ E > 0 \qquad \therefore \alpha = +ve \qquad \therefore \psi_{2} = A \text{sin}(\alpha x) + B \text{cos}(\alpha x) $ 

</br>

$ \text{For} \quad x \leq 0 \text{ and } x \geq L: $
</br></br>
$
\text{ Case 1: } \text{ If } E > V_{0} \qquad \therefore \beta = +ve \\

\therefore \psi_{1} = C \text{sin}(\beta x) + D \text{cos}(\beta x) \qquad \psi_{3} = E \text{sin}(\beta x) + F \text{cos}(\beta x) 
$
</br></br>
$
\text{ Case 2: } \text{ If } E < V_{0} \qquad \therefore \beta = -ve \\

\therefore \psi_{1} = C e^{\beta x } + D e^{- \beta x } \qquad \psi_{3} = E e^{\beta x } + F e^{- \beta x }
$ 

Any exploding (tending to $ \infty $) terms can be neglected as the wave function must adhere to our "sensible" wave-function requirements as show in the solutions section.

For $ E > V_{0} $, there are no exploding terms and we have already **found our solutions**.

However for $ E < V_{0} $, there are **exploding terms** that need to be **removed**. 

##### Note*: The result for $ E < V_{0} $ is significant as this only works for wave-duality and not for classical mechanics. This process is known as tunneling.

For $ x \leq 0 $, as $ \beta < 0 $: 
$$ \psi_{1} = D e^{- \beta x } $$

For $ x \geq L $, as $ \beta < 0 $: 
$$ \psi_{3} = E e^{ \beta x } $$

For $ 0 \leq x \leq L $, we have no exploding terms and the solution is the same as before:
$$ \psi_{2} = A \text{sin}(\alpha x) + B \text{cos}(\alpha x) $$ 

</br>

## Heisenberg's Uncertainty Principle

Measuring the wave function of a particle physically has this limitation. If $ \Delta p $ is the error in determining momentum and $ \Delta x $ is the error in determining position, the following holds true:
$$ \Delta p \Delta x \geqslant \dfrac{\hbar}{2} $$
This can also be written using $ \Delta E $ as the error in energy and $ \Delta t $ as the error in time:
$$ \Delta E \Delta t \geqslant \dfrac{\hbar}{2} $$

$ \therefore p_{min} = \dfrac{\hbar}{2 \Delta x} $

Energy of electron at energy state $ n $:
### $$ E_{n} = (2n \pi)^{2} E_{min} = (2n \pi)^{2} \dfrac{p_{min}^2}{2m} = \dfrac{(n\pi)^2 \ \hbar^2 }{2m \ \Delta x ^{2}} $$

