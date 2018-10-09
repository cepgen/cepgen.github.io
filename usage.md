---
title: Process parameterisation
---

# General usage

The installation guide for the library and general examples may be found [here](/install).

Several tools are shipped to ease the user interaction with the library.
All of these can be compiled (after the `CMake` environment is set as described [here](/install)) through a simple `make <tool_name>`.
The associated **output executable** may then be found in the `test/` directory of the build environment (e.g. in `test/tool_name` for the example above).

These tools are:
- `cepgen` for a trivial **cross section computation** and **events generation**.
  The per-event callback function dumps events in the terminal at a frequency defined by the steering card.
  This may be used to validate a configuration file and modified to fit the user's needs.
- `cepgen-ascii` to **compute the cross section** and **store events** in one of the supported ASCII output format.
- `cepgen-root`, generating a **ROOT file** with **events** and **run information**.
  This latter may be used in parallel to the two `ROOT::CepGenRun` and `ROOT::CepGenEvent` helper reader objects for a compact analysis workflow.

`CepGen` may either be steered through the modification of its **internal parameters definition**, or using the various **steering modules** available.
For the latter, two types of cards are currently supported for the run parameterisation.

- [Structured configurations](/steering-cards/python)
- [LPAIR-like steering cards](/steering-cards/lpair)

