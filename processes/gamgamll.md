---
title: Two-photon production of lepton pairs
tags: lpair
category: processes
---

# Two-photon production of lepton pairs

The $pp \rightarrow p^{(\ast)}(\gamma\gamma \rightarrow \ell^+\ell^-)p^{(\ast)}$ process is defined with two different approaches in CepGen:

- a full matrix elements formalism, aka the `LPAIR` implementation,
- the $k _ {\mathrm T}$-factorised implementation, as introduced in `PPTOLL`.

## Full matrix element
The full description of this two-photon process as previously implemented in `LPAIR` can be reached through the `lpair` process in CepGen.

### Process-specific options

The `mode` enumeration allows to specify the kinematic regime to generate and the size of the phase space to perform the integration.
It can take the following values:

- `ProcessMode.ElasticElastic = 1`, for the elastic emission of photons from the incoming protons (default value if unspecified),
- `ProcessMode.ElasticInelastic = 2` or `ProcessMode.InelasticElastic = 3`, for the elastic scattering of one photon and an inelastic/semi-exclusive emission of the other photon, resulting in the excitation/fragmentation of the outgoing proton state,
- `ProcessMode.InelasticInelastic = 4`, where both the protons are fragmented in the final state.

## $k _ {\mathrm T}$-factorisation

The photon transverse momentum-dependant description of this process as previously developed in [PPtoLL](../bibliography#textbfk-_-mathrmtextbft-factorisation), is provided through the `pptoll` process in CepGen.
You may find a full description of this approach in [this page](../kt-factor)
