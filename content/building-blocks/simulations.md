---
title: "Simulations"
date: 2017-10-24T14:49:09-04:00
weight: 1
---

## Forward and adjoint solvers

To perform a seismic inversion you will need a solver package with __forward__ and __adjoint__ simulation capabilities.

Because the elastic wave equation is _self-adjoint_, numerical code for the forward simulation can be reused for the adjoint simulation.  This is the approach taken with SPECFEM solvers.

For the forward simulation, SPECFEM users must supply a velocity model, a seismic source along with a number of parameter files described in the solver user manual.  The output consists of a set of seismic traces corresponding to user-supplied source and receiver locations.

For the adjoint simulation, SPECFEM users must supply a velocity model, parameter files, and a set of 'adjoint sources'.  Adjoint sources are computed from  processed observations and synthetics through a formula that depends on the objective function under consideration.  In our terminology, generating adjoint traces is the final step in preprocessing procedure.

Several solvers are listed below:

#### **2D Solver**

* **SPECFEM2d**
  SPECFEM2D simulates forward and adjoint seismic wave propagation in two-dimensional acoustic, (an)elastic, poroelastic or coupled acoustic-(an)elastic-poroelastic media, with Convolution PML absorbing conditions.

  The code is hosted on [SPECFEM2D website at CIG](http://geodynamics.org/cig/software/specfem2d/).

#### **3D solver**

* **SPECFEM3D**
  
  SPECFEM3D Cartesian simulates acoustic (fluid), elastic (solid), coupled acoustic/elastic, poroelastic or seismic wave propagation in any type of conforming mesh of hexahedra (structured or not.) It can, for instance, model seismic waves propagating in sedimentary basins or any other regional geological model following earthquakes. It can also be used for non-destructive testing or for ocean acoustics.
  
  The code is hosted on [SPECFEM3D website at CIG](http://geodynamics.org/cig/software/specfem3d/).

* **SPECFEM3D_GLOBE**
  
  SPECFEM3D_GLOBE simulates global and regional (continental-scale) seismic wave propagation.
  
  The code is hosted on [SPECFEM3D_GLOBE website at CIG](http://geodynamics.org/cig/software/specfem3d_globe/).
