---
title: LPAIR-like steering cards
---

# LPAIR-like steering cards

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

