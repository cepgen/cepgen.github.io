---
title: Processes
summary: List of processes currently supported by `CepGen`
---

# List of processes

In its current version, `CepGen` releases the implementation of the following central exclusive processes:

- Generic processes
    - `lpair`: [two-photon production of a lepton pair](/processes/lpair)
    - `diffvm`: [diffractive vector meson production](/processes/diffvm)

- $\kt$-factorised processes
> A full review of this factorisation procedure may be found in [this page](/processes/kt-factor).
    - `pptoff`: [two-photon production of a fermion pair](/processes/pptoff)
    - `pptoww`: [two-photon production of a W gauge boson pair](/processes/pptoww)
    - `patoff`\|`aptoff`\|`aatoff`: [fermion pair production in pp/pA/AA collisions](/processes/patoff)

Developers zone
: Several C++ and Fortran helper modules are provided for an easy process integration.
: For more information on the latter, see the [Fortran process interfacing manual page](/processes/kt-fortran).
