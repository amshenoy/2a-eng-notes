# PN Junction

"Abrupt junction" model

* Abrupt junction
* Negligible recombination
* No fields outside junction


## Charge Neutrality 

$ e N_{A} x_{n} + e N_{D} x_{p} = 0 $

$$ N_{A} x_{n} + N_{D} x_{p} = 0 $$


## Contact Potential

Equations for the contact potential in terms of Fermi levels and doping:

$$ eV_{0} = E_{Fn} - E_{Fp} = kT \ln(\dfrac{N_{A}N_{D}}{n_{i}^{2}}) $$

</br>

## Depletion Region

### Contact Potential
Equation of contact potential in terms of depletion region widths.

$$ \dfrac{d^{2}V}{dx^{2}} = \dfrac{-\rho}{\epsilon} \qquad (\text{from Poisson's Equation})$$

(eg. $ \rho = - e N_{A} = e N_{D} $)

$$ E(x) = \dfrac{dV}{dx} = \int \dfrac{d^{2}V}{dx^{2}} dx $$

Find $ V_{n} $ using conditions for n-type side.
Find $ V_{p} $ using conditions for p-type side.

$ V_{0} = V_{n} - V_{p} $

$$ V_{0} = \dfrac{e}{2 \epsilon} (N_{A} x_{p}^{2} + N_{D} x_{n}^{2}) $$

#### Boundary Conditions

For p-type side: $ E(-x_{p}) = 0 $

For n-type side: $ E(x_{n}) = 0 $

Common: $ V(0) = 0 $


</br>

### Depletion Region Width

$$ w = x_{n} - x_{p} $$

**Rearrange contact potential** to make $ x_{n} $ and $ x_{p} $ the subjects.

Also use **charge neutrality substitution** to get two seperate equations for $ x_{n} $ and $ x_{p} $.

$ w = f(N_{A}, N_{D}) $

**Note: For a one-sided junction (denoted for example by $p_{+}n$), the width of one of the depletion regions with the highest concentration is very small in comparison to the other. (ie.$ N_{A} >> N_{D} $ or $ N_{D} >> N_{A}$ )**

$ w = \dfrac{2 \epsilon V_{0}}{e N_{D}}^{\dfrac{1}{2}} $ for ($ N_{A} >> N_{D} $)


</br>

## Junction Capacitance

Parallel-Plate Analogy

Capacitance (per unit area) $ C_{A} = \dfrac{C}{A} = \dfrac{\epsilon}{w} $


</br>

## Bias Application

Applying a bias voltage changes the Fermi levels in the semiconductor.



For the diagram below, applying a **positive bias voltage** to the **positive side**:




