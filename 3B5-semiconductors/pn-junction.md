# PN Junction

"Abrupt junction" model

* Abrupt junction
* Negligible recombination
* No fields outside junction

## Depletion Region

### Charge Neutrality 

$ e N_{A} x_{n} + e N_{D} x_{p} = 0 $

$$ N_{A} x_{n} + N_{D} x_{p} = 0 $$

### Potential

$$ \dfrac{d^{2}V}{dx^{2}} = \dfrac{-\rho}{\epsilon} \qquad (\text{from Poisson's Equation})$$

(eg. $ \rho = - e N_{A} = e N_{D} $)

$$ E(x) = \dfrac{dV}{dx} = \int \dfrac{d^{2}V}{dx^{2}} dx $$

Find $ V_{n} $ using conditions for n-type side.
Find $ V_{p} $ using conditions for p-type side.

$ V_{0} = V_{n} - V_{p} $


#### Boundary Conditions

$ E(-x_{p}) = 0 $

$ E(x_{n}) = 0 $

$ V(0) = 0 $

**Note: For a one-sided junction, the width of one of the depletion regions with the highest concentration is very small in comparison to the other. (ie.$ N_{A} >> N_{D} $ or $ N_{D} >> N_{A}$ )**


</br>

## Contact Potential
For a one-sided junction (denoted for example by **p_{+}n**), the above method gives the following result in terms $ N_{A} $ and $ N_{D} $ :

$$ eV_{0} = E_{Fn} - E_{Fp} = kT \ln(\dfrac{N_{A}N_{D}}{n_{i}^{2}}) $$


</br>

## Junction Capacitance




