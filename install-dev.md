---
title: Developers installation
---

# Installation for developers

Active development branches:

- `collinear-partons`: for the collinear emission of a valence quark from which the two-photon system arises in Pythia 8
- `pA-to-ff`: for the version allowing FORTRAN implementations of $k _ \mathrm{T}$ processes, including the $pA\to X(g\gamma\to c\bar c)A$ or $pA\to p^{(\ast)}(\gamma\gamma\to\ell^+\ell^-)A$ processes.

Current contributors: {% for contrib in site.github.contributors %}
![{{ contrib.login }}]({{ contrib.avatar_url }} "{{ contrib.login }}"){:width="25px"}
{% endfor %}

## General recipe

To obtain a list of mandatory and optional dependencies, have a look at the [general installation procedure](install).

```sh
git clone git@github.com:forthommel/cepgen-dev
cd cepgen-dev
mkdir build
cd build
```

Then check a development branch out (see the list above for a detailed description of major branch features):

```sh
git checkout <branch name>
```

Then the building procedure can be launched:

```sh
cmake ..
make
```

Currently, several test executables can be linked against the `CepGen` libraries, for instance:

- `cepgen`
- `cepgen-root`
- `cepgen-lhe`

You may build these executables using the `make` command. For instance, `make cepgen`.
The test executable will then be located in the `test/` directory.
You may run it using, for instance (in `cepgen-dev/build/`):

```sh
test/cepgen <path to your steering card>
```

