---
title: kT-factorised two-photon production of fermion pairs
tags: lpair
category: processes
---

# $\kt$-factorised $\ggff$ process

The photon transverse momentum-dependant description of this process as previously developed in [PPtoLL](../bibliography#textbfk-_-mathrmtextbft-factorisation), is provided through the `pptoll` process in CepGen.
You may find a full description of this approach in [this page](kt-factor)

## Process-specific options

The `pair` integer value allows the end-user to specify the PDG identifier of the fermion pair to be produced in the final state.
It can hence take the following values:
- `1-6` for the quark pair production,
- `11`/`13`/`15` for the electron-positron/muon/tau pair production.

The `mode` enumeration allows to specify the kinematic regime to generate and the size of the phase space to perform the integration.
It can take the following values:

- `ProcessMode.ElasticElastic` (or `1`), for the elastic emission of photons from the incoming protons (default value if unspecified),
- `ProcessMode.ElasticInelastic` (or `2`) / `ProcessMode.InelasticElastic` (or `3`), for the elastic scattering of one photon and an inelastic/semi-exclusive emission of the other photon, resulting in the excitation/fragmentation of the outgoing proton state,
- `ProcessMode.InelasticInelastic` (or `4`), where both the protons are fragmented in the final state.

