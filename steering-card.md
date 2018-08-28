---
title: Process parameterisation
---

`CepGen` may either be steered through the modification of its internal parameters definition, or using the various steering modules available.
For the latter, two types of cards are currently supported for the run parameterisation.

## Structured configurations

The first, structured, configuration allows a better control over all run parameters through an increased granularity.
It also allows to include "standard" configuration parameters through `@include` statements.

This configuration style requires the `python` C wrapper to be linked to the main library.

One object is required to be defined within every steering card: the `process` path.

### `process` block

#### General parameters

The first `cepgen.Module` attribute attribute is required to specify the process to generate.
See [the list of processes](proclist) to get all supported values.



#### `process.inKinematics` block

The `pz` Python pair of floating point numbers, allowing to specify the two incoming protons' longitudinal momentum (in GeV).

The `structureFunctions` enumeration attribute specifies the $F _ {2/L}(x,Q^2)$ structure function to use in the parameterisation of the incoming photon fluxes.
The string attribute is the prefered, while the integer-type is kept for backward-compatibility with old `LPAIR` steering cards.
See [the list of structure functions](str-functions) to obtain all supported values.

#### `process.outKinematics` block

The `pair` integer value, only used in the lepton pair production, allows the end-user to specify the PDG identifier of the lepton to be produced in the final state.
It can hence take the following values:
- `11` for the electron/position pair production
- `13` for the dimuon pair production
- `15` for the tau pair production

The kinematics phase space to be used in the integration and events production can be specified using a set of cuts applied on the matrix element level:

- `pt`, for the single central particle transverse momentum range definition,
- `energy`, for the single central particle energy range definition,
- `eta`, for the single central particle pseudo-rapidity range definition,
- `rapidity`, for the single central particle rapidity range definition,
- `mx`, for the outgoing excited proton mass range definition

### Example

The generation of 100k single-dissociative $\gamma\gamma\to\mu^+\mu^-$ events at 13 TeV with the LPAIR matrix element implementation with the following phase space cuts:

- $p _ \mathrm{T}(\mu^\pm)>$ 25 GeV, $\lvert\eta(\mu^\pm)\rvert < $ 2.5
- 1.07 $< M_X < $ 1000 GeV

can be steered using the following card:

```python
import Config.Core as cepgen
from Config.integrators_cff import vegas as integrator
from Config.generator_cff import generator as gentmpl

process = cepgen.Module('lpair',
    processParameters = cepgen.Parameters(
        mode = cepgen.ProcessMode.InelasticElastic,
        ''' or cepgen.ProcessMode.ElasticElastic
               cepgen.ProcessMode.ElasticInelastic
               cepgen.ProcessMode.InelasticInelastic '''
        pair = 13,
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
## LPAIR-like steering cards

The second (and simplest one), inherited from `LPAIR` and `PPtoLL`, only allows to set a well-defined set of parameters through a *key → value* approach.
The table below lists all keys currently handled by this parser, along with their default value (if not retrieved from the steering card).

|        | Description                                                     | Default    | Unit |
|:------:|:----------------------------------------------------------------|:-----------|:----:|
| `PROC` | Process to generate                                             | `lpair`    |      |
| `MODE` | Subprocess' mode                                                | 1 (el-el)  |      |
|        | **Incoming state**                                              |            |      |
| `IN1P` | First incoming particle's momentum                              | 6500       | GeV  |
| `IN2P` | Second incoming particle's momentum                             | 6500       | GeV  |
| `PMOD` | First incoming particle's remnant mode                          | 2 (elastic)|      |
| `EMOD` | Second incoming particle's remnant mode                         | 2 (elastic)|      |
| `Q2MN` | Minimal Q^2 (exchanged parton)                                  | 0.0        | GeV² |
| `Q2MX` | Maximal Q^2 (exchanged parton)                                  | 10⁵        | GeV² |
|        | **Integration parameters**                                      |            |      |
| `NCVG` | Number of function calls in Vegas                               | 10⁵        |      |
| `NCSG` | Number of points to probe in Vegas                              | 100        |      |
| `ITVG` | Number of Vegas iterations                                      | 10         |      |
| `NGEN` | Number of unweighted events to generate                         | 0          |      |
|| **Central system**                                                      |            |      |
| `PAIR` | Outgoing leptons' PDG identifier                                | 13 (muons) |      |
| `PTCT` | Minimal transverse momentum (single central particle)           | 3.0        | GeV  |
| `MSCT` | Minimal central system mass                                     | 0.0        | GeV  |
| `ECUT` | Minimal energy (single central particle)                        | 0.0        | GeV  |
| `ETMN` | Minimal pseudo-rapidity (central outgoing particles)            | -2.5       |      |
| `ETMX` | Maximal pseudo-rapidity (central outgoing particles)            | 2.5        |      |
| `YMIN` | Minimal rapidity (central outgoing particles)                   | -5.0       |      |
| `YMAX` | Maximal rapidity (central outgoing particles)                   | 5.0        |      |
|| **Outgoing protons / remnants**                                         |            |      |
| `HADR` | Hadronisation algorithm                                         | `none`     |      |
| `MXMN` | Minimal invariant mass of proton remnants ($m_p+m _ {\pi^{0}}$) | 1.07       | GeV  |
| `MXMX` | Maximal invariant mass of proton remnants                       | 320        | GeV  |
|        | **CepGen internal flags**                                       |            |      |
| `DEBG` | Debugging verbosity                                             | 2 (warning)|      |

