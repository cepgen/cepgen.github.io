---
title: Installation procedure
---

# CepGen installation

## Dependencies

For successful build and operations, `CepGen` only requires a limited set of external dependencies.

Among the mandatory dependencies,
- `CMake`, for the project building,
- [`GSL`](bibliography#computational-methods), for the Vegas integrator and events generation.

The events generation and storage for further processing can however be simplified by using the following additional (and facultative) dependencies:
- `python` version 2 or 3, with its development headers, for the advanced [input cards](steering-card) parsing,
- [`HepMC`](https://hepmc.web.cern.ch/hepmc/) version 2 or 3, for the output generation,
- [`LHAPDF`](https://lhapdf.hepforge.org/) version 5 or above, for the "exotic" structure functions definition,
- [`Pythia`](http://home.thep.lu.se/Pythia/) version 8 or above, for the various particles decays and excited proton fragmentation.

### Distribution-specific dependencies

- Ubuntu
    - `sudo apt-get install gfortran`
    - `sudo apt-get install libgsl2 libgsl-dev`

- Fedora
    - `dnf install gsl gsl-devel`

## Installation recipe

Start by downloading the latest release on our github project page.
Unpack the sources in a location referred here as: `$CEPGEN_SOURCES`.

For instance, for `CepGen` v1.0:

```sh
tar xvfz cepgen-1.0.tar.gz
cd cepgen-1.0
export CEPGEN_SOURCES=`pwd -P`
```

Once you have set up the sources and downloaded/installed the required dependencies, create your building environment (e.g. in `$CEPGEN_SOURCES/build`), and run
```sh
cmake $CEPGEN_SOURCES # path to the sources
make # optionally, add -j N
     # where N is the number of parallel threads for compilation
```
then, if you need to import the libraries and includes in your standard `PATH`, run (as root)
```sh
make install
```

This will copy all required headers into the local includes directory (e.g. `/usr/local/include/`), and copy the shared objects into the library path (e.g. `/usr/local/lib64/` or `/usr/local/lib/`).

This last stage enables the library developer to link easily its library against all `CepGen` requirements:

- `libCepGenCore.so` contains all "non-physics" standard objects implementation,
- `libCepGenProcesses.so` contains [all processes definitions](proclist) and implementations,
- `libCepGenStructureFunctions.so` embeds all proton [structure functions](str-functions) calculators objects,
- `libCepGenPhysics.so` contains all physics constants, calculators, and helpers,
- `libCepGenEvent.so` holds the definition of events and subleading particles objects (useful for analyses of CepGen outputs).

