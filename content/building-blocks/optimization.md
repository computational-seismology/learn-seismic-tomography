---
title: "Optimization"
date: 2017-10-24T14:49:33-04:00
weight: 3
---

## Non-linear optimization

Through use of an objective function that quanitifies the difference between observations and synthetics, waveform inversion becomes an optimization problem.

Conventionally, the optimization procedure is divided into two steps:

- `Compute search direction`
- `Determine step length`



#### Compute search direction 

Nonlinear conjugate gradient, quasi-Newton, and truncated-Newton algorithms all provide viable options.  In our experience, quasi-Newton algorithms generally provide the best performance.

[example using SeisFlows]()
[example using SPECFEM utilities]()


#### Determine step length

Given a search direction, the line search consists of finding an acceptable step length.  With an efficient line search, good step lengths can usually be found with one or two forward simulations.

[example using SeisFlows]()
[example using SPECFEM utilities]()



#### Nonlinearity and nonconvexity

As an optimization problem, waveform inversion is both nonlinear and nonconvex.  

Many optimization algorithms were devised for linear problems and only later adapted for nonlinear problems.  Numerical errors that accumulate as a result of nonlinearity can be dealt with by discarding the 'memory' of the algorithm and starting once again from the steepest descent direction.

Because of nonconvexity, convergence to a point other than global minimum of the objective function is a possibility.  Through choice of multiscale and regularization parameters, care must be taken that the updated model remains in the basin of convergence of the global minimum.
