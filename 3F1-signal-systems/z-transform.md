# Z-Transform

Z-transform is the discrete version of the Laplace Transform.

$$ \large \mathcal{Z}\{x_{k}\} = \sum_{k=-\infty}^{\infty} x_{k}[k] z^{-k} $$

## Derivation

Consider a continuous time signal $ x(t) $ sampled at rate $ T $ to be $ x_{\delta}(t)$ :
$$ 
\begin{align*}
x_{\delta}(t) &= \sum_{n=-\infty}^{\infty} x(t) \delta(t-nT) \\
&= \sum_{n=-\infty}^{\infty} x(nT) \delta(t-nT) \\
\end{align*}
$$

Taking the Laplace transform of the sampled signal:
$$
\begin{align*}
X_{\delta}(s) & = \mathcal{L}\{x_{\delta}(t)\} \\
& = \int_{t=-\infty}^{\infty} x_{\delta}(t) e^{-st} dt \\
& = \int_{t=-\infty}^{\infty} \Big( \sum_{n=-\infty}^{\infty} x(kT) \delta(t-nT) \ \Big) \ e^{-st} dt \\
& = \sum_{n=-\infty}^{\infty} x(kT) \underbrace{\Big( \int_{t=-\infty}^{\infty} \delta(t-nT) \ e^{-st} dt \Big)}_{\large e^{-snT}} \\
& = \sum_{n=-\infty}^{\infty} x(nT) \ e^{-snT} \\
\end{align*}
$$

As $ T $ is a constant determined by the sampling rate and the integral is of the range $[-\infty,\infty]$, we can replace $ nT $ with the index $ k $:

$$ \therefore X_{\delta}(s) = \sum_{k=-\infty}^{\infty} x(k) \ e^{-sk} $$

We have now discretised the Laplace transform however the signal is still dependent on the signal function $ x(t) $. We can remove this dependency by considering the function $ x(k) $ to be an array $ x_{k} $ indexed by $ k $. 
$$ \therefore X_{\delta}(s) = \sum_{k=-\infty}^{\infty} x_{k}[k] \ e^{-sk} $$

We can rewrite the above as the Z-transform by substituting $ z = e^{s} $:
$$ \therefore X_{\delta}(z) = \sum_{k=-\infty}^{\infty} x_{k}[k] \ z^{-k} $$

Therefore instead of considering the transform applied to a function of time $ x_{d}(t) $, we can also consider it as a transform applied to the array $ x_{k} $ giving us the Z-transform:
$$ \large \mathcal{Z}\{x_{k}\} = \sum_{k=-\infty}^{\infty} x_{k}[k] z^{-k} $$
