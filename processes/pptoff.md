---
title: kT-factorised two-photon production of fermion pairs
tags: lpair
category: processes
---

# $\kt$-factorised $\ggff$ process

The photon transverse momentum-dependant description of this process as previously developed in [PPtoLL](../bibliography#textbfk-_-mathrmtextbft-factorisation), is provided through the `pptoll` process in CepGen.
You may find a full description of this approach in [this page](../kt-factor)

## Process-specific options

The `mode` enumeration allows to specify the kinematic regime to generate and the size of the phase space to perform the integration.
It can take the following values:

- `ProcessMode.ElasticElastic = 1`, for the elastic emission of photons from the incoming protons (default value if unspecified),
- `ProcessMode.ElasticInelastic = 2` or `ProcessMode.InelasticElastic = 3`, for the elastic scattering of one photon and an inelastic/semi-exclusive emission of the other photon, resulting in the excitation/fragmentation of the outgoing proton state,
- `ProcessMode.InelasticInelastic = 4`, where both the protons are fragmented in the final state.

