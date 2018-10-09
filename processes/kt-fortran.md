---
title: Fortran processes interface
---

# Fortran processes

This page describes the interface to Fortran process definition implemented in CepGen.

## Define your process

### Subroutine definition

The core definition of your process will take the form of a new `.f` file you will store in the [`External/Processes/`](https://github.com/forthommel/cepgen-dev/blob/devel/External/Processes) directory of your local CepGen install.

Currently, the following Fortran process(es) is(are) defined:

- `nucl_to_ff`

For illustration in this documentation page, we will be using a dummy process name, such as **`dummy_f77_process`**.

For the sake of simplicity in your processes definition bookkeeping we suggest you to match the filename to the subroutine name.
In our example, this corresponds to `External/Processes/dummy_f77_process.f`

We expect your subroutine to follow the C-equivalent signature:
~~~ c
void dummy_f77_process_( double& aintegrand );
~~~

This might get translated, for instance, into the following minimal working example (with the _free form_ coding convention):

~~~ fortran
subroutine dummy_f77_process(aintegrand)
implicit none
double precision aintegrand
!--------------------------------------------------------------------------
! CepGen overhead
!--------------------------------------------------------------------------
include 'KTBlocks.inc' ! include the kinematics common blocks
call CepGen_print      ! display some run parameters information
!--------------------------------------------------------------------------
! end of overhead, beginning of process definition
!--------------------------------------------------------------------------
weight = 1.D0
!--------------------------------------------------------------------------
! end of process definition
!--------------------------------------------------------------------------
end
~~~

The kinematic blocks defined through this initial **`include`** statement are described in the next section.

### Kinematics block

#### Physics constants
~~~ fortran
      common/constants/am_p,units,pi,alpha_em
      double precision am_p,units,pi,alpha_em
~~~

#### Process definition

~~~ fortran
      common/params/icontri,iflux1,iflux2,imethod,sfmod,pdg_l,
     &     a_nuc1,z_nuc1,a_nuc2,z_nuc2,
     &     inp1,inp2
      integer icontri,iflux1,iflux2,imethod,sfmod,pdg_l,
     &     a_nuc1,z_nuc1,a_nuc2,z_nuc2
      double precision inp1,inp2
~~~

#### $\kt$-factorisation kinematics

~~~ fortran
      common/ktkin/q1t,q2t,phiq1t,phiq2t,y1,y2,ptdiff,phiptdiff,
     &     am_x,am_y
      double precision q1t,q2t,phiq1t,phiq2t,y1,y2,ptdiff,phiptdiff,
     &     am_x,am_y
~~~

#### Phase space cuts

~~~ fortran
      common/kincuts/ipt,iene,ieta,iinvm,iptsum,idely,
     &     pt_min,pt_max,ene_min,ene_max,eta_min,eta_max,
     &     invm_min,invm_max,ptsum_min,ptsum_max,
     &     dely_min,dely_max
      integer ipt,iene,ieta,iinvm,iptsum,idely
      double precision pt_min,pt_max,ene_min,ene_max,eta_min,eta_max,
     &     invm_min,invm_max,ptsum_min,ptsum_max,
     &     dely_min,dely_max
~~~

#### Output event kinematics

This common block stores the whole event structure and information.
Beside the outgoing beam particles 4-momenta `px` and `py`, it contains the PDG id and 4-momentum of all central system particles in `pc`.
For this latter, a maximum multiplicity of 10 particles is set by default in `CepGen`.

~~~ fortran
      common/evtkin/px,py,nout,idum,ipdg,pc
      integer nout,idum,ipdg(10)
      double precision px(4),py(4),pc(4,10)
~~~

### Helper tools

To ease the work of the process developer, we provide utilitaries for the evaluation of unintegrated parton fluxes and other physics quantities through the `CepGen` core C++ library methods.
The external methods exposed to the Fortran process through the **`include`** statement above are:

~~~ fortran
      external CepGen_kT_flux,CepGen_kT_flux_HI
      double precision CepGen_kT_flux,CepGen_kT_flux_HI
      external CepGen_particle_charge,CepGen_particle_mass
      double precision CepGen_particle_charge,CepGen_particle_mass
~~~

They correspond to, respectively, the $\kt$-factorised flux for single nucleon (proton) or heavy ion beams ; the charge (in $e$) and mass (in GeV/c²) of a particle with a PDG id given as an argument.

## Interface to CepGen

Edit the [`External/Processes/CepGenWrapper.cpp`](https://github.com/forthommel/cepgen-dev/blob/devel/External/Processes/CepGenWrapper.cpp) file to link your subroutine to the core processes module.

First step is to declare the subroutine name. In our example, this corresponds to adding the line:

~~~ C
DECLARE_FORTRAN_SUBROUTINE( dummy_f77_process )
~~~

Note
: No single, nor double trailing underscore (*_*) is required for this name registration.

Then, to enable the steering of this process in the [Python](/steering-cards/python) and [LPAIR-like](/steering-cards/lpair) input card definitions, add the following line in the second section:

~~~ C
REGISTER_FORTRAN_PROCESS( my_dummy_process, dummy_f77_process,
                          "this process is only for illustration purposes" )
~~~

Following this nomenclature:

- the first argument corresponds to the process name in the steering card,
- the second argument is the subroutine name as defined above,
- the third one is a one-line process description that will be shown at the run start.

