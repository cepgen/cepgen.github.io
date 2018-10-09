---
title: Developers installation
---

# Installation for developers

### Active development branches

- `devel`
: Main branch where most of the new code is being pushed. The Pythia 8 hadronisation part handles by default the collinear emission of a valence quark from which the two-photon system arises.
- `diffvm`
: Version including the [DiffVM](/processes/diffvm) diffractive vector meson production process.
- `herwig-fragmentation`
: Implementation of the Herwig (aka Herwig 7) cluster fragmentation algorithm.

### Miscellaneous information

* Current contributors: {% for contrib in site.github.contributors %}
[![{{ contrib.login }}]({{ contrib.avatar_url }} "{{ contrib.login }}"){:width="25px"}]({{ contrib.html_url }})
{% endfor %}
* Open issues: {{ site.github.public_repositories[0].open_issues }}

## General recipe

To obtain a list of mandatory and optional dependencies, have a look at the [general installation procedure](install).

~~~ sh
git clone git@github.com:forthommel/cepgen-dev
cd cepgen-dev
mkdir build
cd build
~~~

Then check a development branch out (see the list above for a detailed description of major branch features):

~~~ sh
git checkout <branch name>
~~~

Then the building procedure can be launched:

~~~ sh
cmake ..
make
~~~

Currently, several test executables can be linked against the `CepGen` libraries, for instance:

- `cepgen`
- `cepgen-root`
- `cepgen-ascii`

You may build these executables using the `make` command. For instance, `make cepgen`.
The test executable will then be located in the `test/` directory.
You may run it using, for instance (in `cepgen-dev/build/`):

~~~ sh
./test/cepgen <path to your steering card>
~~~

