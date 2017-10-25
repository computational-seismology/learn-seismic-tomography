---
title: "Post-Processing"
date: 2017-10-24T14:49:21-04:00
weight: 3
---

From the adjoint simulations, we get _sensitivity kernels_ for different events.  We must perform operations on these kernels to get the gradient of the objective function, after which we can move on to the optimization procedure.

We define post-processing as 'operations on sensitivity kernels carried out after the adjoint simulations but before the optimization procedure.'  Such operations may include

- `Summation`
- `Projection (optional)`
- `Regularization`
- `Preconditioning (optional)`


#### Summation
First, contributions from individual sources must be summed to get the unprojected, unregularized gradient of the objective function. In adjoint tomography, we say that _event kernels_ are added together to produce a _misfit kernel_.


#### Projection
Optionally, users can convert from the numerical basis used by the solver to an alternate basis consisting of splines, pixels, harmonics, or the like.  In general we prefer to work in the in the numerical basis because it is simpler and just as effective.


#### Regularization
Viable regularization strategies include 'classical' regularization, based on damping or smoothing terms in the objective function, or 'ad hoc' regularization based on smoothing or clipping performed directly on the sensitivity kernels.  Extensive precedents exist for both strategies.


#### Preconditioning
Finally, we precondition the gradient.  Details of the preconditioning operation vary depending on what optimization algorithm is used.  Usually, our approach involves scaling the gradient by the diagonal Hessian or some approximation to it.
