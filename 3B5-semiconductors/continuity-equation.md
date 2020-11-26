# Continuity Equation

If we introduce local excess carriers, we are now considering inhomogeneous semiconductors.
Therefore we cannot use the mass-action law $ np = n_{i}^{2} $:
We also need to consider transport by **diffusion** as well as **generation and recombination**.

</br><hr>

## Diffusion

### Current Density
$ D $ is **diffusion coefficient** and $ e D_{e} \dfrac{\partial n(x)}{\partial x} $ is the expression for carrier diffusion.

$ e n \mu_{e} E $ is the expression due to **drift** caused by inhomogenous charge density from an **applied electric field** $ \mathcal{E} $. Note that $ \large v_{\text{drift}} = \mu_{e} \mathcal{E} $ 
 
$$ \Large J_{e} = e n \mu_{e} \mathcal{E} \color{blue}{\mathbf{\boldsymbol{+}}} e D_{e} \dfrac{\partial n}{\partial x} $$

$$ \Large J_{h} = e p \mu_{e} \mathcal{E} \color{red}{\mathbf{\boldsymbol{-}}}  e D_{e} \dfrac{\partial p}{\partial x} $$

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

### 1) Generation 
Photonic ($ E > E_{g} $) Electron-Hole Pair Creation (Optical Injection & Excitation)

### 2) Recombination
Transition (VB to CB) Recombination

__a)__ **Direct Recombination** - **Photon** absorption/emission

__b)__ **Indirect Recombination** - **Photon** (move in $ E $ energy dimension) and **Phonon** (move in $ k $ momentum dimension) absorption/emission

### 3) Recombination by Traps

Defects in the crystal lattice causing recombination

– Before entering the **recombination centre**, the electron may pass through several traps.

– The **average time that a carrier can exist in the free state** is called the **lifetime** $ \tau $.

– Whilst trapped, the carriers cannot contribute to conduction.

</br><hr>

## Master Equation

$ \Delta n $ denotes excess electrons and $ \Delta p $ denotes excess holes.

$ D_{e} \dfrac{\partial^{2} \Delta n}{\partial x^{2}} $ is the **diffusion** term.

$ ( \mu \mathcal{E} ) \dfrac{\partial \Delta n}{\partial x} $ is the **drift** term (sign dependent on carrier type).

$ \dfrac{\Delta n}{\tau_{e}} $ is the **generation/recombination** term.




$$ \large \dfrac{\partial \Delta n}{\partial t} = - \dfrac{\Delta n}{\tau_{e}} \color{blue}{\mathbf{\boldsymbol{+}}} \dfrac{1}{e} \dfrac{\partial}{\partial x} J_{e} $$

</br>

$$ \large \dfrac{\partial \Delta p}{\partial t} = - \dfrac{\Delta p}{\tau_{h}} \color{red}{\mathbf{\boldsymbol{-}}} \dfrac{1}{e} \dfrac{\partial}{\partial x} J_{h} $$


### Full Equation

$$ \large \dfrac{\partial \Delta n}{\partial t} = D_{e} \dfrac{\partial^{2} \Delta n}{\partial x^{2}} \color{blue}{\mathbf{\boldsymbol{+}}} \mu_{e} \mathcal{E}  \dfrac{\partial \Delta n}{\partial x} - \dfrac{\Delta n}{\tau_{e}} $$

$$ \large \dfrac{\partial \Delta p}{\partial t} = D_{h} \dfrac{\partial^{2} \Delta p}{\partial x^{2}} \color{red}{\mathbf{\boldsymbol{-}}} \mu_{h} \mathcal{E}  \dfrac{\partial \Delta p}{\partial x} - \dfrac{\Delta p}{\tau_{e}} $$


</br>

### Solving Method

**Simplify the equation**

$ \dfrac{\partial \Delta n}{\partial t} = 0 ? \qquad \mathcal{E} = 0 ? $ 

**Solve the differential**


</br><hr>


## Haynes-Shockley 

Used to obtain **minority carrier mobility**.

$ V_{0} $ - Applied Voltage

$ L_{0} $ - Length of Sample

$ L $ - Distance between Probes

$ \Delta t $ - Width of Applied Pulse (measured by oscilloscope)

$ \Delta w $ - Actual Width of Applied Pulse

$ t_{d} $ - Time of Arrival of Pulse

</br>

$ \Large v_{d} = \mu_{\text{minority}} \ \mathcal{E} = \dfrac{L}{t_{d}} $

$ \mathcal{E} = \dfrac{V_{0}}{L_{0}} $

$ \Large \Delta w = v_{d} \enspace \Delta t $

</br>

**Hall Effect** used to obtain **majority carrier mobility**.

  



