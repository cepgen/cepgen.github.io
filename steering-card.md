---
title: Process parameterisation
---

# CepGen configuration

Two types of steering card are currently supported in `CepGen` for the parameterisation of its run.

## Structured configurations

The first, structured, configuration allows a better control over all run parameters through an increased granularity.
It also allows to include "standard" configuration parameters through `@include` statements.

This configuration style requires the `libconfig` C++ bindings.

One object is required to be defined within every steering card: the `process` path.

### `process` block

#### General parameters

The `name` string attribute is required to specify the process to generate.
See [the list of processes](proclist) to get all supported values.

The `mode` string attribute allows to specify the kinematic regime to generate and the size of the phase space to perform the integration.
It can take the following values:

- `elastic/elastic`, for the elastic emission of photons from the incoming protons (default value if unspecified),
- `elastic/inelastic` or `inelastic/elastic`, for the elastic scattering of one photon and an inelastic/semi-exclusive emission of the other photon, resulting in the excitation/fragmentation of the outgoing proton state,
- `inelastic/inelastic`, where both the protons are fragmented in the final state.

#### `process.in_kinematics` block

The `beam1_pz` and `beam2_pz` floating point numbers allow to specify the two incoming protons' longitudinal momentum (in GeV).

The `structure_functions` string/integer attribute specifies the $$F_2(x,Q^2)$$ structure function to use in the parameterisation of the incoming photon fluxes.
The string attribute is the prefered, while the integer-type is kept for backward-compatibility with old `LPAIR` steering cards.
See [the list of structure functions](str-functions) to obtain all supported values.

#### `process.out_kinematics` block

The `pair` integer value, only used in the lepton pair production, allows the end-user to specify the PDG identifier of the lepton to be produced in the final state.
It can hence take the following values:
- `11` for the electron/position pair production
- `13` for the dimuon pair production
- `15` for the tau pair production

The kinematics phase space to be used in the integration and events production can be specified using a set of cuts applied on the matrix element level:

- `min_pt` and `max_pt`, for the single central particle transverse momentum range definition,
- `min_energy` and `max_energy`, for the single central particle energy range definition,
- `min_eta` and `max_eta`, for the single central particle pseudo-rapidity range definition,
- `min_rapidity` and `max_rapidity`, for the single central particle rapidity range definition,
- `min_mx` and `max_mx`, for the outgoing excited proton mass range definition

### Example

It can be configured with:

```cfg
process = {
  name = "lpair";
  mode = "elastic/elastic";
  /* or "inelastic/elastic"
        "elastic/inelastic"
        "inelastic/inelastic"*/
  in_kinematics = {
    beam1_pz = 6500.;
    beam2_pz = 6500.;
    structure_functions = "Suri-Yennie";
  };
  out_kinematics = {
    pair = 13;
    min_pt = 25.0;
    min_energy = 0.0;
    min_eta = -2.5;
    max_eta = 2.5;
    max_mx = 1000.;
  };
};
```
## LPAIR-like steering cards

The second (and simplest one), inherited from `LPAIR` and `PPtoLL`, only allows to set a well-defined set of parameters through a *key → value* approach.
The table below lists all keys currently handled by this parser, along with their default value (if not retrieved from the steering card).

|        | Description                                                     | Default    | Unit |
|:------:|:----------------------------------------------------------------|-----------:|:----:|
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
|        | **Central system**                                              |            |      |
| `PAIR` | Outgoing leptons' PDG identifier                                | 13 (muons) |      |
| `PTCT` | Minimal transverse momentum (single central particle)           | 3.0        | GeV  |
| `MSCT` | Minimal central system mass                                     | 0.0        | GeV  |
| `ECUT` | Minimal energy (single central particle)                        | 0.0        | GeV  |
| `ETMN` | Minimal pseudo-rapidity (central outgoing particles)            | -2.5       |      |
| `ETMX` | Maximal pseudo-rapidity (central outgoing particles)            | 2.5        |      |
| `YMIN` | Minimal rapidity (central outgoing particles)                   | -5.0       |      |
| `YMAX` | Maximal rapidity (central outgoing particles)                   | 5.0        |      |
|        | **Outgoing protons / remnants**                                 |            |      |
| `HADR` | Hadronisation algorithm                                         |            |      |
| `MXMN` | Minimal invariant mass of proton remnants ($m_p+m _ {\pi^{0}}$) | 1.07       | GeV  |
| `MXMX` | Maximal invariant mass of proton remnants                       | 320        | GeV  |
|        | **CepGen internal flags**                                       |            |      |
| `DEBG` | Debugging verbosity                                             | 2 (warning)|      |

