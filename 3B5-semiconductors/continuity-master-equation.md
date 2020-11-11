# Continuity Master Equation

If we introduce local excess carriers, we are now considering inhomogeneous semiconductors.
Therefore we cannot use the mass-action law $ np = n_{i}^{2} $:
We also need to consider transport by **diffusion** as well as **generation and recombination**.

</br><hr>

## Diffusion

### Current Density
$ D $ is **diffusion coefficient** and $ e D_{e} \dfrac{\partial n(x)}{\partial x} $ is the expression for carrier diffusion.

$ e n \mu_{e} E $ is the expression due to **drift** caused by inhomogenous charge density from an **applied electric field** $ \mathcal{E} $. Note that $ \large v_{\text{drift}} = \mu_{e} \mathcal{E} $ 
 
$$ \Large J_{e} = e n \mu_{e} \mathcal{E} + e D_{e} \dfrac{\partial n(x)}{\partial x} $$

$$ \Large J_{h} = e p \mu_{e} \mathcal{E} - e D_{e} \dfrac{\partial p(x)}{\partial x} $$

At **equilibrium**, no net current flows:
$ \large J_{e} = J_{h} = 0 $




</br>

### Einstein's Relation

$$ \large \dfrac{D_{e}}{\mu_{e}} = \dfrac{D_{h}}{\mu_{h}} = \dfrac{kT}{e} \quad (\text{Volts}) $$

#### Derivation:

1) Consider equilibrium ie. **diffusion current density** $ J_{n} = 0 $.

2) Find $ \dfrac{\partial n}{\partial x} $ from $ n(x) = N_{c} e^{\dfrac{E_{f}-E_{c}(x)}{kT} }$  and $ \dfrac{dE_{c}}{dx} = \mathcal{E} e $ (from $ E = F x = \mathcal{E} q \ x $ )




</br><hr>

## Generation & Recombination

$ np \ne n_{i}^{2} $
 
Consider the generation rate of carriers $ g_{i} $ due to excitation and recombination rate of carriers $ r_{i} $:

$$ \large \dfrac{dn}{dt} = g_{i} - r_{i} $$







