---
title: "Inversion"
date: 2017-10-24T14:39:35-04:00
---

Seismic inversion is by nature an iterative procedure.  At each iteration we perform the following steps.

To perform a model inversion, the following steps need to be done.
<center><img src="/SeisStar/img/inversion_workflow.jpg" alt="" width="400" align="middle"></center>
![Inversion Workflow](/workflows/images/inversion_workflow.jpg?classes=shadow&width=400px)

#### 1. Forward simulation

  Given a **velocity model** as input, the forward simulation returns **synthetic seismograms** as output.

  Since your _velocity model_ is different from the real-world model, the synthetic seismograms are also different from the observed data recorded by the seismometers. Thus, the key point here is how to use the difference between observed data and synthetic data to update your velocity model, which we call the Seismic Inversion in tomography. After the first iteration, forward simulations performed as part of optimization procedure can simply be carried over to the next iteration.

  More information about the forward solver(the software that can run forward simulation) could be found in the [**solver**](/SeisStar/docs/solvers) page.

#### 2. Pre-processing
In our terminology, _pre-processing_ includes all operations performed on seismic traces prior to the adjoint simulation.  **Signal processing** operations, **window selection** of obervations and synthetics, and **creation of adjoint sources** fall into this category.

  1. Signal Processing
    The signal processing includes steps like removing trend, tapering data, removing instrument response and etc. Observed and synthetic data will be filtered into targeted period band.

  2. Window Selection
    If you do not want to make measurements on the whole seismograms, then selecting windows on the seismograms are required. We use some criterial to generate windows and afterwards measurement will only be made inside those windows.

  3.  Adjoint Source Generation
    Adjoint sources are calculated inside windows. There are different kinds of adjoint sources you can choose.

More information could be found in the [**pre-processing**](/SeisStar/docs/preprocessing) page

#### 3. Adjoint simulation

Given _adjoint traces_ as input, the adjoint simulations returns **sensitivity kernels** as output.

More information about the adjoint solver(the software that can run adjoint simulation) could be found in the [**solver**](/SeisStar/docs/solvers) page.

#### 4. Post-processing
In our terminology _post-processing_ includes all operations performed on sensitivity kernels following the adjoint simulation. After post-processing, we will turn the kernels into gradient, and the gradient will be used in the optimization stage. **Projection**, **regularization**, and **preconditioning** fall into this category.

More information could be found in the [**post-processing**](/SeisStar/docs/solvers) page.

#### 5. Optimization

Given the gradient direction, the optimization procedure returns an **updated model**.  Conventionally, the optimization procedure consists of separate _search direction_ and _line search_ computations.

More information could be found in the [**optimization**](/SeisStar/docs/optimization) page.
