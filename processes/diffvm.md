---
title: DiffVM's diffractive production of vector meson
tags: diffvm
category: processes
---

# DiffVM

The $ep$-induced $\gamma^{(\ast)}\Pom\rightarrow VM$ process may be steered with the `diffvm` label.

## Process-specific options

- `vmFlavour` controls the PDG id of the VM produced
- `vmMode` and `protonMode` steer the VM production mode and proton side emission types respectively
    - `BeamMode.GluonFragmentation` or `-1`
    - `BeamMode.Elastic` or `0`
    - `BeamMode.StandardFragmentation` or `1`
    - `BeamMode.NucleonPionsDecay` or `2`
- `photonMode` controls the photon emission type
    - `PhotonMode.Fixed` or `-1`
    - `PhotonMode.InvK` or `0`
    - `PhotonMode.WWA`, `PhotonMode.ABTSmith`, `PhotonMode.AandS` = `1-3`

Furthermore, the following parameters can be steered in this process:

### `slopeParameters`

- `wb0` is the $w _ {\gamma p}$ centre-of-mass energy (in GeV) at which `b0` $=b_0$ was measured
- `amxb0` is the mass $M_X$ of the diffractively dissociating hadronic system $X$ for which $b_0$ was measured
- `anexp` is a power-law exponent

### `pomeronParameters`

- `epsilonW` and `epsilonM` controlling the intercept of the pomeron trajectory (minus 1).
  The first one steers the rise of $\sigma _ {\gamma p}$ with $W$, while the second controls the $M_X$ spectrum
- `alpha1` and `alpha1m` control the pomerons trajectory's $\alpha'$ (therefore, expressed in GeV¯²)

### `vmParameters`

- `lambda` and `eprop` control the $Q^2$-dependence of the total production cross section, through

$$\sigma(Q^2) = \sigma_0\left(1 + Q^2/\Lambda^2\right)^{-E _ {\rm prop}}$$

- `xi` and `chi` control the behaviour of the longitudinal-to-transverse cross section ratio through

$$\frac{\sigma_L(Q^2)}{\sigma_T(Q^2)}=\frac{\xi Q^2/m^2}{1+\xi\chi Q^2/m^2}.$$

Therefore, in this scheme,

$$\sigma_L/\sigma_T\to \left\{\begin{array}{ll}
\xi Q^2/m^2 & \text{for low-}Q^2,\\
1/\chi      & \text{for high-}Q^2.
\end{array}\right.$$

