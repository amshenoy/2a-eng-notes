# JFET, MESFET & HEMT

FETs are **unipolar** devices ie. current flow dominated by drift current (ie. a single carrier type).

</br><hr>

# JFET

$ P^{+} N P^{+} $
 
**Use of PN Junction**


</br>

## Pinch-Off Voltage

**Depetion Region Width** of $ P^{+} N $ junction:

$ \Large w_{PN} = (\dfrac{2\epsilon(V_{0} - V)}{e N_{D}})^\dfrac{1}{2} $

where $ V $ is the applied bias.

At **pinch-off**, the applied voltage $ \color{blue}{ V = V_{p} = V_{GS} - V_{DS} } $ and $ \color{blue}{ w(x=L) = w_{PN} = \dfrac{h}{2} = (\dfrac{2\epsilon(V_{0} - V_{p})}{e N_{D}})^\dfrac{1}{2} } $  

</br>

$$  \large w(x) = w \dfrac{x}{L} = \dfrac{h}{2} \dfrac{x}{L} = (\dfrac{2\epsilon(V_{0} - V_{p})}{e N_{D}})^\dfrac{1}{2} \ \dfrac{x}{L} $$  

(Symmetry about midpoint of N layer)

 </br>

To find $ V_{p}(h)$, assume $\color{red}{ V_{0} << V_{p} }$ and rearrange $ w $ for $ V_{p} $:

$$ \Large \color{red}{ V_{p} \approx h^{2} \dfrac{e N_{D}}{\epsilon} } $$

</br>

## Current-Voltage Characteristics

$ R = \dfrac{\rho L}{A}$

Per unit depth, this can be written as:
$$ \Large \color{blue}{ \delta r_{d} = \dfrac{\rho dx}{d(h-2w)} } $$


$$ \Large \color{blue}{ I_{DS} = \dfrac{\delta V_{DS}}{\delta r_{d}} }$$

$ \Large w \approx \Big(\dfrac{2\epsilon(V_{DS} - V_{GS})}{e N_{D}} \Big)^\dfrac{1}{2} = \Big(\dfrac{h^{2}(V_{GS} - V_{DS})}{4 V_{p}} \Big)^\dfrac{1}{2} $

$$ \color{blue}{ d(h - 2w) = dh \ (1 - 2 \dfrac{dw}{dh}) } $$


$$ \Large
\begin{align*}
\int_{x=0}^{L} I_{DS} \ dx &= \int \dfrac{d(h-2w)}{\rho} dV_{DS} \\
&= \dfrac{dh}{\rho} \int_{V_{DS} = 0}^{V_{DS}} (1 - 2\dfrac{dw}{dh} ) \ dV_{DS} \\
&= \dfrac{dh}{\rho} \int_{V_{DS} = 0}^{V_{DS}} (1 - \big(\dfrac{V_{GS} - V_{DS}}{V_{p}}\big)^\frac{1}{2} ) \ dV_{DS}
\end{align*}
$$

where $ \rho = \dfrac{1}{eN_{D}\mu_{e}}$.

**Perform integral by substitution $ u = \big(\dfrac{V_{GS} - V_{DS}}{V_{p}}\big) $**

$$ I_{DS} = \dfrac{dh}{\rho L} \int_{V_{DS} = 0}^{V_{DS}} (1 - \big(\dfrac{V_{GS} - V_{DS}}{V_{p}}\big)^\frac{1}{2} ) \ dV_{DS} $$

This solution is only valid for $ V_{p} < V_{GS} - V_{DS} $, ie. $ V_{DS} < V_{GS} - V_{p} $ (for saturation graph).

To find the saturation current $I_{DS, sat}$, substitute a value for $ V_{DS} \ge V_{G} - V_{p} $ into $ I_{DS} $:

$ \color{blue}{ I_{DS, sat} = I_{DS}\Bigg(V_{GS} - V_{p}\Bigg) } $


Small signal mutual transconductance in the saturated region $ g_{m} $:

$ \color{blue}{ g_{m} = \dfrac{\partial I_{DS}(sat) }{V_{GS}} } $

</br><hr>


# MESFET 

**Use of MS Junction** (More specifically a **reverse-biased Schottky barrier**)

(+) Easier to manufacture </br>
(+) In contrast to a JFET, a MESFET can also be realised
for materials that can be only p-doped or n-doped. </br>
(+) Useful in high-speed digital and microwave circuits. </br>



## HEMT

High Electron Mobility Transistor (HEMT) is a variant on the MESFET

To increase conductivity of a MESFET, we could increase the doping level, but the increased number of impurity atoms causes more electron scattering and reduces mobility.

Instead we do the following:

- A **wide bandgap doped** SC provides a **source of electrons** to the **thin, low doped** SC. This accumulation is
referred to as **two-dimensional electron gas** (2-DEG).

- We therefore have a large carrier density in a
region of low doping density

- These carriers therefore have a high mobility (enabling
fast switching and access times)


