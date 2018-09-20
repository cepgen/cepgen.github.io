---
title: kT factorisation
---

# The $\kt$ factorisation approach

As described in [the reference papers](../bibliography#kt-factorisation), the $\kt$-factorisation approach allows a direct factorisation of any hard process (e.g. photon- or gluon-induced productions) while accounting for transverse components of parton virtualities.

For instance, a $pp\to p^{(\ast)}(\ggx)p^{(\ast)}$ matrix element can be factorised through the following formalism:

$$\mathrm d\sigma = \int \frac{\mathrm d^2{\mathbf q_{\mathrm T}^2}_1}{\pi {\mathbf q_{\mathrm T}^2}_1}
                    {\cal F}_{\gamma/p}^{\rm el/inel}(x_1,{\mathbf q_{\mathrm T}^2}_1)
                    \int \frac{\mathrm d^2{\mathbf q_{\mathrm T}^2}_2}{\pi {\mathbf q_{\mathrm T}^2}_2}
                    {\cal F}_{\gamma/p}^{\rm el/inel}(x_2,{\mathbf q_{\mathrm T}^2}_2) ~ \mathrm d\sigma^\ast,$$

where $\mathcal F_{\gamma/p}^{\rm el/inel}(x_i,\vecqt_i)$ are unintegrated parton densities, and $\mathrm d\sigma^\ast$ the hard process factorised out of the total matrix element.

## Unintegrated photon fluxes

Elastic unintegrated photon densities are expressed as functions of the proton electric and magnetic form factors $G_E$ and $G_M$:

$$\mathcal F_{\gamma/p}^{\rm el}(\xi,\vecqt^2) = \frac{\alpha}{\pi}\left[(1-\xi)\left(\frac{\vecqt^2}{\vecqt^2+\xi^2 m_p^2}\right)^2 F_E(Q^2)+\frac{\xi^2}{4}\left(\frac{\vecqt^2}{\vecqt^2+\xi^2 m_p^2}\right) F_M(Q^2)\right].$$

The inelastic contribution further requires both the diffractive state four-momentum norm $M_X$ and a proton structure functions parameterisation as an input:

$$\mathcal F_{\gamma/p}^{\rm inel}(x,\vecqt^2) = \frac{\alpha}{\pi}\Bigg[(1-\xi)\left(\frac{\vecqt^2}{\vecqt^2+\xi(M_X^2-m_p^2)+\xi^2 m_p^2}\right)^2\frac{F_2(\xbj,Q^2)}{Q^2+M_X^2-m_p^2}+{}\\
  {}+\frac{\xi^2}{4}\frac{1}{\xbj^2} \left(\frac{\vecqt^2}{\vecqt^2+\xi(M_X^2-m_p^2)+\xi^2 m_p^2}\right) \frac{2\xbj F_1(\xbj,Q^2)}{Q^2+M_X^2-m_p^2}\Bigg],$$

with $\xbj = {Q^2}/({Q^2+M_X^2-m_p^2})$ the Bjorken scaling variable.

