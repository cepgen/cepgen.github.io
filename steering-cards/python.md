---
title: Python steering cards
---

# Structured ("Python") configurations

This format allows a better control over all run parameters through an increased granularity.
It also allows to reduce the configuration overhead through Python's `import` statements.
Obviously, it requires the Python C API to be linked against the steering cards utils library.

Two core object types (both inheriting from Python's `dict` containers) are imported in the scripting scope through the general statement:

~~~ python
import Config.Core as cepgen
~~~

These two types are **`Module`**, and **`Parameters`**.
The earlier is a subset of the latter, with the first string-type attribute defining the module name.

The common usage for such a module definition is, for instance:

~~~ python
import Config.Core as cepgen
module = cepgen.Module('my_first_module', foo = 'bar')
~~~
In [this section](#more-information-about-containers), one can see an illustrated example of this **`Module`**/**`Parameters`**/`dict` relation.

Several blocks are required to be defined in a `CepGen` steering card.
In the following sections, you may find a nonexhaustive (and evolving) list of such attributes.

## `Module` The _process_ block

This block comes as a required **`Module`** object defined in the general scope.
Its first feature is to specify the process to account for in the user-defined run.
See [the list of processes](/processes) to find your model of interest.

### `Parameters` _process.inKinematics_ block

A `pz` Python pair (or list) of floating point numbers allows to specify the two incoming protons' longitudinal momentum (in GeV).
The `cmEnergy` keyword can also be used for symmetric, head-on colliding beams.

Equivalently, a `pdgIds` pair/list of [integer-type PDG identifiers](http://pdg.lbl.gov/2007/reviews/montecarlorpp.pdf) may be used to control beam particles type.
A default `pdgIds = (2212,2212)` corresponding to the proton-proton initial state is used.

The `structureFunctions` attribute specifies the $F _ {2/L}(\xbj,Q^2)$ structure function to use in the parameterisation of the incoming photon fluxes.
The name of the structure functions set (see [the complete list here](/structure-functions)) has to be prepended by `StructureFunctions`.

For instance, the _Suri-Yennie_ set may be selected through `StructureFunctions.SuriYennie`.

### `Parameters` _process.outKinematics_ block

The kinematics phase space to be used in the integration and events production can be specified using a set of cuts applied on the matrix element level:

- `pt`, for the single central particle transverse momentum range definition,
- `energy`, for the single central particle energy range definition,
- `eta`, for the single central particle pseudo-rapidity range definition,
- `rapidity`, for the single central particle rapidity range definition,
- `mx`, for the outgoing excited proton mass range definition

### `Parameters` _process.processParameters_ block

This block is a generic placeholder for all process-dependent parameters.
See the description page of each process to get a list of supported parameters to include in this collection.

## Configuration card example

The generation of 100k single-dissociative $\gamma\gamma\to\mu^+\mu^-$ events at 13 TeV with the [LPAIR matrix element](/processes/lpair) implementation with the following phase space cuts:

- $p _ \mathrm{T}(\mu^\pm)>$ 25 GeV, $\lvert\eta(\mu^\pm)\rvert < $ 2.5
- 1.07 $< M_X < $ 1000 GeV

can be steered using the following card:

~~~ python
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
~~~

This configuration is equivalent to the _LPAIR card_ shown [here](lpair#configuration-card-example).

-----------------------------------------------------------

### More information about containers

The **`Module`** object is defined as a named **`Parameters`** container.
Its naming is stored within its `mod_name` attribute.
For instance, the example shown [in this section](#structured-python-configurations) may be rewritten as:

~~~ python
import Config.Core as cepgen
module = cepgen.Parameters(mod_name = 'my_first_module', foo = 'bar')
~~~
or, using standard Python containers:
~~~ python
module = {'mod_name': 'my_first_module', 'foo': 'bar'}
~~~

Among the features introduced by these two objects, one may quote the capability of deep-cloning one while changing one or several attributes in one pass.
For instance, using the former definition of `module`:
~~~ python
module_bis = module.clone(
    foo2 = 42,
    foo3 = cepgen.Parameters(
        nestedFoo = 'nestedBar',
    )
)
~~~
is equivalent to defining a `module_bis` container as:
~~~ python
module_bis = cepgen.Module('my_first_module',
    foo = 'bar',
    foo2 = 42,
    foo3 = cepgen.Parameters(
        nestedFoo = 'nestedBar',
    ),
)
~~~

