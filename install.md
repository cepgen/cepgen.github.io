---
title: Installation procedure
---

# CepGen installation

The recipe detailed below is intended for "regular users", who downloaded a version of the code from a current [stable release]({{ site.github.releases_url }}).
***For developers, please find a collection of useful procedures [in this page](install-dev).***

Start by downloading the latest release on our github project page.
Unpack the sources in a location referred here as: `$CEPGEN_SOURCES`.

For instance, for `CepGen` v`x.y`:

~~~ sh
tar xvfz cepgen-x.y.tar.gz
cd cepgen-x.y
export CEPGEN_SOURCES=`pwd -P`
~~~

Once you have set up the sources and downloaded/installed the required dependencies, create your building environment (here, we will use the general `CMake` convention `$CEPGEN_SOURCES/build`).
The compilation is hence done with:
~~~ sh
mkdir $CEPGEN_SOURCES/build && cd $CEPGEN_SOURCES/build
cmake $CEPGEN_SOURCES # or `cmake ..`, path to the sources
make # optionally, add -jN (N=number of parallel threads for compilation)
~~~

-----------------------------------------------------------
If you need to import the libraries and includes in your standard `PATH`, run (as root)
~~~ sh
make install
~~~

This will copy all required headers into the local includes directory (e.g. `/usr/local/include/`), and copy the shared objects into the library path (e.g. `/usr/local/lib64/` or `/usr/local/lib/`).

> This last stage enables the library developer to link easily its library against all `CepGen` requirements:
  - `libCepGenCore` contains all physics constants, calculators, and helpers, along with "non-physics" standard objects implementation,
  - `libCepGenProcesses` contains [all processes definitions](/processes) and implementations,
  - `libCepGenStructureFunctions` embeds all proton [structure functions](/structure-functions) calculators objects,
  - `libCepGenEvent` holds the definition of events and subleading particles objects (useful for analyses of CepGen outputs),
  - `libCepGenIO` provides a set of helper tools for the interfacing with external applications.

## Dependencies

For successful build and operations, `CepGen` only requires a limited set of external dependencies.

Among the mandatory dependencies,
- [`CMake`](https://cmake.org/) for the management of the build process,
- [`GSL`](https://www.gnu.org/software/gsl/), for the integrators definition and general utilitaries.
  A version greater than or equal to `2.1` is recommended for the bilinear spline interpolation capability.
  This latter is used in e.g. the MSTW structure functions and KMR $\kt$-factorised gluon flux definitions.

> Depending on your system architecture and distribution, these dependencies may be installed the following way:
  - Debian/Ubuntu
    - `sudo apt-get install gfortran`
    - `sudo apt-get install libgsl2 libgsl-dev`
  - RHEL/Fedora
    - `dnf install gcc-gfortran`
    - `dnf install gsl gsl-devel`

A set of facultative libraries may also be linked against `CepGen` to extend its capabilities:
- `python` version 2 or 3, with its development headers, for the [advanced input cards](/steering-cards/python) parsing,
- [`Pythia`](http://home.thep.lu.se/Pythia/) version 8.1 or above, for the various particles decays and excited proton fragmentation,
- [`LHAPDF`](https://lhapdf.hepforge.org/) version 5 or above, for the "exotic" structure functions definition.

Events generation and storage for further processing can be coupled to several (also facultative) tools, for instance:
- [`HepMC`](https://hepmc.web.cern.ch/hepmc/) version 2 or 3, for the same-name output format handling, or LHEF formats (from version 3 on only; if not present, this latter format can be handled through `Pythia 8` instead)
- [`ROOT`](https://root.cern.ch/) for the ntuples/histogramming/plotting capabilities widely used in HEP.
