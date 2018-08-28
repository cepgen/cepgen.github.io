---
title: Python steering cards
---

# Structured ("Python") configurations

The first, structured, configuration allows a better control over all run parameters through an increased granularity.
It also allows to include "standard" configuration parameters through Python's `import` statements.

This configuration style requires the Python C API to be linked against the steering cards utils library.

One object is required to be defined within every steering card: the `process` path.

### `process` block

#### General parameters

The first `cepgen.Module` attribute attribute is required to specify the process to generate.
See [the list of processes](/processes) to get all supported values.


#### `process.inKinematics` block

The `pz` Python pair of floating point numbers, allowing to specify the two incoming protons' longitudinal momentum (in GeV).

The `structureFunctions` enumeration attribute specifies the $F _ {2/L}(x,Q^2)$ structure function to use in the parameterisation of the incoming photon fluxes.
The string attribute is the prefered, while the integer-type is kept for backward-compatibility with old `LPAIR` steering cards.
See [the list of structure functions](/str-functions) to obtain all supported values.

#### `process.outKinematics` block

The kinematics phase space to be used in the integration and events production can be specified using a set of cuts applied on the matrix element level:

- `pt`, for the single central particle transverse momentum range definition,
- `energy`, for the single central particle energy range definition,
- `eta`, for the single central particle pseudo-rapidity range definition,
- `rapidity`, for the single central particle rapidity range definition,
- `mx`, for the outgoing excited proton mass range definition

### Example

The generation of 100k single-dissociative $\gamma\gamma\to\mu^+\mu^-$ events at 13 TeV with the [LPAIR matrix element](/processes/lpair) implementation with the following phase space cuts:

- $p _ \mathrm{T}(\mu^\pm)>$ 25 GeV, $\lvert\eta(\mu^\pm)\rvert < $ 2.5
- 1.07 $< M_X < $ 1000 GeV

can be steered using the following card:

```python
import Config.Core as cepgen
from Config.integrators_cff import vegas as integrator
from Config.generator_cff import generator as gentmpl

process = cepgen.Module('lpair',
    processParameters = cepgen.Parameters(
        mode = cepgen.ProcessMode.InelasticElastic, # single-dissociation
        pair = 13, # muons
    ),
    inKinematics = cepgen.Parameters(
        pz = (6500., 6500.), # or cmEnergy = 13.e3,
        structureFunctions = cepgen.StructureFunctions.SuriYennie,
    ),
    outKinematics = cepgen.Parameters(
        pt = (25., ),
        energy = (0., ),
        eta = (-2.5, 2.5),
        mx = (1.07, 1000.),
    )
)

generator = gentmpl.clone(
    numEvents = 1e5,
)
```

