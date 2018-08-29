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
| `IN1P`<br/>`INPP` | First incoming particle's momentum                              | 6500       | GeV  |
| `IN2P`<br/>`INPE` | Second incoming particle's momentum                             | 6500       | GeV  |
| `PMOD` | First incoming particle's remnant mode                          | 2 (elastic)|      |
| `EMOD` | Second incoming particle's remnant mode                         | 2 (elastic)|      |
| `Q2MN`<br/>`Q2MX` | Q² range (exchanged parton)                                  | 0.0<br/>10⁵        | GeV² |
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
| `ETMN`<br/>`ETMX` | Pseudo-rapidity range (central outgoing particles)            | -2.5<br/>2.5       |      |
| `YMIN`<br/>`YMAX` | Rapidity range (central outgoing particles)                   | -5.0<br/>5.0       |      |
|| **Outgoing protons / remnants**                                         |            |      |
| `HADR` | Hadronisation algorithm                                         | `none`     |      |
| `MXMN`<br/>`MXMX` | Invariant mass range of proton remnants              | 1.07 ($m_p+m _ {\pi^{0}}$)<br/>320  | GeV  |
|        | **CepGen run**                                                  |            |      |
| `NGEN` | Number of events to generate                                    | 0          |      |
| `DEBG` | Debugging verbosity                                             | 2 (warning)|      |

## Configuration card example

The generation of 100k single-dissociative $\gamma\gamma\to\mu^+\mu^-$ events at 13 TeV with the [LPAIR matrix element](/processes/lpair) implementation with the following phase space cuts:

- $p _ \mathrm{T}(\mu^\pm)>$ 25 GeV, $\lvert\eta(\mu^\pm)\rvert < $ 2.5
- 1.07 $< M_X < $ 1000 GeV

can be steered using the following card:

~~~ fortran
PROC lpair
MODE 3      ! inelastic-elastic
PAIR 13     ! muons
IN1P 6500.
IN2P 6500.
PMOD 11     ! Suri-Yennie
PTCT 25.
ETMN -2.5
ETMX 2.5
ECUT 0.
MXMN 1.07
MXMX 1000.
NGEN 100000 ! generate 100k events
~~~

This configuration is equivalent to the _Python card_ shown [here](python#configuration-card-example).
