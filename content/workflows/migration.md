---
title: "Migration"
date: 2017-10-24T14:39:42-04:00
---

Migration can be formulated as optimization problem involving forward and adjoint simulations, much like inversion.  While inversions usually require many model update iterations, conventional migration involve only a single iteration.



#### 1. Forward simulation

Given a velocity model as input, the forward simulation returns synthetic traces as output, just as in an inversion.


#### 2. Pre-processing
In our terminology, _pre-processing_ includes all operations performed on seismic traces prior to the adjoint simulation.  Signal processing operations, comparison of obervations and synthetics, and creation of adjoint traces fall into this category.


#### 3. Adjoint simulation

Given _adjoint traces_ as input, the adjoint simulations returns _sensitivity kernels_ as output.


#### 4. Post-processing
In our terminology _post-processing_ includes all operations performed on sensitivity kernels following the adjoint simulation.  Summation, projection, regularization, and preconditioning fall into this category.


#### 5. Optimization (optional)

In conventional migration, only a single iteration is carried out.  Optionally, additional iterations can be performed using the same type of optimization procedure as in seismic waveform inversion.
