---
title: LPAIR's two-photon production of lepton pairs
tags: lpair
category: processes
---

# LPAIR's $\ggll$

The full description of this $pp \rightarrow p^{(\ast)}(\ggll)p^{(\ast)}$ process  as previously implemented in `LPAIR` can be reached through the `lpair` process in CepGen.

## Process-specific options

The `pair` integer value, only used in the lepton pair production, allows the end-user to specify the PDG identifier of the lepton to be produced in the final state.
It can hence take the following values:
- `11` for the electron/position pair production
- `13` for the dimuon pair production
- `15` for the tau pair production

The `mode` enumeration allows to specify the kinematic regime to generate and the size of the phase space to perform the integration.
It can take the following values:

- `ProcessMode.ElasticElastic` (or `1`), for the elastic emission of photons from the incoming protons (default value if unspecified),
- `ProcessMode.ElasticInelastic` (or `2`) / `ProcessMode.InelasticElastic` (or `3`), for the elastic scattering of one photon and an inelastic/semi-exclusive emission of the other photon, resulting in the excitation/fragmentation of the outgoing proton state,
- `ProcessMode.InelasticInelastic` (or `4`), where both the protons are fragmented in the final state.

